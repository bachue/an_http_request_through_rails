# An HTTP Request Through Rails

本文是一篇Rails 3.2.13源码阅读的笔记，整理自我的Evernote
我自从12年第四季度开始阅读Rails源代码，最初跟着《Crafting Rails Applications》阅读，对Rails 3源码有个初步概念。然后开始自己独立阅读，从简单的Sinatra源码读到ActiveSupport库，从i18n库读到Rails启动过程，从复杂的Routes处理读到Rails对于HTTP请求的处理过程，在阅读过程中留下了大量Evernote笔记。这里将其中HTTP请求以Markdown的形式整理出来，也是对自己的一个复习的过程。

这里所有Markdown均用Mou编写，由于Mou只能使用```来指定代码高亮但不能设置具体的编程语言，所以这里的高亮不是很好看，期待Mou能够解决这个问题。

Bachue Zhou