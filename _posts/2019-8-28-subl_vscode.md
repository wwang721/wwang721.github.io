---
layout: post
title: "Sublime Text & VS Code 配置使用"
tagline: "漫谈两款优秀文本编辑器的配置使用..."
#categories: 
#author: ""
#meta: ""
---
啰里啰嗦说了一大堆 ...... 但这篇文章其实不仅仅是个编辑器编程环境的配置教程，也简单介绍了一些常见的概念，并谈了谈我个人对其的理解。

## **IDE 漫谈**

<hr style="height:5px;" />
对于刚入门的同学来说，<font color="#26975b"><b>集成开发环境</b></font> ( **IDE** , Integrated Development Environment ) 是一个很好的选择，但是长期使用 IDE 可能会影响我们对文件系统的理解。

* 常见的 IDE 有[**微软公司**](https://www.microsoft.com) ( **Microsoft** ***Inc.*** ) 的 [**Visual Studio**](https://www.visualstudio.com) 和[**苹果公司**](https://www.apple.com)（ **Apple** ***Inc.*** ）的 [**Xcode**](https://developer.apple.com/xcode/) , 它们功能丰富各有千秋，但是只能在自家的系统上很好的运行，虽然 Visual Studio 已经有了 MacOS 版本，但那实际上只是个半成品，很多语言都还不支持。
 <br>
 <br>
* 总部位于捷克共和国首都布拉格的 [***JetBrains***](http://www.jetbrains.com) 公司发布的 **[CLion](http://www.jetbrains.com/clion)、[PyCharm](http://www.jetbrains.com/pycharm/)、 [IntelliJ IDEA](http://www.jetbrains.com/idea/)** 等跨平台的 IDE ，在 Windows、 MacOS、 Linux 系统上都能很好的运行。

* 这些优秀的 IDE 在资深 coder 手里能发挥出更高的效率，但是它们大多体积臃肿甚至能达到10几个G。而且优秀的 IDE 一般都不是开源软件，上述的 Visual Studio 价格感人，JetBrains 的订阅价格也不低 ( **学生和老师用学校邮箱订阅可以免费** ) , Xcode 虽然是免费软件，但前提是你得买个 Mac 。

* IDE 往往都是一键编译运行然后 debug 的，在操作上方便不少。但是习惯于 IDE 操作的同学在服务器上面对黑乎乎的命令行往往就不知所措了，搞不清文件之间的依赖关系。我相信经过学习文本编辑器的配置后，会对编译过程有更加深刻的理解。

## **Editor 漫谈**

<hr style="height:5px;" />
最常见的<font color="#26975b"><b>文本编辑器</b></font> ( Editor ) 可能就是 Windows 上的**记事本**了，用过 Linux 系统的同学可能还知道 [**Vi/Vim**](https://www.vim.org) 和 [**Emacs**](http://www.gnu.org/software/emacs/)，我之前就有[<u><b>一篇文章</b></u>]({{ site.url }}/2019/05/21/Vim-notes.html)总结了一些 Vim 的常用命令。
Vim 和 Emacs 是两款历史悠久的文本编辑器，都有着 “**编辑器之神**” 的称号。

* **Emacs** ( Editor Macros , 编辑器宏 ) 的作者是 [<font color="#26975b"><b><u>GNU 革奴计划</u></b></font>](http://www.gnu.org) ( gnu 在英文中原意为**非洲牛羚**，发音与 new 相同，GNU 应当发音为 Guh-NOO 以避免与 new 混淆 ) 的创立者、**自由软件运动**的精神领袖、著名黑客 --- **理查德·马修·斯托曼** (Richard Matthew Stallman)。<br><br>这里简单介绍下 **GNU** ( "**GNU is Not Unix**" 的递归缩写 ) 系统，它是革奴 ( GNU ) 计划的主要目标，一个自由的操作系统，它的内容软件完全以 **GPL** ( GNU General Public License , GNU 通用公共许可证 ) 开源发布。<br><br>我们熟知的开源系统 Linux 就是包涵了 Linux 内核与一些 GNU 组件和软件，比如 GNU 编译器套件 [**GCC**](http://gcc.gnu.org) ( GNU Compiler Collection ) 和 GNU debug 调试器 [**GDB**](http://www.gnu.org/s/gdb/) 以及文本编辑器 Emacs , 所以有人认为 Linux 系统的正式名称应该是 <font color="#26975b"><b>GNU/Linux 操作系统</b></font>。

* **Vi** 是 Unix 及 Linux 系统的标准编辑器，由伯克利的计算机科学家 Bill Joy 创立。而 **Vim** 在 Vi 的基础上改进和增加了很多特性，被推崇为类 Vi 编辑器中最好的一个。<br><br>开始 Vim 的目标只是在 Amiga 计算机上完全复制 Vi 的功能，那个时候的 Vim 只是 **Vi Imitation** 的简称，1992 年 1.22 版本的 Vim 被移植到了 [UNIX](http://www.unix.org) 和 MS-DOS 系统上。从那个时候开始，Vim 的全名就变成 **Vi Improved** 了。

Vim 的劲敌来自 Emacs 的不同变体。1999 年 Emacs 被选为 Linuxworld 文本编辑分类的优胜者，Vim 屈居第二。但在 2000 年 2 月 Vim 赢得了 Slashdot Beanie 的最佳开放源代码文本编辑器大奖，又将 Emacs 推至二线。

总的来看, Vim 和 Emacs 在文本编辑方面都是非常优秀的，但是他们的 <font color="#26975b"><b>GUI</b></font> ( Graphical User Interface , 图形用户界面 ) 做得都不太适合鼠标操作 ( 比如 Mac 版的 [**MacVim**](http://www.macvim.org) , 尽管有了很大进步，但是鼠标操作还是很不方便 ) ，习惯了鼠标点击的初学者学起来可能有困难。

所以我在这里推荐两款优秀的跨平台文本编辑器 [<font color="#26975b"><b><u>Sublime Text</u></b></font>](http://www.sublimetext.com) 和 [<font color="#26975b"><b><u>Visual Studio Code</u></b></font>](https://code.visualstudio.com) **!** 

## **Sublime Text 配置**

<hr style="height:5px;" />
**Sublime Text** 其实是一款收费软件，但是即便不激活也不影响你的正常使用，只是偶尔会弹出提示框提醒购买许可证，收费是 $80。

主题、字体、文件图标等美化插件的配置我都不详细讲了，我个人比较喜欢 <font color="#26975b"><b>Monokai</b></font> 配色，几乎所有编辑器和 IDE 我都用了这个配色。在这我主要讲一下 Sublime Text 自带的编译系统。

<span id="systemCompiler"></span>

### **系统编译器** 

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />
* MacOS 和 Linux 系统配置起来比较容易，简单几步就可以完成：<br><br>
	* 两者系统一般都自带了 Python 2.X , 如果想用更新的版本，如 3.6 或者 3.7 ，可以去官网 [***<u>https://www.python.org</u>***](https://www.python.org) 下载，或者安装 [**Anaconda**](https://www.anaconda.com) 进行配置;
	
	* 至于 C/C++ , 不同版本的 Linux 系统使用它们自带的**安装包管理工具**，如 [**apt**](https://launchpad.net/ubuntu/+source/apt/) ( Advanced Packaging Tool )、[**rpm**](https://rpm.org) ( Red-Hat Package Manager )、 [**yum**](http://yum.baseurl.org) ( Yellow dog Updater, Modified ) 直接 install gcc、gdb 等组件就好了。<br><br>Mac 系统则可以使用自带安装包管理工具 [**Homebrew**](https://brew.sh) 来 install ，或者直接在 [**App Store**](https://www.apple.com/ios/app-store/) 里下载 Xcode ，安装完就自动配置好 C/C++ 的环境了。值得一提的是，有的系统版本的 Mac 可能无法正常运行 gdb ，所以<font color="#26975b"><b><u>推荐直接下载 Xcode</u></b> </font>，就算用不到 IDE ，但是 Xcode 配置好的 [**Clang**](http://clang.llvm.org) 和 [**lldb**](http://lldb.llvm.org) 可以取代 gcc 和 gdb 在 Mac 下很好的工作。安装 Xcode 后的 Mac 在终端使用 gcc/g++ 其实就是在使用 Clang 的别名。<br><br>
<img src='https://raw.githubusercontent.com/NoNo721/Pictures/master/arrow.png' alt="arrow" title="right arrow" style='float:left; width:30px;height:10 px'/>这里简单介绍下 [**LLVM**](https://llvm.org) 构架编译器 ( **compiler** ) 框架系统，它的命名最早源自于<font color="#26975b"><b>底层虚拟机</b></font>（ Low Level Virtual Machine ）的缩写，由于命名带来的混乱，目前 LLVM 就是该项目的全称。LLVM 计划启动于 2000 年，最初由美国 [**UIUC**](https://illinois.edu) ( University of Illinois at Urbana-Champaign , 伊利诺伊大学厄巴纳-香槟分校 ) 的 **Chris Lattner** 博士主持开展，以 C++ 编写而成，用于优化以任意程序语言编写的程序的<u>编译时间、链接时间、运行时间以及空闲时间</u>，对开发者保持开放，并兼容已有脚本。2006 年 Chris Lattner 加盟 **Apple** ***Inc.*** 并致力于 LLVM 在 Apple 开发体系中的应用。Apple 也是 LLVM 计划的主要资助者。项目中的 Clang 和 lldb 等软件也兼容 GNU 规范，已经广泛被用于 [**苹果 IOS 开发工具**](https://developer.apple.com)、[**Facebook**](https://www.facebook.com)、[**Google**](http://www.google.com) 等各大公司。

<br>

* Windows 系统稍微麻烦一些，而且注意 Windows 路径使用的是<font color="#26975b"><b>反斜杠</b></font> `\` 分隔:<br><br>
	* 如果之前下载过 [**Dev-C++**](https://bloodshed-dev-c.en.softonic.com) 或者 [**Code::Blocks**](http://www.codeblocks.org) 等 IDE ，可以使用它们自带的编译器，只要配置好路径就行了。
	
	* 没有用过 IDE 的同学可以下载 [**MinGW**](http://www.mingw.org) ( Minimalist GNU for Windows ), 通过它下载配置 GCC 和 GDB 等 GNU 组件，记得下载完将 MinGW 安装目录下的 **bin** 文件夹添加到系统环境变量 PATH 里（ Win10系统: `桌面-此电脑-右键-属性-高级系统设置-高级-环境变量` ) ; 
	
	* Python 可以到 [***<u>https://www.python.org</u>***](https://www.python.org) 官网下载，也可以直接下载 [**Anaconda**](https://www.anaconda.com) 进行配置，记得也要添加安装目录里的 python.exe 的路径到系统环境变量 PATH 里。注意在 Windows 的 **PowerShell** 里无法直接 `conda activate base` 激活 base 环境， 目前的解决方案是使用 **CMD** 来执行该命令。

### **Sublime Text 编译系统**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />
打开 Sublime Text，选择 `工具-编译系统` 可以看到自带的多种编译系统，其中可能有的能够正常使用，而有的不能，对应的配置文件在安装目录下找到 **Packages** 文件夹，里面有很多 XXX.sublime-package ( XXX 是对应语言，如 C++、Python 等 ) 文件，这些其实就是 **zip** 压缩文件，复制一个出来将后缀名改为 .zip 就可以解压看到里面的 XXX.sulime-build 文件。

一般<font color="#26975b"><b>不推荐直接修改自带的编译系统</b></font>，但是如果想把自己改过的 .sublime-build 文件放入 .build-package 中，可以使用 `zip` 命令:

1. `sudo zip -d XXX.sublime-package XXX.sublime-build`: 删除原有的 .sublime-build 文件;
2. `sudo zip -g XXX.sublime-package /path/to/XXX.sublime-build`: 将新的 .sublime-build 文件放入;
3. 重启 Sublime Text 就 OK 了。

我们也可以<font color="#26975b"><b>新建自己的编译系统</b></font>，选择 `工具-编译系统-编译新系统` 就会生成一个新的 xxx.sublime-build 文件，其实这就是一个 **JSON** ( JavaScript Object Notation , JS 对象简谱 ) 文件，是一种轻量级的数据交换格式。我给出一个 Python 编译系统的模板：

``` json
{
	"encoding": "utf-8",
	"working_dir": "$file_path",
	"shell_cmd": "/usr/bin/python -u \"$file\"",
	"file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
	"selector": "source.python",

	"variants":
	[
		{
			"name": "Run",
			"shell_cmd": "/usr/bin/python -u \"$file\"",
		}
	]
}
```

看上去很简单，主要就是要将编译器路径配置正确。

<br>
<img src='https://raw.githubusercontent.com/NoNo721/Pictures/master/arrow.png' alt="arrow" title="right arrow" style='float:left; width:30px;height:10 px'/>
这里简单提一下 python 的 **-u** 参数，python 的**标准错误**是直接输出的，但是**标准输出**却要先停留在**缓冲区**等待，-u 参数可以让标准输出不停留在缓冲区而直接输出，所以一般都会把 -u 这个参数加上。

<br>

后面的 “**variants**” 标签部分其实就是 Sublime Text 的`工具` 选项里**编译** ( Compile ) 和**运行** ( Run ) 的区别，标签外就是 `编译` 执行的部分, 而 "variant" 内就是 `Run` 执行的部分 （ 当然，对于 Python 这种**解释型**语言没有什么区别 )。进入 `偏好设置/首选项-浏览程序包` ，打开 **User** 文件夹就可以找到<u><b>自定义的编译系统</b></u>。

配置完成后打开想要编译执行的代码，按 `Command/Ctrl+B` 就可以编译，或者按 `Shift+Command/Ctrl+B` 快捷键就可以直接运行了。


## **Visual Studio Code 配置**

<hr style="height:5px;" />
**Visual Studio Code** 作为微软公司的**开源**编辑器，不仅名字继承于微软的 IDE **Visual Studio** ，图标也和 Visual Studio 很相似。微软出品的产品质量都很有保障，但配置起来可能会让初学者一头雾水。

同样，主题、字体、文件图标等美化插件的配置我都不详细讲了，推荐一款 “**Monokai GRS**” 的主题配色，可以直接在 Visual Studio Code 内嵌的**拓展应用商店**里搜到。如果觉得英文 **UI** ( User Interface , 用户界面 ) 使用起来有困难，可以在拓展应用商店里下载微软官方汉化插件 "**Chinese (Simplified) Language Pack for Visual Studio Code**" 进行汉化。

简单谈谈 VS Code 的设置，微软最近的产品设置使用的都是 JSON 文件，按照 **用户设置-工作区设置-文件夹设置** 分级，越往后优先级越高，后一级会覆盖前一级的设置。更改设置后会在工作文件夹中生成一个 **.vscode** 隐藏文件夹，里面有一个 **settings.json** 文件，这就是你的文件夹设置文件。

### **Visual Studio Code 编译配置**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />
在 VS Code 中编译运行程序，同样首先得配置好系统的编译器和 debug 工具，在上面关于 Sublime Text 的部分中[**已经说过**](#systemCompiler "系统编译器")，这里不再赘述。

配置好后用 VS Code 打开工作文件夹和代码，选择 `终端-配置任务`，对于 C/C++ 可以直接选择 `C/C++: g++ build active file` , VS Code 会在 .vscode 中自动生成一个 **task.json** 文件，我们几乎不用去更改它。

对于 Python 代码，则只能选择 `使用模板创建task.json文件-Others` 生成 task.json 文件，这样得到的基本配置文件为：

``` json
{
    // See https://go.microsoft.com
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "echo",
            "type": "shell",
            "command": "echo Hello"
        }
    ]
}
```

这就是一个输出 "Hello" 的 task , 我们大致修改一下

``` json
{
    // See https://go.microsoft.com
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "pybuild",
            "type": "shell",
            "command": "/usr/python",
            "args": [
                "-u",
                "${file}"
            ]
        }
    ]
}
```

其中 "**label**" 标签大致就是任务名称，最重要的是在 “**command**” 里正确配置编译器路径，并且给 “**args**” ( **arguments** ) 标签里加上一些 -flag，根据需要自行确定 ( `${file}` 代表当前程序的文件名 ) 。

<br>
<img src='https://raw.githubusercontent.com/NoNo721/Pictures/master/arrow.png' alt="arrow" title="right arrow" style='float:left; width:30px;height:10 px'/>
这里简单谈谈 <font color="#26975b"><b>arg</b></font> 这个变量名，我们经常在 C/C++ 里看到：

``` cpp
int main(int argc, char *argv[])
```
其中 **argc** 代表传入 main 函数的参数个数，即 **argument count** ;
而 **argv** 代表传入 main 函数的参数序列或指针，即 **argument vector** 。

<br>

保存配置后选择 `终端-配置默认生成任务`，选择更名后的 task “label” , VS Code 会自动在 task.json 里添加一小段 "**group**" 设置分组的代码：

``` json
{
    // See https://go.microsoft.com
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "pybuild",
            "type": "shell",
            "command": "/usr/python",
            "args": [
                "-u",
                "${file}"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        }
    ]
}
```
这个操作其实就是将当前 task 分入 **build** 分组，使用 `Shift+Command/Ctrl+B` 快捷键会默认执行 build 分组中的 task 。

### **Visual Studio Code 调试配置**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />
* 完成 task.json 配置后，选择 `调试-打开配置`，对于 C/C++ 直接选择 `C++ (GDB/LLDB)` 就会在 .vscode 文件夹里生成 **launch.json** 文件，我们几乎也不用去更改它。

* 对于 Python 代码， 这回也有 `Python File` 这个选项了，也可以自动生成 launch.json 文件。

编译后 ( 对于 python 这种解释型语言不需要编译 ) 我们按 `F5` 就可以进行 debug 了。 不需要使用插件，VS Code 就支持在每一行的行号前的空位处直接鼠标**左键**设置<font color="#26975b"><b>断点</b></font> ( **breakpoint** ) ，调试起来很方便。

### **Code Runner 插件**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />
对于一些很简单的程序，如果不需要 debug 可以直接运行，我们只需要在**拓展应用商店**里下载 “**Code Runner**” 插件。下载完成后， VS Code 的界面右上方就会出现一个代表**运行** ( Run ) 的**三角形图标**， 直接左键点击就可以执行了。

也可以在 settings.json 中进行自定义设置:
``` json
{
    ...,
	
    // Set the executor of each language.
    "code-runner.executorMap": {
        "cpp": "cd $dir && g++ *.cpp -o $fileNameWithoutExt && $dir$fileNameWithoutExt",
        "python": "python -u",
        ...
    },
    
    ...
}
```

## **结语**

<hr style="height:5px;" />
到此 **Sublime Text** 和 **Visual Studio Code** 两款编辑器的编程环境配置差不多就已经完成了，更多高级的设置和功能需要在日常使用中慢慢学习探索。

按着这个过程一路配置下来应该也不会是一帆风顺的，边琢磨边实验可以加深对其的理解，希望各位都会有所收获。🎉 🎉 🎉 


&ensp;

[<b><u>Go to the Home Page</u></b>]({{ site.url }}{{ site.baseurl }})

&ensp;

<center class="half">
<font color="#26975b"><b>Sponsor the author </b></font><font color="#08a2e4"><b>if you like the contents!</b></font><br/><br/>
</center>

<center class="half">
    <img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/WechatPay.png" width="251" style="margin-right:10px;margin-left:10px"/><img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/AliPay.png" width="250" style="margin-right:10px;margin-left:10px"/>
</center>

&ensp;