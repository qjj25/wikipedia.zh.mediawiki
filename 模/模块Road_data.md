local p = {}

-- Change to "" upon deployment.
local moduleSuffix = "/sandbox"

local parserModuleName = "Module:Road data/parser" .. moduleSuffix
local statenameModuleName = "Module:Jct/statename/sandbox" -- TODO transition

local concat = table.concat
local insert = table.insert
local format = mw.ustring.format

local parserModule = require(parserModuleName)
local parser = parserModule.parser
local util = require("Module:Road data/util")

-- Shields
local defaultShieldSize = 20

local function addContextBanner(route, name, suffix, bannerSpec)
	local bannerModule = 'Module:Road data/banners/' .. string.upper(route.country)
	local shieldfield = name .. 'shield'
	local shield = parser(route, shieldfield)
	if shield == nil then
		-- This route type does not define shield.
		-- Find shield in the default banner table.
		shield = parser(route, 'shield', name, bannerModule)
		if shield and shield ~= '' then
			if suffix == nil then
				suffix = parser(route, 'shield', 'suffix', bannerModule)
			end
			if suffix and suffix ~= '' then
				shield = shield .. " " .. suffix
			end
			shield = shield .. ".svg"
		end
	end
	if shield and shield ~= '' then
		local shieldsizefield = name .. 'shieldsize'
		local shieldSize = parser(route, shieldsizefield)
		if shieldSize == nil then
			-- This route type does not define shield size.
			-- Find shield size in the default banner table.
			shieldSize = parser(route, 'shieldsize', name, bannerModule)
		end
		if shieldSize == nil then shieldSize = "20" end
		-- Add banner plate.
		insert(bannerSpec, {shield, shieldSize})
	end
end

local function bannerSpec(banner, bannerSize, bannerSuffix, route)
	local banners = {}
	if type(banner) == "table" then
		local bannerSizeIsNotTable = type(bannerSize) ~= "table"
		for i,filename in ipairs(banner) do
			local bannersize = bannerSizeIsNotTable and bannerSize or bannerSize[i] or defaultShieldSize
			insert(banners, {filename, bannersize})
		end
	elseif banner ~= '' then
		insert(banners, {banner, bannerSize})
	end

	if route.dir then
		addContextBanner(route, 'dir', bannerSuffix, banners)
	end
	if route.to then
		addContextBanner(route, 'to', bannerSuffix, banners)
	end

	return banners
end

local function shieldSpec(route, mainShield)
	local shieldSpec = {}

	local shield
	if mainShield then shield = parser(route, "shieldmain") end
	if not shield then shield = parser(route, 'shield') or '' end
	if shield == '' then return shieldSpec end

	local shieldsize
	if mainShield then shieldsize = parser(route, "shieldmainsize") end
	if not shieldsize then shieldsize = parser(route, "shieldsize") or "" end
	local shieldsizeIsNotTable = type(shieldsize) ~= "table"

	local banner = parser(route, 'banner') or {}
	local bannersize = parser(route, 'bannersize') or defaultShieldSize
	local bannersuffix = parser(route, 'bannersuffix')

	local bannerIsNotTable = type(banner) ~= "table"
	local bannersizeIsNotTable = type(bannersize) ~= "table"
	local bannersuffixIsNotTable = type(bannersuffix) ~= "table"

	if type(shield) == "table" then
		for i,filename in ipairs(shield) do
			local size = shieldsizeIsNotTable and shieldsize or shieldsize[i]
			if size == "" then size = nil end
			-- banner.all describes banners that apply to all multiple shields.
			local shieldBanner = bannerIsNotTable and banner or (banner[i] or banner.all or {})
			-- Banner size is default if the corresponding entry
			-- in bannerSize table is not set.
			local shieldBannerSize =
				bannersizeIsNotTable and bannersize
				or (bannersize[i] or bannersize.all or defaultShieldSize)
			local shieldBannerSuffix = bannersuffix and (bannersuffixIsNotTable and bannersuffix or bannersuffix[i])
			insert(shieldSpec, {
				shield = {filename, size},
				banners = bannerSpec(shieldBanner, shieldBannerSize, shieldBannerSuffix, route)
			})
		end
	elseif shield ~= '' then
		if shieldsize == "" then shieldsize = nil end
		insert(shieldSpec, {
			shield = {shield, shieldsize},
			banners = bannerSpec(banner, bannersize,  bannersuffix, route)
		})
	end

	return shieldSpec
