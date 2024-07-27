# Along32 中文注释版

[英文版源码位： http://along32.sourceforge.net](http://along32.sourceforge.net)


学习书籍《汇编语言（基于intel x86处理器）第5版 - Kip R. Irvine》时，需使用Irvine32库，但该库仅能运行在windows环境中。于是Curtis Wong编写了一个Linux环境中基于Nasm的函数库Along3，用于学习基于intel的汇编语言。

该库可以在Linux（x86）或其他POSIX兼容的操作系统下使用，但它只在Linux下进行过测试，由于Linux和Windows设计模式的不同，Irvine32中的函数和宏并没有全部重写，而是重写了其中的核心部分。在您开始使用Along32库编程之前，请阅读Along32.inc中的注释，以确保您想要的函数包含在库中。

在您开始使用Along32库之前，请阅读Along32.inc中的注释，以确保您想要的函数包含在库中。


## 1. 编译安装Along32

安装Along32 lib非常简单，只需几个简单步骤。

   1. `cd src`
       切换当前路径到src
   2. `make`
       编译库
   3. `make install`
       将库安装到你的Linux系统中，默认位置是`/usr/lib`。首先，应确保拥有足够的权限将库安装到该位置。sudo是最好的解决方案。
   4. 安装完成!

## 2. 使用

安装库后，您可以轻松使用其中的函数和宏。

   1. 在.asm源文件中包含Along32.inc，这一步是使用这些功能的关键，不要忘记。
   2. 扫描Along32.inc以查找您想要的功能。某些函数的用法包含在src/Along32.asm中，或者您可以在《汇编语言（基于intel x86处理器）第5版 - Kip R. Irvine》中详细阅读。
   3. 完成你的汇编程序。
   4. 用NASM汇编你的源文件，在组装之前，请确保您的nasm已正确安装。然后键入以下命令： `nasm -f elf -o objfile srcfile` ，其中 `objfile` 是对象文件的名称，通常以 `.o` 作为后缀， `srcfile` 是程序集源文件。
   5. 使用Along32库将目标文件链接到二进制程序中。键入以下命令： `ld -lAlong32 --dynamic-linker /lib/ld-linux.so.2 -o binfile objfil` 其中 `binfil` 是最终程序的名称， `objfile` 是最后一步生成的目标文件。
   6. 享受你的程序和Along32库。


---------------------------------------------------------------

此外，还创建了一些宏来模拟MASM中的伪指令。如果您想使用这些功能，请阅读Macros_沿着.inc中的注释以获取更多信息。要使用这些宏，只需包含该文件，然后根据上述说明构建程序。

欲了解更多信息或错误报告，请发送电子邮件给我：[airekans@gmail.com](mailto:airekans@gmail.com)

## 版权

Along32库位于GNU LGPL之下。有关详细信息，请参阅文件COPYING和COPYING.LESSER。
