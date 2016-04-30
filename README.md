## 简介

之前用 LaTex 完成毕业论文，顺手就写了这个模板，之后就没怎么去维护。转眼就过了一年，前两天看到了这个项目第一个 [PR](https://github.com/clinyong/latex-szu/pull/1)，考虑着要怎么合并，就把这个项目克隆到本地，没想到，居然编译出错!

不过想想也正常，从上次写完论文之后，就基本没有在自己的电脑上面编译过 LaTex，中间又是升级系统，又是升级 Sublime。

还好之前写过一篇[博客](http://www.jianshu.com/p/e59aaac15088)，但是发现里面也没怎么提及安装这个过程，只是引用了一篇文章，实在是太不负责任了！所以这次打算把安装过程好好记录下来。

## 安装

因为我自己用的是 [OS X](http://www.apple.com/cn/osx/)，所以只能提供这个平台的安装方法，欢迎帮忙补充其它平台的方法。

### OS X

先安装 [MacTex Basic](http://tug.org/cgi-bin/mactex-download/BasicTeX.pkg)，安装的位置是在

```
/usr/local/texlive/2015basic
```

然后把下面这个路径加到 PATH 当中

```
/usr/local/texlive/2015basic/bin/x86_64-darwin
```

这时候你在终端输入 `tlmgr` 应该会有输出。因为 MacTex 我们装的是基础版，所以还要安装一些第三方库，执行

```
$ sudo tlmgr update --self
$ sudo tlmgr install latexmk lastpage
```

这样 MacTex 这边就算配置完成了。接下来就是安装 [Sublime](https://www.sublimetext.com/)，[Package Control](https://packagecontrol.io/)，还有 [LaTeXTools](https://github.com/SublimeText/LaTeXTools)。

然后配置一下 LaTexTools，打开 `Preferences | Package Settings | LaTeXTools | Settings - User`，然后定位到 `Platform settings` 这一节，改成下面像这样

```
// ------------------------------------------------------------------
// Platform settings: adapt as needed for your machine
// ------------------------------------------------------------------

    "osx":  {
        // Path used when invoking tex & friends; MUST include $PATH
        "texpath" : "/usr/local/texlive/2015basic/bin/x86_64-darwin:$PATH"
        // Path to PDF viewer, if needed
        // TODO think about it. Also, maybe configure it here!
    },
```

用 Sublime 打开这个项目，按 `Ctrl - b` 应该就可以顺利编译了。
