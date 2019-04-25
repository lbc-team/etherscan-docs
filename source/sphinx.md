# 帮助手册-用Markdown写Sphinx

Sphinx 默认是使用reStructuredText(简称reST) 格式进行写作，喜欢Markdown格式可以使用Recommonmark插件来实现。

大部分情况，我们写普通的Markdown格式，如果需需要高级一些的用法，可以看看下面有没有想要的效果：

## Markdown转reST

 ```important::
  Its a note! in markdown!
 ```

 ``` note::
  Its a note! in markdown!
 ```

 ``` warning::
  Its a note! in markdown!
 ```


``` sidebar:: 侧边栏用法

 emphasis-lines:
   highlights the lines.
 linenos:
   shows the line numbers as well.
 caption:
   shown at the top of the code block.
 name:
   may be referenced with `:ref:` later.
```

``` code-block::
     :linenos:
     :emphasize-lines: 3,5
     :caption: 使用code-block 高亮 第3  5行.
     :name: Full code-block example

     # 注释行
     import System
     System.run_emphasis_line
     # code ........................ 很长的代码会自动产生 水平 scrollbar
     System.exit!
```

## 数学公式
``` math::
  E = m c^2

  y=\sum_{i=1}^n g(x_i)
```


## 参考

* [Recommonmark auto_structify ](https://recommonmark.readthedocs.io/en/latest/auto_structify.html)
* [sphinx-rtd-theme](https://sphinx-rtd-theme.readthedocs.io/en/latest/index.html)
* [reStructuredText 格式说明](http://docutils.sourceforge.net/docs/user/rst/quickref.html)
