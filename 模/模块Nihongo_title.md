local p = {}

local getArgs = require('Module:Arguments').getArgs
local yesno = require('Module:Yesno')

local function varCase(t)
	local case = 'CHT'
	
	if t.cn == '' or t.tw == '' then
		case = ''
	
	elseif t.hk == '' or t.hk == 'tw' or t.hk == t.tw then
		case = 'CTT'

	elseif t.hk == 'cn' or t.hk == t.cn then
		case = 'CCT'

	elseif t.tw == 'cn' or t.tw == t.cn then
		case = 'CHC'

	elseif t.cn == 'tw' or t.cn == t.tw then
		case = 'THT'
	end
	
	return case
end

local function chi(t)
	local ret = ''
	local _list = {}
	local case = varCase(t)
	
	local list = {
		{'C', "中国大陆", t.cn},
		{'H', "香港", t.hk},
		{'T', "台湾", t.tw},
		{'CH', "中国大陆和香港", t.cn},
		{'HT', "香港和台湾", t.tw},
		{'CT', "中国大陆和台湾", t.cn},
		{'CT2', "中国大陆和台湾", t.tw},
	}
	local varTag = {}

		
	for i, v in ipairs(list) do
		if v[3] == "en" then
			varTag[v[1]] = v[2] .. "使用英文"
		else
			varTag[v[1]] = v[2] .. "译作“<b>" .. v[3] .. '</b>”'
		end
	end

	local function gen(a)
		local listVar = { '', '-hans', '-hant', '-cn', '-hk', '-mo', '-sg', '-tw', }
		local r = '-{ '
		for i, v in ipairs(listVar) do
			r = r .. 'zh' .. v .. ':-{zh; zh-hans; zh-hant;|' .. a[i] ..  '}-; '
		end
		r = r .. '}-'
		
		return r
	end
	
	if case == '' then
 		return ''
	elseif case == 'CHT' then
		_list = { 
			varTag.C .. '，' ..  varTag.H .. '，' ..  varTag.T, -- zh
			varTag.C .. '，' ..  varTag.H .. '，' ..  varTag.T, -- zh-hans
			varTag.C .. '，' ..  varTag.H .. '，' ..  varTag.T, -- zh-hant
			varTag.H .. '，' ..  varTag.T, -- zh-cn
			varTag.C .. '，' .. varTag.T, -- zh-hk
			varTag.C .. '，' .. varTag.T, -- zh-mo
			varTag.C .. '，' ..  varTag.H .. '，' ..  varTag.T, -- zh-sg
			varTag.C .. '，' ..  varTag.H -- zh-tw
		}
		
	elseif case == 'CTT' then
		_list = { 
			varTag.C .. '，' ..  varTag.HT, -- zh
			varTag.C .. '，' ..  varTag.HT, -- zh-hans
			varTag.C .. '，' ..  varTag.HT, -- zh-hant
			varTag.HT, -- zh-cn
			varTag.C, -- zh-hk
			varTag.C, -- zh-mo
			varTag.C .. '，' ..  varTag.HT, -- zh-sg
			varTag.C -- zh-tw
		}
				
	elseif case == 'CCT' then
		_list = { 
			varTag.CH .. '，' ..  varTag.T, -- zh
			varTag.CH .. '，' ..  varTag.T, -- zh-hans
			varTag.CH .. '，' ..  varTag.T, -- zh-hant
			varTag.T, -- zh-cn
			varTag.T, -- zh-hk
			varTag.T, -- zh-mo
			varTag.CH .. '，' ..  varTag.T, -- zh-sg
			varTag.CH -- zh-tw
		}
	
	elseif case == 'CHC' then
		_list = { 
			varTag.CT .. '，' ..  varTag.H, -- zh
			varTag.CT .. '，' ..  varTag.H, -- zh-hans
			varTag.CT .. '，' ..  varTag.H, -- zh-hant
			varTag.H, -- zh-cn
			varTag.CT, -- zh-hk
			varTag.CT, -- zh-mo
			varTag.CT .. '，' ..  varTag.H, -- zh-sg
			varTag.H -- zh-tw
		}	

	elseif case == 'THT' then
		_list = { 
			varTag.CT2 .. '，' ..  varTag.H, -- zh
			varTag.CT2 .. '，' ..  varTag.H, -- zh-hans
			varTag.CT2 .. '，' ..  varTag.H, -- zh-hant
			varTag.H, -- zh-cn
			varTag.CT2, -- zh-hk
			varTag.CT2, -- zh-mo
			varTag.CT2 .. '，' ..  varTag.H, -- zh-sg
			varTag.H -- zh-tw
		}
	end
	
	return gen(_list)
end

local function link(cont)

	if yesno(_link, true) then
		if yesno(_lead) then
			cont = '[['_.._cont_.._'|' .. cont .. ']]'
		end
		cont = cont .. '：'
	else
		cont = ''
	end

	return cont

end

function p.nihongo_title(frame)
	
	local ret 
	local _ret
	
	local args = getArgs(frame, {
		frameOnly= true;
		valueFunc = function (key, value)
			if value == nil and value ~= 'no' then 
				return ''
			else
				return value
			end
		end;
	})
	
	_link = args.link
	_lead = args.lead

	if args[1] ~= '' and args[2] ~= '' then
		
		ret = '《<b>' .. args[1] .. '</b>》' .. '<span style="font-weight: normal">（' .. link('日语') .. '<span lang="ja" xml:lang="ja">-{' .. args[2] .. '}-</span>'
		
		if args[3] ~= '' then
			
			ret = ret .. '，' .. link('英语') .. '<span lang="en" xml:lang="en">-{<i>' .. args[3] .. '</i>}-</span>'
			
		end
		
		if args.cn ~= '' and args.tw ~= '' then
			
			ret = ret .. '，' .. chi(args)
			
		end
		
		if args[4] ~= '' then
			
			ret = ret .. '，' .. args[4]
			
		end
		
		ret = ret .. '）'
		
		if args[5] ~= '' then
			
			ret = ret .. '　' .. args[5]
			
		end
		
		ret = ret .. '</span>'
	end
	

	return ret
	
end
	
return p