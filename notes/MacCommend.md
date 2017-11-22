---
layout: notes

---

# Title 
##  Short Key 
cmd+C： 拷贝
cmd+V： 粘贴
cmd+W:  关闭窗口
cmd+Q：退出程序
cmd+I：显示文件/文件夹属性
cmd+Backspace：删除
cmd+shift+3：捕获整个屏幕
cmd+shift+4：捕获选择的区域
cmd+shift+4+space：捕获某个应用程序的窗口
cmd+F：在应用程序中搜索
cmd+Space：用Spotlight进行桌面搜索
fn+Backspace：相当于Windows里面的Delete键（笔记本键盘专用，台式机键盘有Delete键）
 开机时，听到启动音后，按住Option（相当于Windows的Alt）键，可以选择从Windows或者Mac启动。
 开机时，听到启动音后，按住“    T”键，将使计算机进入目标磁盘状态，即通过USB连线，可以将苹果机当作USB硬盘使用。

组合键    功能   
Command-A    选中最前面的 Finder 窗口中的所有项（如果未打开任何窗口则选中桌面内容）   
Option-Command-A    取消选择所有项   
Shift-Command-A    打开“应用程序”文件夹   
Command-C    拷贝所选项/文本至夹纸板   
Shift-Command-C    打开“电脑”窗口   
Command-D    复制所选项   
Shift-Command-D    打开桌面文件夹   
Command-E    推出   
Command-F    查找任何匹配 Spotlight 属性的内容   
Shift-Command-F    查找 Spotlight 文件名匹配项   
Option-Command-F    导航到已打开的 Spotlight 窗口中的搜索栏   
Shift-Command-G    前往文件夹   
Shift-Command-H    打开当前所登录用户帐户的个人文件夹   
Command-I    显示简介   
Option-Command-I    显示检查器   
Control-Command-I    获得摘要信息   
Shift-Command-I    打开 iDisk   
Command-J    调出“显示”选项   
Command-K    连接服务器   
Shift-Command-K    打开“网络”窗口   
Command-L    为所选项制作替身   
Command-M    最小化窗口   
Option-Command-M    最小化所有窗口   
Command-N    新建 Finder 窗口   
Shift-Command-N    新建文件夹   
Option-Command-N    新建智能文件夹   
Command-O    打开所选项   
Shift-Command-Q    注销   
Option-Shift-Command-Q    立即注销   
Command-R    显示（替身的）原身   
Command-T    添加到工具条   
Shift-Command-T    添加到个人收藏   
Option-Command-T    在 Finder 窗口中隐藏工具栏/显示工具栏   
Shift-Command-U    打开“实用工具”文件夹   
Command-V    粘贴   
Command-W    关闭窗口   
Option-Command-W    关闭所有窗口   
Command-X    剪切   
Option-Command-Y    幻灯片显示（Mac OS X 10.5 或更高版本）   
Command-Z    还原/重做   
Command-1    以图标显示   
Command-2    列表方式显示   
Command-3    以分栏方式显示   
Command-4    以 Cover Flow 方式显示（Mac OS X 10.5 或更高版本）   
Command-,（Command 加逗号键）    打开 Finder 偏好设置   
Command-`（重音符键 - 美式英语键盘布局中 Tab 键的上方）    循环显示打开的 Finder 窗口   
Command-Shift-?    打开 Mac 帮助   
Option-Shift-Command-Esc（按住三秒钟）- 仅 Mac OS X v10.5、v10.6 或更高版本    强制退出最前面的应用程序   
Command-[    后退   
Command-]    前进   
Command-上箭头    打开所含文件夹   
Control-Command-上箭头    在新窗口中打开所含文件夹   
Command-下箭头    打开高亮显示的项   
Command-Tab    切换应用程序 - 向前循环   
Shift-Command-Tab    切换应用程序 - 向后循环   
Command-Delete    移到废纸篓   
Shift-Command-Delete    清倒废纸篓




# AppleScript 

tell application "System Events"
	keystroke "k"
	click at {10, 10}
end tell
Variables 
set a to 1  		// a=1
set b to a+1  		// b=a+1
IF  LOOP
if 条件 then  
else  条件
end if 
条件语句         = ,    <= , >= ,     /= (不等)
LOOP循环
repeat with counter from 1 to 3  
    keystroke "a"
end repeat  

repeat 2 times  
    keystroke "a"
end repeat  
Others
(**   注释Command   **)
delay 2   

display dialog "弹出对话框" (**   弹出对话框  **)
Click鼠标
click at {10, 10}
	//  Mac Pro:  1280x800
Key键盘
keystroke "abc"
keystroke return

keystroke "d" using {command down}   
或者
key down command
keystroke "d"
	(** 2种方法 按下 command + d  **)
key up command	   //command键抬起
key code 123	  //command + option + left
key code 表 
1 -35 	asdfhgzxcv§bqweryt123465=97-80]ou[ip
36  Return
37 – 47 	lj'k;\,/nm.
48  Tab
49  Space
50  32  Grave
51  33 Delete
53  35 Escape
55  37 Command
56  38 Shift
57  39 CapsLock
58  3A Option
59  3B Control
60  3C RightShift
61  3D RightOption
62  3E RightControl
63  3F Function
64  40 F17
65  41  KeypadDecimal
67  43  KeypadMultiply
69  45  KeypadPlus
71  47  KeypadClear
72  48 VolumeUp
73  49 VolumeDown
74  4A Mute
75  4B  KeypadDivide
76  4C  KeypadEnter
78  4E  KeypadMinus
79  4F F18
80  50 F19
81  51  KeypadEquals
82  52  Keypad0
83  53  Keypad1
84  54  Keypad2
85  55  Keypad3
86  56  Keypad4
87  57  Keypad5
88  58  Keypad6
89  59  Keypad7
90  5A F20
91  5B  Keypad8
92  5C  Keypad9
93  5D JIS_Yen
94  5E JIS_Underscore
95  5F JIS_KeypadComma
96  60 F5
97  61 F6
98  62 F7
99  63 F3
100  64 F8
101  65 F9
102  66 JIS_Eisu
103  67 F11
104  68 JIS_Kana
105  69 F13
106  6A F16
107  6B F14
109  6D F10
111  6F F12
113  71 F15
114  72 Help
115  73 Home
116  74 PageUp
117  75 ForwardDelete
118  76 F4
119  77 End
120  78 F2
121  79 PageDown
122  7A F1
123  7B LeftArrow
124  7C RightArrow
125  7D DownArrow
126  7E UpArrow


# Terminal 
## 删除 Chess.app 文件
cd /Applications/
sudo rm -rf Chess.app
## 显示隐藏文件
defaults write com.apple.finder AppleShowAllFiles -bool true
killall Finder
### 关闭隐藏
defaults write com.apple.finder AppleShowAllFiles -bool false
killall Finder

