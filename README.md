# An HTTP Request Through Rails

本文是一篇Rails 3.2.13源码阅读的笔记，整理自我的Evernote
我自从12年第四季度开始阅读Rails源代码，最初跟着[《Crafting Rails Applications》](http://pragprog.com/book/jvrails/crafting-rails-applications)阅读，对Rails 3源码有个初步概念。然后开始自己独立阅读，从简单的Sinatra源码读到ActiveSupport库，从i18n库读到Rails启动过程，从复杂的Routes处理读到Rails对于HTTP请求的处理过程，在阅读过程中留下了大量Evernote笔记。这里将其中最核心的HTTP请求部分以Markdown的形式整理出来，也是对自己的一个复习的过程。

挑选一个趁手的Markdown编辑器真是几经周折，刚开始时用[Mou](http://mouapp.com/)编写Markdown文件，由于Mou只能使用```来声明这是一段代码但不能设置具体的编程语言，所以没有代码高亮，造成在Github上读取效果不佳，此外声明的代码之间不能有空行，否则编辑效果会出现错误，最后终于让我难以忍受。改成直接在Github上编辑的方法。希望Mou能尽快更新以解决这个问题。

不过后来我又改用Sublime Text上的[MarkdownEditing](https://github.com/ttscoff/MarkdownEditing)插件编写了，因为感觉Github没有良好的自动保存功能，加上编辑框太小，全屏后高亮完全失去等诸多缺陷。不过MarkdownEditing也并非完美，高亮功能不够理想，另外Sublime Text的WordWrap功能对中文没有支持，Vim Mode下不得不频繁来回切换中英文模式，希望以后改进。

直到最后看到[@SublimePackages](https://twitter.com/SublimePackages)的推荐，用了[Markdown Extended](https://github.com/jonschlinkert/sublime-markdown-extended)这个插件，并且为这个插件Pull Request了Ruby代码高亮的功能，才最终彻底解决了在编辑状态写Ruby代码高亮的问题，在此感谢这个插件的原作者。

另外这篇笔记绝对不会逐字逐句解析代码细节或解释机制，因此需要读者对Ruby语法和Rails机制有着非常深入的理解。另外部分内容可能涉及到Rails的启动机制，对此大家学习<http://railscasts-china.com/episodes/the-rails-initialization-process-by-kenshin54>的视频就已经足够了。

另外，请恕我不是文科出生，难以用华丽的辞藻和幽默风趣的对话吸引读者。读者必须怀着极大的热情和精力才有可能读完并理解本文，否则本文将具有强烈的催眠作用。

Bachue Zhou
