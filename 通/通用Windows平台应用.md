{{noteTA|G1=IT}}
[[File:Khan_Academy_Metro_app_(player).png|thumb]]
[[File:Wikipedia_App_snapped_to_Windows_8_desktop.png|thumb]]，粗邊框和[[用戶界面|用戶界面]]。<br/>右邊：Metro風格應用程式；主要由內容組成]]
'''通用Windows平台应用'''，也称'''Metro风格应用'''，是一种通過[[Windows应用商店|Windows应用商店]]向[[Microsoft_Windows|Microsoft Windows]]作業系統分發的[[移动应用程序|移動應用程式]]，它們不同於在設計、開發、分發以及內容上不同於傳統桌面應用程式。

==感觀==
[[File:Window_(windowing_system).svg|thumb]]
傳統的桌面軟體運行於[[窗口_(计算机)|窗口]]內，有它們自己的邊框，以區分彼此。邊框上還會附著用於顯示應用程式標題的標題欄，系統菜單、偶爾也會有一組最大化、最小化、關閉和求助按鈕置於其上。框圍軟體的窗口可水平或垂直的更改尺寸。它們是由用戶界面中可見的元素控制，包括[[菜单_(计算机)|菜單]]、[[工具栏|工具欄]]、[[ribbon|繃帶]]、滾動條以及窗口邊框。在Windows Vista和Windows 7中這些元素變得更加複雜，以至於需要特定的應用程式來做截屏。