end

local missingShields

local shieldExistsCache = {}

-- Return up to two booleans.
-- The first boolean is false if `shield` does not exist, and true otherwise.
-- If the first boolean is true, the second boolean is true if the shield is
-- landscape (width >= height), and false otherwise.
local function shieldExists(shield)
	local result = shieldExistsCache[shield]
	if result == nil then
		local file = mw.title.new(shield, 'Media').file
		-- Cache result.
		local exists = file.exists
		result = {exists}
		if exists then result[2] = file.width >= file.height end
		shieldExistsCache[shield] = result
	end
	if result[1] then return true, result[2] end
	insert(missingShields, shield)
	return false
end

local function render(shieldEntry, scale, showLink)
	local shield = shieldEntry.shield
	local banners = shieldEntry.banners
	local exists, landscape = shieldExists(shield[1])
	if not exists then return '' end

	local size
	if shield[2] then
		local width, height = mw.ustring.match(shield[2], "(%d*)x?(%d*)")
		width = tonumber(width)
		height = tonumber(height)
		local sizeparts = {}
		if width then
			insert(sizeparts, format("%d", width * scale))
		end
		if height then
			insert(sizeparts, format("x%d", height * scale))
		end
		size = concat(sizeparts)
	else
		size = format("%s%d", landscape and "x" or "", defaultShieldSize * scale)
	end
	local link = showLink and "" or "|link="
	local shieldCode = format("[[File:%s|%spx%s]]", shield[1], size, link, shield[1])
	if not banners[1] then return shieldCode end

	for _,banner in ipairs(banners) do
		if shieldExists(banner[1]) then
			shieldCode = format("[[File:%s|%dpx%s]]<br>%s",
				banner[1],
				banner[2] * scale,
				link,
				banner[1],
				shieldCode)
		end
	end
	return '<span style="display: inline-block; vertical-align: baseline; line-height: 0; text-align: center;">' .. shieldCode .. '</span>'
end

function p.shield(route, scale, showLink, mainShield)
	missingShields = {}
	if route.rdt then
		local shieldSize = mw.ustring.match(route.rdt, '^(%d+)$') or 17
		scale = shieldSize/defaultShieldSize
	end
	scale = scale or 1

	local rendered = {}
	for _,entry in ipairs(shieldSpec(route, mainShield)) do
		insert(rendered, render(entry, scale, showLink))
	end
	return concat(rendered), missingShields
end

function p.link(route)
	local abbr = parser(route, 'abbr')
	if not abbr then
		route.typeerror = true
		return util.err(format("Invalid type: %s", route.type or "(nil)"))
	end
	if route.nolink then return abbr, abbr end

	local link = parser(route, 'link') or ''
	if link == '' then return abbr, abbr end

	return format("[[%s|%s]]", link, abbr), abbr
end

local function stateName(args)
	-- TODO transition
	local data = mw.loadData(statenameModuleName) 
	local abbr = args.state or args.province
	local countryData = data[args.country]
	return countryData and countryData[abbr]
end

