-- This module implements [[Template:Parameters|Template:Parameters]].
-- [SublimeLinter luacheck-globals:mw]

local DEFINITIONS = {
	alt = {
		code = '<!-- 图像的替代文字，参见WP:ALT -->',
		dlist = '图像的替代文字，参见[[WP:ALT|WP:ALT]]'},
	coordinates = {
		code = '<!-- 使用 {{Coord}} -->',
		dlist = '使用 {{tl|Coord}}'},
	coords = {
		code = '<!-- 使用 {{Coord}} -->',
		dlist = '使用 {{tl|Coord}}'},
	native_name = {
		code = '<!-- 根据其国家语系的名字，非拉丁字母系的外文名（如日文，韩文或俄文等）' ..
			'如果多于一个，请使用{{Plainlist}}和{{lang}}模板，并省略native_name_lang -->',
		dlist = '根据其国家语系的名字，非拉丁字母系的外文名（如日文，韩文或俄文等）' ..
			'如果多于一个，请使用{{tl|Plainlist}}和{{tl|lang}}模板，并省略{{para|native_name_lang}}'},
	native_name_lang = {
		code = '<!-- 指明外文名之语系，以正确显示文字（如日文、韩文、俄文等）' ..
			'注意：是 ISO-639 语言代码，不是中文 -->',
		dlist = '指明外文名之语系，以正确显示文字（如日文、韩文、俄文等）' ..
			'注意：是 ISO-639 语言代码，不是中文'},
	start_date = {
		code = '<!-- {{Start date|YYYY|MM|DD}} -->',
		dlist = '填写格式：{{tlx|Start date|YYYY|MM|DD}}'},
	end_date = {
		code = '<!-- {{End date|YYYY|MM|DD}} -->',
		dlist = '填写格式：{{tlx|Start date|YYYY|MM|DD}}'},
	url = {
		code = '<!-- {{URL|example.com}} -->',
		dlist = '使用 {{tl|URL}}'},
	website = {
		code = '<!-- {{URL|example.com}} -->',
		dlist = '填写格式：{{tls|URL|example.com}}'},}

local p = {}
local removeDuplicates = require('Module:TableTools').removeDuplicates
local yesno = require('Module:Yesno')

local function makeInvokeFunction(funcName)
	return function(frame)
		local getArgs = require('Module:Arguments').getArgs
		return p[funcName](getArgs(frame, {removeBlanks = false}))
	end
end

local function extractParams(page)
	local source = mw.title.new(page, 'Template'):getContent()

	local parameters = {}
	for parameter in string.gmatch(source, '{{{(.-)%f[}|<>]') do
		table.insert(parameters, parameter)
	end
	return removeDuplicates(parameters)
end

local function map(tbl, transform)
	local returnTable = {}
	for k, v in pairs(tbl) do
		returnTable[k] = transform(v)
	end
	return returnTable
end

local function strMap(tbl, transform)
	local returnTable = map(tbl, transform)
	return table.concat(returnTable)
end

function p._check(args)
	local title = args._base or mw.title.getCurrentTitle().fullText
	return string.format(
		'{{#invoke:Check for unknown parameters|check|unknown=' ..
		'[[Category:使用未知%s参数的页面|Category:使用未知%s参数的页面]]|%s}}', title,
		table.concat(extractParams(args.base), '|'))
end

function p._code(args)
	local definitions = yesno(args.definitions)
	local pad = yesno(args.pad)

	local parameters = extractParams(args.base)
	-- Space-pad the parameters to align the equal signs vertically
	if pad then
		local lengthPerPara = map(parameters, function (parameter)
			return string.len(parameter) end)
		-- Lua doesn't support printf's <*> to specify the width, apparently
		local fs = string.format('%%-%ss', math.max(unpack(lengthPerPara)))
		for i, parameter in pairs(parameters) do
			parameters[i] = string.format(fs, parameter)
		end
	end

	local title = args._base or mw.title.getCurrentTitle().baseText
	return string.format([[{{%s
%s}}]], title, strMap(parameters,
		function(s)
			if definitions then
				return string.format('| %s = %s\n', s,
					DEFINITIONS[s] and DEFINITIONS[s].code or '')
			else
				return string.format('| %s = \n', s)
			end
		end))
end

function p._compare(args)
	local Set = require('Module:Set')

	local function normaliseParams(parameters)
		local paramsNorm = {}
		-- Prepare a key lookup metatable, which will hold the original
		-- parameter names for each normalised parameter, e.g.
		-- [test] = {TEST, Test}. paramIndex functions like a Python
		-- defaultdict, where the default is a table.
		local paramIndex = setmetatable({}, {__index = function(t, k)
			if not rawget(t, k) then
				rawset(t, k, {})
			end
			return rawget(t, k)
		end})
		for _, parameter in pairs(parameters) do
			table.insert(paramsNorm,
				string.lower(string.gsub(parameter, '%A', '')))
			table.insert(paramIndex[
				string.lower(string.gsub(parameter, '%A', ''))], parameter)
		end

		paramsNorm = removeDuplicates(paramsNorm)
		-- Overload key lookup in paramsNorm. While [[Module:Set|Module:Set]] will
		-- operate on the table (which is to say, the normalised parameters
		-- array), key access will be by way of the paramIndex metatable.
		setmetatable(paramsNorm, {__index = paramIndex})
		return paramsNorm
	end

	local baseParams = extractParams(args.base)
	local otherParams = extractParams(args.other)
	local baseNormParams = normaliseParams(Set.valueComplement(
			otherParams, baseParams))
	local otherNormParams = normaliseParams(otherParams)

	return string.format([[等效参数：
%s
相似参数：
%s
不同参数：
%s]],
	strMap(Set.valueIntersection(baseParams, otherParams),
		function(v) return string.format('* %s\n', v) end),
	strMap(Set.valueIntersection(baseNormParams, otherNormParams),
		function(v) return string.format('* %s < %s [%s]\n',
			table.concat(baseNormParams[v], '; '),
			table.concat(otherNormParams[v], '; '),
			v)
		end),
	strMap(Set.valueComplement(otherNormParams, baseNormParams),
		function(v) return strMap(baseNormParams[v],
			function(s) return string.format('* %s\n', s) end)
		end))
end

function p._demo(args)
	local title = args._base and ('|_template=' .. args._base) or ''
	return string.format('{{Parameter names example%s|%s}}', title,
		table.concat(extractParams(args.base), '|'))
end

function p._dlist(args)
	local definitions = yesno(args.definitions, true)
	return strMap(extractParams(args.base),
		function(s)
			if definitions then
				return string.format('; %s: %s\n', s,
					DEFINITIONS[s] and DEFINITIONS[s].dlist or '')
			else
				return string.format('; %s: \n', s)
			end
		end)
end

function p._list(args)
	return strMap(extractParams(args.base),
		function(s) return string.format('* %s\n', s) end)
end

p.check = makeInvokeFunction('_check')
p.code = makeInvokeFunction('_code')
p.compare = makeInvokeFunction('_compare')
p.demo = makeInvokeFunction('_demo')
p.dlist = makeInvokeFunction('_dlist')
p.list = makeInvokeFunction('_list')

return p