在[[Windows_8|Windows 8]]中，Metro風格應用程式不運行於窗口中。它們或者是佔據了整個熒屏；或者是移到熒屏的一側，而佔據了熒屏的那個垂直部分。Metro風格應用程式沒有傳統的用戶界面，沒有標題欄、沒有系統窗口、沒有窗口邊框、也沒有控制按鈕等等，真正的應和了微軟常說的“內容才是主角”的口號。但必要的命令界面像滾動條這樣的界面元素還是有的，不過起初被隱藏起來。Metro風格應用程式在他們自己的界面中並沒有菜單，而是借用置於[[Windows_shell#The_charms|Settings charm]]中的特製菜單。

根據用戶的反饋，微軟逐漸寬鬆了這種無界面元素的規則。在[[Windows_8.1|Windows 8.1]]中，標題欄被引入但處於隱藏的狀態，除非用戶將滑鼠滑越於熒屏頂端，否則它決不會現身。[[Windows_10|Windows 10]]引入了[[平板模式|平板模式]]，平板電腦安裝後會自動開啟這種模式；而在桌面或筆電中它被默認是關閉的，但卻可手動開啟與關閉。當這種模式關閉時，運行於桌面的Metro風格應用程式有可見的標題欄，大小也是可調的。當平板模式開啟後，Metro風格應用回退至Windows 8.1時的樣式，所有應用程式都以最大化呈現佔據著整個熒屏，不可調節尺寸。<ref>{{cite web|last1=Seifert|first1=Dan|title=The nine most important updates in Windows 10|url=http://www.theverge.com/2015/7/29/9060177/microsoft-windows-10-update-changes-browser-start-menu-cortana-xbox#list-item-5|website=[[The_Verge|The Verge]]|publisher=[[Vox_Media|Vox Media]]|date=29 July 2015}}</ref><ref>{{Cite web|url = http://www.theverge.com/2015/7/28/9045331/microsoft-windows-10-review|title = Windows 10 review|date = 28 July 2015|accessdate = |website = [[The_Verge|The Verge]]|publisher = [[Vox_Media|Vox Media]]|last = Warren|first = Tom}}</ref><ref>{{Cite web|url = http://www.zdnet.com/article/windows-10-a-new-beginning/|title = Windows 10: A new beginning|date = 28 July 2015|accessdate = |website = [[ZDNet|ZDNet]]|publisher = [[CBS_Interactive|CBS Interactive]]|last = Bott|first = Ed}}</ref>

此外，Windows 10也將設定Charm移除，被一種稱之為“漢堡菜單”的系統菜單變體所取代。

==分發和授權==

此前，Windows可以安裝來自於任何地方的應用程式，無論是隨身碟還是網際網。但對於Metro風格應用程式來說，只能夠透過Windows商店來購買安裝。購買而來的Metro風格應用程式與賬戶綁定，因此無論身處何處，都可通過同一帳戶安裝於不同的設備中。然而在Windows 10中安裝次數得以受限。

==多任務==

Windows 8之前，任務欄被用於抽選正在運行的程式，而在Windows 8中運行中的Metro風格應用程式是通過熒屏左側特定的應用選擇器來選取。<ref>{{cite web|title=Switch between open apps|url=http://www.microsoft.com/surface/en-us/support/apps-and-windows-store/how-to-switch-between-apps?lc=1033|work=[[Microsoft_Surface|Microsoft Surface]] manual|publisher=[[Microsoft|Microsoft]]|accessdate=31 December 2013}}</ref>

==生命週期==

在Metro風格應用程式出現以前，軟體的運轉與結束都可由用戶控制，比如雙擊圖標開始，單擊關閉按鈕結束。然而Metro應用程式是沉浸式的，可能在用戶還未開啟它們時，系統已將其啟用；而當用戶關閉後，系統可能還在保留它們在後臺工作。Metro風格應用程式的生存週期是由Windows應用管理員根據系統資源利用情形而自行管理的。

==開發==
===Windows運行時===

傳統的應用程式是通過使用[[Windows_API|Windows API]]庫函數在計算機語言下開發的，人們可以自由選擇喜愛的開發工具與開發語言。然而要開發Metro風格應用程式便須使用WinRT運行時庫，並且對於系統函數的調用加以限制，未能資質驗證通過的應用是無法在Windows商店中上架的。

並不是每個使用WinRT運行時庫的應用都是Metro風格應用；WinRT中的有些功能也可被桌面應用程式所利用。<ref>{{cite web|title=Windows Runtime APIs for desktop apps|url=https://msdn.microsoft.com/en-us/library/windows/desktop/dn554295%28v=vs.85%29.aspx|website=[[MSDN|MSDN]]|publisher=[[Microsoft|Microsoft]]|accessdate=31 July 2015}}</ref>


Metro風格應用程式只能使用微軟自家的開發工具開發。雖然聲稱可以在多種語言下互操作，但自行嘗試實現對窗口運行時的綁定將導致失敗。根據[[Embarcadero_Technologies|Embarcadero Technologies]]的首席科學家Allen Bauer所說，這裡有些編程接口幾乎是所有程式開始者所必須調用的，但是卻得到微軟的禁止，除非是使用微軟自家的[[Visual_C++|Visual C++]]運行時才行。<ref>{{cite web|last=Grange|first=Eric|title=Why no native WinRT support in Delphi XE3?|url=http://www.delphitools.info/2012/08/23/why-no-native-winrt-support-in-delphi-xe3/|work=DelphiTools|accessdate=13 January 2014|date=23 August 2012}}</ref><ref>{{cite web|last=Anderson|first=Tim|title=Third-party compilers locked out of Windows Runtime development|url=http://www.itwriting.com/blog/6347-third-party-compilers-locked-out-of-windows-runtime-development.html|work=Tim Anderson's ITWriting|accessdate=13 January 2014|date=23 August 2012}}</ref><ref>{{cite web|last=Bauer|first=Allen|title=HTML5 Builder|url=https://forums.embarcadero.com/message.jspa?messageID=484319#484319|work=Embarcadero Developer Network|publisher=Embarcadero Technologies|accessdate=13 January 2014|date=22 August 2012}}</ref>

===通用應用===
可同時運行於[[智慧型電話|智慧型電話]]、[[個人電腦|個人電腦]]、[[遊戲終端|遊戲終端]]和[[HoloLens|HoloLens]]的應用稱之''為通用應用''。這是通過使用通用應用接口來完成的，最早出現於Windows 8.1和[[Windows_Phone_8.1|Windows Phone 8.1]]中。[[Visual_Studio_2013|Visual Studio 2013]] with Update 2起可以開發這類應用程式。<ref>{{cite web|last1=Waheed|first1=Ahmed|title=A first look at the Windows 10 universal app platform|url=http://blogs.msdn.com/b/msgulfcommunity/archive/2015/03/02/a-first-look-at-the-windows-10-universal-app-platform.aspx|website=Microsoft Gulf Technical Community blog|publisher=[[Microsoft|Microsoft]]|date=2 March 2015}}</ref><ref>{{cite journal|last1=Appel|first1=Rachel|title=Modern Apps : Build Universal Apps for the Windows Platform|url=https://msdn.microsoft.com/en-us/magazine/dn781364.aspx|website=[[MSDN_Magazine|MSDN Magazine]]|publisher=[[Microsoft|Microsoft]]|date=September 2014|volume=29|number=9}}</ref>Windows 10為開發通用應用而引入了通用Windows平台10。使用Visual Studio 2015可以利用這一平台開發這樣的應用。早先的Windows 8.1、Windows Phone 8.1的應用需要經過修改後才可遷移至此平台。<ref>{{cite web|title=Migrate apps to the Universal Windows Platform (UWP)|url=https://msdn.microsoft.com/library/mt148501.aspx|website=[[MSDN|MSDN]]|publisher=[[Microsoft|Microsoft]]|accessdate=31 July 2015}}</ref><ref>{{cite web|title=Move from Windows Runtime 8.x to UWP|url=https://msdn.microsoft.com/en-us/library/windows/apps/xaml/mt238322.aspx|website=[[MSDN|Windows Developer Center]]|publisher=[[Microsoft|Microsoft]]|accessdate=31 July 2015}}</ref>

特定Windows平台並不是一個不同於WinRT的開發庫，相反只是它的擴展。通用應用不再是為特定作業系統而編寫的，相反，它們定位於一個或多個不同的設備，比如桌面、移動、電玩XBox以至于物聯網。只要設備能力允許，那麼它們便可運行。一個通用應用可以在智慧型電話和平板上運行，並提供差不多的體驗。運行於智慧型電話的通用應用在連接到熒屏後會可能會與運行於平板之上相同。<ref>{{cite web|title=Guide to Universal Windows Platform (UWP) apps|url=https://msdn.microsoft.com/en-us/library/windows/apps/xaml/dn894631.aspx|website=[[MSDN|Windows Developers Center]]|publisher=[[Microsoft|Microsoft]]|accessdate=31 July 2015}}</ref>

===APPX===
'''APPX'''是用於分發和安裝Metro風格應用程式文件格式，它使用於桌面和移動版的Windows<ref>[http://msdn.microsoft.com/en-us/library/windows/apps/hh464929.aspx App packages and deployment (Windows Store apps) (Windows)<!-- Bot generated title -->]</ref>。 為了統一桌面版和移動版中的應用，在[[Windows_Phone_8.1|Windows Phone 8.1]]中，XAP文件格式也被APPX取代。<ref>[http://www.theverge.com/2014/2/11/5400660/windows-phone-8-1-features-leaked Windows Phone 8.1 includes universal apps and lots of feature updates - The Verge]</ref>APPX文件僅兼容Windows Phone 8.1和之後的版本<ref>[http://www.wphoneapps.net/2013/12/how-to-install-xap-file-on-windows-phone.html How to Install Appx File on Windows Phone 8.1]</ref>。

Windows電話市場允許用戶將APPX文件下載至SD卡中並手動安裝它們。但在桌面系統，如Windows 8，這樣的做法是被禁止的，除非用戶可得到開發者許可或使用在商業域中的電腦。<ref>[http://www.howtogeek.com/129535/how-to-sideload-modern-apps-on-windows-8/ How To Sideload Modern Apps on Windows 8 - HowToGeek]</ref>

==安全性==

Windows軟體只要它們希望便有使用和改變他們生態系統的能力。Windows賬戶權限，用戶賬戶控制面板和殺毒軟體嘗試在應用試圖這麼做前通知並讓用戶干預他們的做法，以至於免於它們帶來的威脅。然而Metro風格應用軟體運行於沙盒中，是無法永遠改變Windows作業系統的生態環境的。它們需要權限才可訪問硬體資源，比如網際錄影機和麥克風，而且它們也僅能使用用戶文檔，比如我的文檔。微軟進一步的協調這些應用，並當在發現它們帶來安全和隱私問題時刪除它們。<ref>{{cite web |title=Microsoft talks Windows Store features, Metro app sandboxing for Windows 8 developers |url=http://www.theverge.com/2012/5/17/3026590/microsoft-windows-8-developers-windows-store-sandboxing |work=[[The_Verge|The Verge]] |publisher=[[Vox_Media|Vox Media]] |date=17 May 2012 |accessdate=12 January 2013 |first=Chris |last=Ziegler}}</ref><ref name=bi-windows8>{{cite web |last=Rosoff |first=Matt |title=Here's Everything You Wanted To Know About Microsoft's Upcoming iPad Killers |url=http://articles.businessinsider.com/2012-02-09/tech/31040510_1_steven-sinofsky-pcs-microsoft-first |work=[[Business_Insider|Business Insider]] |date=9 February 2012 |accessdate=12 January 2013 |deadurl=yes |archiveurl=https://web.archive.org/web/20130122030754/http://articles.businessinsider.com/2012-02-09/tech/31040510_1_steven-sinofsky-pcs-microsoft-first |archivedate=22 一月 2013 }}</ref>
==参见==
*[[通用Windows平台|通用Windows平台]]（UWP）
*[[Modern_UI|Modern UI]]

==參考资料==
{{Reflist|2}}

[[Category:Microsoft_Windows|Category:Microsoft Windows]]
[[Category:可执行文件格式|Category:可执行文件格式]]
[[Category:应用程序接口|Category:应用程序接口]]
[[Category:.NET|Category:.NET]]