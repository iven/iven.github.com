---
title: "关于 C++ 中模板类（Template Class）在多文件中的问题"
date: 2009-04-27 08:29
categories:
- 编程
tags:
- c
---

最近 C++ 学到模板类了，老师要做一个模板类的题目。

一直以来我们都是保持着类声明和类实现分别写在头文件和 CPP
文件中这个不错的习惯，这次也没有例外，然而这次问题却出来了。

先是在 g++ 中提示：

    undefined reference to `Array::Array(int, int const*)’

移到 VC++ 6.0 后又提示：

    ex_08_1.obj : error LNK2001: unresolved external symbol “public:
    __thiscall Array<int>::~Array<int>(void)”
    (<??1?$Array@H@@QAE@XZ>)ex_08_1.obj : error LNK2001: unresolved
    external symbol “public: __thiscall
    Array<int>::Array<int>(int,int const *)”
    (<??0?$Array@H@@QAE@HPBH@Z>)

到底是怎么回事呢？老师说是编译器的 BUG，我却觉得没那么简单。

搜索了一下，才发现，C++
中模板类（或者叫“类模板”）的声明和实现和普通类是不同的，模板类的声明有两种模式：包含编译模式和分离编译模式。

包含编译模式就是把声明和实现写在同一个文件中；分离编译模式当然就是写在不同文件中，不过用这种形式的时候，要在类的声明前加上
export 关键字。

我在 g++ 上试了一下，出现：

    警告：关键字‘export’未实现，将被忽略

汗一个……VC++ 上更不用说了……

C++ 真是个复杂的东西，还是写在一个文件里吧……

