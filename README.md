# win11_new_machine
个人新电脑配置备忘。

## 必要的初始化设置

### 上网设置

手机上设置里面搜索“USB共享网络”，然后打开，打开后使用手机通过数据线连接到电脑后，电脑就可以上网。

### 代理软件下载

下载[快连](https://oss.wvlwqx.cn/)。

下点windows的版本，然后登陆账号，如果设备已经满了，可以先剔除一个设备。

### 输入法设置

首先设置电脑的输入法，搜索网上的小鹤双拼的键位图，然后按照键位图设置正确，并且打开容易误导的模糊音，候选词导航中打开逗号和句号的翻页功能，自动扩展到全屏的功能关闭，输入法的默认语言设置为英文，方便编程。

零声母模式选择->韵母的第一个字母（两个字母的韵母为全拼）
然后下面的自定义按键按照下面的来映射：

```txt
Q->iu
W->ei
R->uan
T->ue ve
Y->un
U->sh
I->ch
O->uo
P->ie
A->a
S>iong ong
D->ai
F->en
G->eng
H->ang
J->a
K->ing uai
L->lang uang
Z->ou
X->ia ua
C->ao
V->zh ui
B->in
N->iao
M->ian
```

### 其他必要的小步骤

#### 交换电脑上的ESC

https://github.com/qindapao/my_vim_config

在这个页面上搜索“ESC”的关键字，然后能看到教程。

#### 恢复经典的右键菜单。

在桌面上右键，然后选择在终端中打开。然后复制下面的命令：

```powershell
reg.exe add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /f /ve
```

按回车键执行命令。然后按下 `Ctrl + Alt + Delete`，打开“任务管理器”,在“进程”选项卡中找到“Windows 资源管理器”，右键点击它并选择“重新启动”。

#### 调整键盘的灵敏度

按 Win + R 打开运行对话框，输入 control keyboard 并按回车。

如果发现无法直接打开运行对话框，可以找到cmd命令行，然后以管理员的身份运行。

在“键盘属性”窗口中，选择“速度”选项卡。

调整“重复延迟”和“重复速率”滑块以设置你想要的速度。

点击“应用”然后“确定”保存更改。


## 重要软件和工具安装


### 下载notepad--文本编辑器。

https://gitee.com/cxasm/notepad--/releases/tag/v3.6.1

### vim

https://github.com/vim/vim-win32-installer/releases

先安装vim，固定安装到这个目录：D:\programes\vim
安装完后把这个目录也加入到环境变量中。

最开始我安装的是`1-16`号补丁，当前现在安装的最新的是`1-44`号补丁。因为不知道什么原因导致的，现在的最新的`windows`系统的构建版本有下面的问题:

就是无法识别`Shift`键了，比如：`Ctrl+V`和`Ctrl+Shift+V`对于编辑器来说都是一个按键，按键码都是`22`。对于其他的组合情况也是这样。

验证方法是在vim的命令行中输入：`:echo getchar()`，然后按`Ctrl+V`；重复这个动作，然后按`Ctrl+SHift+V`，就可以测试是否是相同的按键。

但是呢，使用老版本的`gvim`补丁，比如当前使用的`16`号或者`44`号补丁，只能安装`python3.12`。如果安装最新版本的`python`，某些插件，比如：`LeaderF`就会不正常！

1. 安装完vim后我们需要手动安装 vim-plug插件。

https://github.com/junegunn/vim-plug

下载`plug.vim`，然后放置到`autoload`目录下。

2. https://github.com/LuaJIT/LuaJIT

下载解压后使用msys2的环境进入源码目录后直接make。
然后在可执行文件的目录下建立目录`lua\jit\`，并把源码的`src\jit`目录下的所有文件都拷贝到这个目录中来。

3. gvim的终端环境配置。
如果要使用`msys2`的`ucrt64`环境，那么需要用下面的包装脚本。放到msys2的根目录下面。

```bash
ucrt64_bash.bat
```

然后`vim`中像下面这样配置。

```vim
let g:terminal_cwd = 1
let g:terminal_shell = 'D:/msys64/ucrt64_bash.bat'
```

`coc.nvim`是一个很大的插件，具体安装什么子插件，依需求而定。

### 7zip

https://github.com/ip7z/7zip

### 百度网盘

### msys2执行环境

直接从百度网盘中的备份的拿出来解压后使用ucrt64终端即可。
在`msys64_备份`目录中。

### git

https://git-scm.com/install/windows

安装好了后设置用户名和密码

```bash
git config --global user.name QinQing
git config --global user.password xxxxxxxxxx
git config --global user.email "northisland2017@gmail.com"
```

### python

https://www.python.org/downloads/windows/

### nodejs

注意安装的时候不要勾选完整构建环境的安装，会出问题。暂时也不需要。

### go

下载链接：https://go.dev/dl/

然后安装到这个路径：`D:\go\bin`。安装完成后把：`D:\go\bin`添加到系统环境变量中。
其实可能并没有必要，因为安装程序自动就添加到了环境变量中。

### 字体

[MappleMono](https://github.com/subframe7536/maple-font)

### zim

### everything

https://www.voidtools.com/zh-cn/

### shellcheck

https://github.com/koalaman/shellcheck
windows: shellcheck-v0.9.0.zip set shellcheck.exe to PATH

### shfmt

https://github.com/mvdan/sh => shfmt_v3.7.0_windows_amd64.exe

放置到vim能找到的可执行路径后需要把名字修改成 `shfmt.exe`

### gtags

http://adoxa.altervista.org/global/

放置后记得把路径添加到环境变量中，比如：`D:\programes\vim\glob\bin`

### ctags

https://github.com/universal-ctags/ctags-win32

配置在`_vimrc`的注释中的自定义格式。

```txt
" tagbar 配置 {
" conf.ctags 配置 C:\Users\xx\ctags.d\conf.ctags
"
" --langdef=asciidocx
" --langmap=asciidocx:.ad.adoc.asciidoc
" --regex-asciidocx=/^=[ \t]+([^[:cntrl:]]+)/o \1/h/
" --regex-asciidocx=/^==[ \t]+([^[:cntrl:]]+)/. \1/h/
" --regex-asciidocx=/^===[ \t]+([^[:cntrl:]]+)/. . \1/h/
" --regex-asciidocx=/^====[ \t]+([^[:cntrl:]]+)/. . . \1/h/
" --regex-asciidocx=/^=====[ \t]+([^[:cntrl:]]+)/. . . . \1/h/
" --regex-asciidocx=/^======[ \t]+([^[:cntrl:]]+)/. . . . \1/h/
" --regex-asciidocx=/^=======[ \t]+([^[:cntrl:]]+)/. . . . \1/h/
" --regex-asciidocx=/\[\[([^]]+)\]\]/\1/a/
" --regex-asciidocx=/^\.([^ \t\.][^[:cntrl:]]+)/\1/t/
" --regex-asciidocx=/image::([^\[]+)/\1/i/
" --regex-asciidocx=/image:([^:][^\[]+)/\1/I/
" --regex-asciidocx=/include::([^\[]+)/\1/n/


" --langdef=txt
" --langmap=txt:.txt
" --regex-txt=/^(\={6}\s)(\S.+)(\s\={6})$/\2/h,heading/
" --regex-txt=/^(\={5}\s)(\S.+)(\s\={5})$/. 2/h,heading/
" --regex-txt=/^(\={4}\s)(\S.+)(\s\={4})$/.   \2/h,heading/
" --regex-txt=/^(\={3}\s)(\S.+)(\s\={3})$/.     \2/h,heading/
" --regex-txt=/^(\={2}\s)(\S.+)(\s\={2})$/.       \2/h,heading/

" --langdef=zim
" --langmap=zim:.txt
" --regex-zim=/^(\={6}\s)(\S.+)(\s\={6})$/\2/h,heading/
" --regex-zim=/^(\={5}\s)(\S.+)(\s\={5})$/. \2/h,heading/
" --regex-zim=/^(\={4}\s)(\S.+)(\s\={4})$/.   \2/h,heading/
" --regex-zim=/^(\={3}\s)(\S.+)(\s\={3})$/.     \2/h,heading/
" --regex-zim=/^(\={2}\s)(\S.+)(\s\={2})$/.       \2/h,heading/
```


### ripgrep
https://github.com/BurntSushi/ripgrep

### clang

https://github.com/llvm/llvm-project
安装完后记得加入环境变量中。

### Go编译依赖的软件

https://github.com/qindapao/common_tool
按照这个项目的要求安装相关的软件。

然后需要把相关的目录添加到：`msys2`的`ucrt64`终端的默认`shell`的`.bashrc`文件的末尾。
把其他的经常用到的可执行文件的目录也添加进来。

```bash
echo 'export PATH=${PATH}:/d/go/bin' >> ~/.bashrc
echo 'export PATH=${PATH}:/d/programes/ImageMagick-7.1.2-Q16-HDRI' >> ~/.bashrc
echo 'export PATH=${PATH}:/c/Users/admin/go' >> ~/.bashrc
echo 'export PATH=${PATH}:/c/Users/admin/go/bin' >> ~/.bashrc
echo 'export PATH=${PATH}:/d/programes/vim' >> ~/.bashrc
echo 'export PATH=${PATH}:/d/programes/vim/glob/bin' >> ~/.bashrc
source ~/.bashrc
```

### trans

项目地址：https://github.com/soimort/translate-shell
可执行文件下载地址：https://raw.githubusercontent.com/soimort/translate-shell/gh-pages/trans

下载后应该放到`msys2`或者是当前机器的默认`shell`的可执行目录中。

### snippaste


### 屏幕录屏软件和按键记录软件

把 git go 的路径加入到msys2中的.bashrc的PATH环境变量中去。


