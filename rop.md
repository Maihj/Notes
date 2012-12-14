#Return-Oriented Programming#

##1.Principles of ROP##
在libc等库的代码字节序列中寻找以ret结尾的指针序列，然后将这些指针序列链接，形成能完成简单操作的指令序列(gadget)，并通过这些gadgets串联来完成一些复杂的操作。这些gadgets的组合能形成图灵完备的表述能力。

栈指针取代指令指针后，程序会怎样运行？这个问题的结果就是ROP的原理。

程序层：一个普通程序是由一系列的在text段的机器指令组成。一个面向返回的程序是由栈段的一个特殊层组成的，每一个RO指令指向栈上的一个指令序列（大小为一个字），栈指针指向下一个RO指令。

无操作指令：在ROP中，nop包含一个ret指令的地址。

立即数的编码：little-endian

控制流：在普通程序中跳转通过改变eip的值，在ROP中跳转通过esp。

Gadgets：读地址，再读该地址的内存。包含一个或多个指令序列指针和相关的立即数。

##2.Return-Oriented Exploitation##
一个RO程序是被安排好的一个或多个gadgets，包含这些gadgets的负荷必须放到被利用的程序的内存里，栈指针重定向到指向第一个gadget，实现这些任务最简单的方法是通过栈的缓冲区溢出：将gadgets放到已经溢出的栈中，那个第一个gadget会覆盖某些函数的指令指针，当这个函数返回时，RO程序会执行。但是栈溢出并不是必须的，包含ROP的负荷可以在堆中，攻击者可以用一个代码片段的地址重写函数指针：设置esp=第一个gadget的地址，然后执行return。

##3.ROP攻击方法##
1)分析libc库中的代码片段，获取包含以ret结尾的指令序列，并获取这些序列的起始地址：trie树
2)构建gadgets，自动化？how？
Load/Store
Arithmetic and Logic
Control Flow
System Calls
Function Calls
Shellcode
3)组织gadgets进行运算，使用ROP构建return-oriented rootkit？
