---
layout: post
title: "Sublime Text & VS code 配置使用"
tagline: "漫谈两款优秀文本编辑器的配置使用..."
#categories: 
#author: ""
#meta: ""
---
啰里啰嗦说了一大堆。这篇文章不仅仅是个配置教程，也简单介绍了一些概念并谈了谈我个人的理解。

## **IDE 漫谈**

<hr style="height:5px;" />

对于刚入门的同学来说，集成开发环境 （ **IDE** , Integrated Development Environment ）是一个很好的选择，但是长期使用 IDE 可能会影响我们对文件系统的理解。

* 常见的 IDE 有微软公司 ( Microsoft Inc. ) 的 **Visual Studio** 和苹果公司（ Apple Inc. ）的 **Xcode** , 它们功能丰富各有千秋，但是只能在自家的系统上很好的运行，虽然 Visual Studio 已经有了 MacOS 版本，但那实际上只是个半成品，很多语言都还不支持。
 <br>
 <br>
* 位于捷克共和国首都布拉格的 **JetBrains** 公司发布的 **CLion、PyCharm、 IntelliJ IDEA** 等跨平台的 IDE ，在 Windows、 MacOS、 Linux 系统上都能很好的运行。

这些优秀的 IDE 在资深 coder 手里能发挥出更高的效率，但是它们大多体积臃肿甚至能达到10几个G。而且优秀的 IDE 一般都不是开源软件，上述的 Visual Studio 价格感人，JetBrains 的订阅价格也不低 (**学生和老师用学校邮箱订阅可以免费**) , Xcode 虽然是免费软件，但前提是你得买个 Mac 。

IDE 往往都是一键编译运行然后 debug 的，在操作上方便不少。但是习惯于 IDE 操作的同学在服务器上面对黑乎乎的命令行往往就不知所措了，搞不清文件之间的依赖关系。我相信经过学习文本编辑器的配置后，会对编译过程有更加深刻的理解。

## **Editor 漫谈**

<hr style="height:5px;" />

最常见的文本编辑器 ( Editor ) 可能就是 Windows 上的记事本了，用过 Linux 系统的同学可能还知道 **Vi/Vim** 和 **Emacs**，我之前就有[一篇文章]({{ site.url }}/2019/05/21/Vim-notes.html)总结了一些 Vim 的常用命令。
Vim 和 Emacs 是两款很老的文本编辑器，都有着 “**编辑器之神**” 的称号。

* **Emacs** ( Editor Macros , 编辑器宏 ) 的作者是 **GNU 革奴计划**的创立者、自由软件运动的精神领袖、著名黑客 --- **理查德·马修·斯托曼**（Richard Matthew Stallman）。这里简单介绍下 GNU ( "**GNU is Not Unix**" 的递归缩写 ) 系统，它是革奴 ( GNU ) 计划的主要目标，一个自由的操作系统，它的内容软件完全以 **GPL** ( GNU 通用公共许可证, GNU General Public License ) 开源发布。我们熟知的开源系统 Linux 就是包涵了 Linux 内核与一些 GNU 组件和软件，比如 GNU 编译器套件 **GCC** ( GNU Compiler Collection ) 和 GNU debug 调试器 **GDB** 以及文本编辑器 Emacs , 所以有人认为 Linux 系统的正式名称应该是 GNU/Linux 操作系统。

* **Vi** 是 Unix 及 Linux 系统的标准编辑器，由伯克利的计算机科学家 Bill Joy 创立。而 **Vim** 在 Vi 的基础上改进和增加了很多特性，被推崇为类 Vi 编辑器中最好的一个。开始 Vim 的目标只是在 Amiga 计算机上完全复制 Vi 的功能，那个时候的 Vim 只是 Vi Imitation（模拟）的简称， 1992 年 1.22 版本的 Vim 被移植到了 UNIX 和 MS-DOS 系统上。从那个时候开始，Vim 的全名就变成 Vi Improved 了。

Vim 的劲敌来自 Emacs 的不同变体。1999 年 Emacs 被选为 Linuxworld 文本编辑分类的优胜者，Vim 屈居第二。但在 2000 年 2 月 Vim 赢得了 Slashdot Beanie 的最佳开放源代码文本编辑器大奖，又将 Emacs 推至二线。总的来看, Vim 和 Emacs 在文本编辑方面都是非常优秀的，但是他们的 GUI ( Graphical User Interface , 图形用户界面 ) 做得都不太适合鼠标操作 ( 比如 Mac 版的 **MacVim**, 尽管有了很大进步，但是鼠标操作还是很不方便 ) ，习惯了鼠标点击的初学者可能学起来有困难。

所以我在这里推荐两款优秀的跨平台文本编辑器 **Sublime Text** 和 **Visual Studio Code !** 

## **Sublime Text 配置**

<hr style="height:5px;" />

**Sublime Text** 其实是一款收费软件，但是即便不激活也不影响你的正常使用，只是偶尔会弹出提示框提醒购买。主题、字体、文件图标等美化插件的配置我都不详细讲了，我个人比较喜欢 **Monokai** 配色，几乎所有编辑器和 IDE 我都用了这个配色。在这我主要讲一下 Sublime Text 自带的编译系统。

### **系统编译器**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />

