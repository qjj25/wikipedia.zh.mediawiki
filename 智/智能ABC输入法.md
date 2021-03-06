{{NoteTA|G1=IT|G2=Windows}}
{{Refimprove|time=2017-03-17T10:24:08+00:00}}
{{IME|朱守涛|2000|[[汉语拼音|汉语拼音]]、[[音形码|音形码]]}}
'''智能ABC输入法'''（又稱作'''标准输入法'''<ref>{{cite book|title=中文版Windows XP 实用教程(21世纪电脑学校)|date=2005|publisher=清华大学出版社有限公司|isbn=9787302111740|pages=105|accessdate=2017-03-17}}</ref>）是运行于[[Microsoft_Windows|Microsoft Windows]]之下的[[汉语拼音输入法|汉语拼音输入法]]软件。大多数人都把智能ABC归纳入[[拼音输入法|拼音输入法]]，其实该输入法身兼两职，既可以纯拼音输入，又可以音形码输入。智能ABC因捆绑于Microsoft Windows简体中文版操作系统而一举成名，曾经是中国大陆使用人数最多的输入法软件。此软件是[[北京大学|北京大学]]教授[[朱守涛|朱守涛]]发明的，开发于北京大学科技开发部。智能ABC的最新版本为5.23。{{fact}}

== 双拼方案 ==
智能ABC支持[[双拼|双拼]]输入，它包含了一种定-{}-製的双拼方案，其键位-{}-图为：
[[File:Intelligent_ABC_Double_Pinyin_Scheme.png|left]]
{{clr}}

== 智能ABC的缺点 ==
智能ABC与其他输入法相比，它不能够随着拼音符号的输入立刻显示出字词，而需要先按一下空格键，才能显示出选字菜单，不够直观；而且在输入长句时，句中的每个字或词都要按一下空格加以确认，较为繁琐。这是因为智能ABC有一个特殊功能，在音节之后可以输入一个数字，代表某个笔画，这样候选字中就都是以该笔画开头的字，减少选字时间（尤其是生僻字）。第二个缺点便是智能ABC升级慢，詞庫也没有其他的输入法多。由于需要按空格键才出现选字菜单，以及软件功能和詞庫依赖系统版本，更新缓慢、不足的缺点，随着互联网的发达，智能ABC的用户大量流失到[[搜狗拼音输入法|搜狗拼音输入法]]等新兴的输入法软件。

由于智能ABC只存在于简体中文版Microsoft Windows操作系统中，而Windows NT 5.x系列操作系统中只有[[Windows_Server_2003|Windows Server 2003]]存在64位简体中文版，故捆绑于该操作系统中的智能ABC输入法5.0版为该输入法唯一的64位版本。然而64位版智能ABC在图形界面下使用时却无法弹出输入法状态栏，只能依靠盲打，命令行界面下工作正常。该操作系统中附带的32位版智能ABC在32位软件中使用时会提示找不到詞庫、基础表等文件，在32位命令行界面下使用时工作正常，将<source lang="dos" inline>winabc.cwd</source>与<source lang="dos" inline>winabc.ovl</source>两个文件由<source lang="dos" inline>%SystemRoot%\system32</source>复制到<source lang="dos" inline>%SystemRoot%\SysWOW64</source>即可解决该问题{{efn|在64位Windows Server 2003操作系统中，<source lang="dos" inline>%SystemRoot%\SysWOW64</source>目录下只有智能ABC输入法的本体文件<source lang="dos" inline>winabc.ime</source>，该文件亦同时存在于<source lang="dos" inline>%SystemRoot%\system32</source>目录下，其他两个文件仅存在于<source lang="dos" inline>%SystemRoot%\system32</source>目录下。}}。

另外，由于智能ABC推出时间较早，缺乏对[[Unicode|Unicode]]的原生支持，因此只要在「控制面板」的「区域和语言选项」中将「非Unicode程序的语言」由「-{zh-hans:中文（中国）;zh-hant:中文（PRC）;}-」改为其他语言，智能ABC便会无法使用。

== 被模仿 ==
由于智能ABC升级极慢，该输入法上次的升级是在2012年还停留在32位，而很多输入法已经升级到64位{{efn|事实上，智能ABC输入法的64位版本早在Windows Server 2003 x64简体中文版发布时便已推出，但从未进行过更新。}}，其他输入法为争夺智能ABC的用户纷纷推出智能ABC风格输入，其中模仿得最相似的是QQ拼音输入法中的智能ABC风格输入。

但是QQ输入法智能ABC风格输入缺少了智能ABC输入法中的两大功能。其一就是按回车键进行按字转换，该功能在输入人名的时候特别有用，由于人名不是固定词按字转换会更简便且能快速地将人名记忆起来方便日后调用；其二是缺少了智能ABC的强制记忆功能，该功能强制记忆词的最大长度为15个字，方便人们打自定义常用的词。

==参见==
*[[郑码|郑码]]
*[[双拼|双拼]]
*[[五笔字型输入法|五笔字型输入法]]

==注释==
{{notelist}}

==参考资料==
{{reflist}}

==外部链接==
* [https://web.archive.org/web/20061025180424/http://www.znabc.com/ 官方网站]

{{漢語輸入法}}

[[Category:汉语拼音输入法|Category:汉语拼音输入法]]
[[Category:音形码|Category:音形码]]