function p.locations(args, module, group)
	module = module or ""
	local modulearticle = module .. "article"
	local moduleprefix = module .. "prefix"
	local modulenameprefix = module .. "nameprefix"
	local modulenamesuffix = module .. "namesuffix"

	local warnings = {}

	-- Region, for disambiguation
	local region = parserModule.parser(args, "region", "common")
	if not region then
		-- TODO transition
		if args.region then
			warnings.region = "region parameter is deprecated"
			region = args.region
		elseif args.country and (args.state or args.province) then
			warnings.region = "Inferring region from country and state/province"
			region = stateName(args)
		end
	end
	local regionName
	local regionText
	if type(region) == "table" then
		regionName = region.name
		regionText = format("[[%s|%s]]", region.link, regionName)
	else
		regionName = region
		regionText = format("[[%s|%s]]", regionName)
	end
	args.region = regionName

	local locations = parserModule.parser(args, "locations", " common ") or {}

	-- Primary topic requires no specialization to supplied locations.
	local primaryTopic = not locations and module == "jctint" and args.primary_topic ~= 'no'
	if args.primary_topic then
		-- TODO transition
		warnings.primary_topic = "primary_topic parameter is deprecated"
	end

	-- Independent city
	local indepCityText
	if args.indep_city_special then
		indepCityText = args.indep_city_special -- Overrides `indep_city` argument.
	elseif args.indep_city then
		local indepCity = args.indep_city
		local spec = locations.indep_city
		if spec then
			local link = format("%s%s%s",
				spec.linkprefix or "", indepCity, spec.linksuffix or "")
			local name = format("%s%s%s",
				spec[modulenameprefix] or spec.nameprefix or "",
				indepCity,
				spec[modulenamesuffix] or spec.namesuffix or "")
			indepCityText = format("%s%s[[%s|%s]]",
				spec[modulearticle] or spec.article or "",
				spec[moduleprefix] or spec.prefix or "",
				link, name)
		else
			-- TODO transition
			warnings.indep_city = "Spec for indep_city parameter undefined in road data module"
			local cityLink -- Wikilink for independent city
			if primaryTopic then
				cityLink = format('[[%s|%s]]', indepCity)
			else
				-- Specialize independent city to the region.
				cityLink = format('[[%s,_%s|%s]]', indepCity, region, indepCity)
			end
			indepCityText = "[[Independent_city|City]] of " .. cityLink
		end
	end
	if indepCityText then
		return {region = regionText, indep_city = indepCityText, warnings = warnings}
	end

	-- First-level subdivision, e.g., county
	-- Name of the type of subdivision, e.g., "County" and "Parish"
	local sub1name = args.sub1name -- TODO transition
	local sub1Text
	if args.sub1_special then
		sub1Text = args.sub1_special -- Overrides `sub1` argument.
	elseif args.sub1 then
		local sub1 = args.sub1
		local article
		local link = sub1
		local name = sub1
		-- Type of first-level subdivision area, as a form of disambiguation
		local sub1area = args.sub1area
		if sub1area then
			local sub1areaSpec = locations.sub1areas and locations.sub1areas[sub1area]
			if sub1areaSpec then
				article = sub1areaSpec[modulearticle] or sub1areaSpec.article or ""
				link = format("%s%s%s",
					sub1areaSpec.linkprefix or "", link, sub1areaSpec.linksuffix or "")
				name = format("%s%s%s",
					group and "" or sub1areaSpec[modulenameprefix] or sub1areaSpec.nameprefix or "",
					name,
					group and "" or sub1areaSpec[modulenamesuffix] or sub1areaSpec.namesuffix or "")
			else
				-- TODO report error
				local errMsg = util.err(format("Undefined sub1area: %s", sub1area))
				name = format("%s%s", name, errMsg)
			end
		end
		if locations.sub1 then
			local spec = locations.sub1
			-- Prepend and append text from spec.
			link = format("%s%s%s",
				spec.linkprefix or "", link, spec.linksuffix or "")
			name = format("%s%s%s",
				spec[modulenameprefix] or spec.nameprefix or "",
				name,
				spec[modulenamesuffix] or spec.namesuffix or "")
			sub1Text = format("%s[[%s|%s]]", article or "", link, name)
		else
			-- TODO transition
			warnings.sub1 = "Spec for sub1 parameter undefined in road data module"
			-- Add type (if specified) to wikilink for first-level subdivision.
			local sub1Link = sub1name and format("%s %s", sub1, sub1name) or sub1
			local sub1Name = module == "jcttop" and sub1Link or sub1
			if primaryTopic then
				sub1Text = format('[[%s|%s]]', sub1Link, sub1Name)
			else
				-- Specialize first-level subdivision, with type added, to the region.
				sub1Text = format('[[%s,_%s|%s]]', sub1Link, region, sub1Name)
			end
		end
	end

	-- Second-level subdivision, e.g., city and town
	local sub2Text
	if args.sub2_special then
		sub2Text = args.sub2_special -- Overrides `sub2` argument.
	elseif args.sub2 then
		local sub2 = args.sub2
		if sub2 == "none" then
			sub2Text = "​" -- Zero-width space
		elseif sub2 == " " then
			-- TODO transition
			warnings.sub2 = "  argument for sub2 parameter is deprecated"
			sub2Text = "​" -- Zero-width space
		elseif primaryTopic then
			-- TODO transition
			sub2Text = format("[[%s|%s]]", sub2)
		else
			local article
			local link = sub2
			local name = sub2
			-- Type of area, e.g., city and village, as a form of disambiguation
			local sub2area = args.sub2area --[[TODO_transition|TODO transition]] or args.area
			if sub2area then
				local sub2areaSpec = locations.sub2areas and locations.sub2areas[sub2area]
				if not sub2areaSpec then
					-- TODO transition
					warnings.sub2 =
						format("Spec for area parameter '%s' undefined in road data module", sub2area)
					local sub2areas = { -- table of different area types
						city = {
							linksuffix = " (city)",
							jcttoparticle = "the ",
							nameprefix = "City of "
						},
						town = {
							linksuffix = " (town)",
							jcttoparticle = "the ",
							nameprefix = "Town of "
						},
						village = {
							linksuffix = " (village)",
							jcttoparticle = "the ",
							nameprefix = "Village of "
						},
						community = {
							linksuffix = " (community)",
							jcttoparticle = "the ",
							nameprefix = "Community of "
						},
						CDP = {
							linksuffix = " (CDP)",
							jcttoparticle = "the ",
							nameprefix = "Community of "
						},
						hamlet = {
							linksuffix = " (hamlet)",
							jcttoparticle = "the ",
							nameprefix = "Hamlet of "
						},
						["unorganized territory"] = {
							linksuffix = " (unorganized territory)",
							jcttoparticle = "the ",
							nameprefix = "Unorganized Territory of "
						},
						township = {
							linksuffix = "鎮區",
							namesuffix = "鎮區",
						}
					}
					sub2areaSpec = sub2areas[sub2area]
				end
				if sub2areaSpec then
					article = sub2areaSpec[modulearticle] or sub2areaSpec.article or ""
					link = format("%s%s%s",
						sub2areaSpec.linkprefix or "", link, sub2areaSpec.linksuffix or "")
					name = format("%s%s%s",
						group and "" or sub2areaSpec[modulenameprefix] or sub2areaSpec.nameprefix or "",
						name,
						group and "" or sub2areaSpec[modulenamesuffix] or sub2areaSpec.namesuffix or "")
				else
					-- TODO report error
					local errMsg = util.err(format("Undefined sub2area: %s", sub2area))
					name = format("%s%s", name, errMsg)
				end
			end
			if locations.sub2 then
				local spec = locations.sub2
				-- Prepend and append text from spec.
				link = format("%s%s%s",
					spec.linkprefix or "", link, spec.linksuffix or "")
				name = format("%s%s%s",
					spec[modulenameprefix] or spec.nameprefix or "",
					name,
					spec[modulenamesuffix] or spec.namesuffix or "")
			else
				-- TODO transition
				warnings.sub2 = "Spec for sub2 parameter undefined in road data module"
				-- Some second-level subdivisions are not unique in a given region.
				-- `sub1dab` is the first-level subdivision to be used for disambiguation.
				local sub1dab = args.sub1dab
				if sub1dab then
					sub1dab = sub1dab
					link = format("%s (%s%s)", link, region, sub1dab)
				end
				
			end
			sub2Text = format("%s[[%s|%s]]", article or "", link, name)
		end
	end
	return {region = regionText, sub1 = sub1Text, sub2 = sub2Text, warnings = warnings}
end

return p