* MacOS 和 Linux 系统都自带了 GCC 和 Python 等编译器，配置起来很方便。
* Windows 系统稍微麻烦一些，而且注意 Windows 路径使用的是 `\` 分隔:
	* 如果之前下载过 **Dev-C++** 或者 **Code::Blocks** 等 IDE ，可以使用它们自带的编译器，只要配置好路径就行了。
	* 没有用过的可以下载 **MinGW** ( Minimalist GNU for Windows ), 通过它下载配置 GCC 和 GDB 等 GNU 组件，记得下载完将 MinGW 安装目录下的 **bin** 文件夹添加到系统环境变量 PATH 里（ `桌面-计算机-右键-属性` ) ; 
	* Python 可以到 Python 官网下载也可以直接下载 **Anaconda** 配置，注意 **Powershell** 里不能 `conda activate base` 激活 base 环境， 打开 **Cmd** 执行该命令即可。

### **Sublime Text 编译系统**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />

打开 Sublime Text，选择 `工具-编译系统` 可以看到自带的多种编译系统，其中可能有的能够正常使用，而有的不能，对应的配置文件在安装目录下找到 Packages 文件夹，里面有很多 XXX.sublime-package ( XXX 是对应语言，如 C++、Python 等 ) 文件，这些其实就是 zip 压缩文件，复制一个出来将后缀名改为 .zip 就可以解压看到里面的 XXX.sulime-build 文件。不推荐直接修改自带的编译系统，但是如果自己改过的 .sublime-build 文件想放入 .build-package 可以用 `zip` 命令:

1. `sudo zip -d XXX.sublime-package XXX.sublime-build`: 删除原有的 .sublime-build 文件;
2. `sudo zip -g XXX.sublime-package /path/to/XXX.sublime-build`: 将新的 .sublime-build 文件放入;
3. 重启 Sublime Text 就 OK 了。

我们也可以新建自己的编译系统，选择 `工具-编译系统-编译新系统` 就会生成一个新的 xxx.sublime-build 文件，其实这就是一个 JSON 文件，我给出一个Python编译系统的模板：

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

后面的 “variants” 标签部分其实就是 Sublime Text 的`工具` 选项里编译 ( Compile ) 和运行 ( Run ) 的区别，标签外就是 `编译` 执行的部分, 而 "variant" 内就是 `Run` 执行的部分 （ 当然，对于 Python 这种解释型语言没有什么区别 )。进入 `偏好设置/首选项-浏览程序包` ，打开 User 文件夹就可以找到自定义的编译系统。

配置完成后打开想要编译执行的代码，按 `Command/Ctrl+B` 就可以编译，或者按 `Shift+Command/Ctrl+B` 就可以直接运行了。


## **Visual Studio Code 配置**

<hr style="height:5px;" />

作为微软公司的开源编辑器，品质质量都很有保障，但配置起来可能会让初学者一头雾水。
同样，主题、字体、文件图标等美化插件的配置我都不详细讲了，推荐一款 “**Monokai GRS**” 的主题配色，可以直接在拓展应用商店里搜到，如果觉得英文界面有困难，可以在拓展应用商店里下载 "**Chinese (Simplified) Language Pack for Visual Studio Code**" 微软官方汉化插件进行汉化。

简单谈谈 VS Code 的设置，它的设置使用的都是 JSON 文件，按照 **用户设置-工作区设置-文件夹设置** 分级，越后优先级越高，后一级会覆盖前一级的设置。更改设置后会在工作文件夹中生成一个 **.vscode** 文件夹，里面有一个 **setting.json** 文件，它就是你的文件夹设置。

### **Visual Studio Code 编译配置**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />

在 VS Code 中编译运行程序，同样首先得配置好系统的编译器和 debug 工具。配置好后用 VS Code 打开工作文件夹和代码，选择 `终端-配置任务`，对于 C/C++ 可以直接选择 `C/C++: g++ build active file`, VS Code 会在 .vscode 中生成一个 **task.json** 文件，我们几乎不用去更改它。对于 Python 代码，则只能选择 `使用模板创建task.json文件-Others`生成 task.json 文件，这样得到的基本配置为：

``` json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
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
    // See https://go.microsoft.com/fwlink/?LinkId=733558
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

其中 "label" 标签大致就是任务名称，最重要的是在 “command” 里正确配置编译器路径，并且给 “**args**” ( **arguments** ) 标签里加上一些 -flag，根据需要自行确定。

<br>
<img src='https://raw.githubusercontent.com/NoNo721/Pictures/master/arrow.png' alt="arrow" title="right arrow" style='float:left; width:30px;height:10 px'/>
这里简单谈谈 **arg** 这个变量名，我们经常在 C/C++ 里看到：

``` cpp
int main(int argc, char *argv[])
```
其中 **argc** 代表传入 main 函数的参数个数，即 **argument count** ;
而 **argv** 代表传入main函数的参数序列或指针，即 **argument vector** 。

<br>

保存配置后选择 `终端-配置默认生成任务`，选择更名后的 “label” , VS Code 会自动在 task.json 里添加一小段代码变成：

``` json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
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
这个操作其实就是将当前 task 分入 build 分组，然后我们用 `Shift+Command/Ctrl+B` 快捷键就会默认执行这个 task 了。

### **Visual Studio Code 调试配置**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />

完成 task.json 配置后，选择 `调试-打开配置`，对于 C/C++ 直接选择 `C++ (GDB/LLDB)` 就会在 .vscode 文件夹里生成 **launch.json** 文件，我们也几乎不用去更改它。对于 Python 代码， 这回也有 `Python File` 这个选项了，也可以自动生成 launch.json 文件。在编译后我们按 `F5` 就可以进行 debug 了， 不需要使用插件，VS Code 就支持在每一行的行号前的空位直接**左键**设置断点，调试起来很方便。

### **Code Runner**

<hr style="height:1px;border:none;border-top:1px dashed #1c6eb4" />

对于一些很简单的程序，如果不需要 debug ，只要直接运行就可以的，我们只需要在拓展应用商店里下载 “**Code Runner**” 插件。下载完后， VS Code 的右上方就会出现一个代表**运行** ( Run ) 的三角形图标, 直接左键点击就可以执行了。




&ensp;

[Go to the Home Page]({{ site.url }}{{ site.baseurl }})