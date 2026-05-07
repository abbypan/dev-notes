vim
#####

简单入门
--------

+-----------------------------------+-----------------------------------+
| 资料                              | 简介                              |
+===================================+===================================+
| 七个有效的文本编辑习惯            | 经典                              |
+-----------------------------------+-----------------------------------+
| `最佳vim技巧 <                    | 经典                              |
| http://bbs.byr.cn/wForum/elite.ph |                                   |
| p?file=/groups/sci.faq/Linux/linu |                                   |
| xSoftUsage/VI/M.1116044565.s0>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `不是打vi的广告                   | 实例                              |
|  <http://greenisland.csie.nctu.ed |                                   |
| u.tw/wp/category/comuter/vim/>`__ |                                   |
+-----------------------------------+-----------------------------------+
| vim hacks                         | PPT                               |
+-----------------------------------+-----------------------------------+

站点
----

+-----------------------------------+-----------------------------------+
| 站点                              | 简介                              |
+===================================+===================================+
| `vi Complete Key Binding          | 不错的手册页                      |
| List <http://hea-www.har          |                                   |
| vard.edu/%7Efine/Tech/vi.html>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `Efficient Editing With           | 不错，可以看                      |
| vim <http://robertam              |                                   |
| es.com/files/vim-editing.html>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `Colors Sampler                   | 一堆color scheme配色              |
| Packer <http://www.vim.org/scr    |                                   |
| ipts/script.php?script_id=625>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `vim tips                         | wiki                              |
| wiki <http://vim.wikia.com/>`__   |                                   |
+-----------------------------------+-----------------------------------+
| `vim参考手册 <http:/              | 碰到问题再查                      |
| /vimcdoc.sourceforge.net/doc/>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `vim <http://www.vim.org>`__      | 官网                              |
+-----------------------------------+-----------------------------------+

书籍
----

+-------------------+-------------------+-----------------------------+
| 时间              | 书籍              | 读后感                      |
+===================+===================+=============================+
| 2001              | Vi IMproved       | 很赞，命令有截图。附录Quick |
|                   |                   | Reference超赞。就是书太厚了 |
+-------------------+-------------------+-----------------------------+
| 2010              | hacking vim       | 中规中矩的工具书            |
+-------------------+-------------------+-----------------------------+
| 2008              | Vi(1) Tips        | vi基础操作介绍，还行吧      |
+-------------------+-------------------+-----------------------------+

插件
----

+-----------------------------------+-----------------------------------+
| 插件                              | 用途                              |
+===================================+===================================+
| `L                                | 打开大文件不会卡住                |
| argeFile <http://www.vim.org/scri |                                   |
| pts/script.php?script_id=1506>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `perl-support <http://www.vim     | perl开发                          |
| .org/script.php?script_id=556>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `NERD                             | 代码注释                          |
| C                                 |                                   |
| ommenter <http://www.vim.org/scri |                                   |
| pts/script.php?script_id=1218>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `honza /                          | 代码补全                          |
| vim-snippets <https://            |                                   |
| github.com/honza/vim-snippets>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `neoco                            | 函数补全                          |
| mplcache <http://www.vim.org/scri |                                   |
| pts/script.php?script_id=2620>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `surr                             | word两边加引号标签                |
| ound.vim <http://www.vim.org/scri |                                   |
| pts/script.php?script_id=1697>`__ |                                   |
+-----------------------------------+-----------------------------------+
| `simple                           | ``<leader>f``\ 进行折叠           |
| fold.vim <http://www.vim.org/scri |                                   |
| pts/script.php?script_id=1868>`__ |                                   |
+-----------------------------------+-----------------------------------+

配置
----

打开当前文件所在路径下的其他文件
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

见：\ `Tip #2: easy edit of files in the same
directory <http://www.vim.org/tips/tip.php?tip_id=2>`__

{% highlight vim %} if has(“unix”) map ,e :e =expand(“%:p:h”) . “/” else
map ,e :e =expand(“%:p:h”) . “" endif {% endhighlight %}

Perl-Support 设置
~~~~~~~~~~~~~~~~~

快捷键
^^^^^^

先在\ ``~/.vimrc``\ 设置： ``let g:Perl_MapLeader  = ','``

==== ==================================
按键 作用
==== ==================================
,cfr 块状说明
,cfu 函数说明
,isu 函数说明
,ii  读文件（Ctrl-j跳转到下一个输入点）
,io  写文件
,ip  print “:raw-latex:`\n`”;
,pb  ``[:blank:]``
,rr  运行脚本
,rs  检查语法
.ra  指定脚本运行的参数
,rd  开始debug (也可以按F9)
,rp  阅读perldoc
,ry  运行perltidy整理代码
,hp  perl-support的帮助信息
==== ==================================

时间格式
^^^^^^^^

| {% highlight vim %} let g:Perl_TimestampFormat= ‘%Y-%m-%d %H:%M:%S’
  let g:Perl_FormatDate = ‘%Y-%m-%d’ let g:Perl_FormatTime = ‘%H:%M:%S’
  let g:Perl_FormatYear = ‘Year %Y’
| {% endhighlight %}

Nerd Commenter 代码注释
~~~~~~~~~~~~~~~~~~~~~~~

==== ============================================
按键 作用
==== ============================================
,cc  把选中的行注释掉
,cn  把选中的行注释掉，已注释过的行仍继续加注释符
,c   反注释选中的行
,c$  从光标开始处注释掉当前行
,cA  在当前行结尾处添加注释
==== ============================================

自动识别打开的中文乱码
~~~~~~~~~~~~~~~~~~~~~~

把\ `fencview.vim <http://www.vim.org/scripts/script.php?script_id=1708>`__\ 扔到\ ``~/.vim/plugin``\ 下

在\ ``~/.vimrc``\ 中设置\ ``let g:fencview_autodetect=1``

Windows下的相关编码设置
~~~~~~~~~~~~~~~~~~~~~~~

参考：\ `vim、gvim在windows下中文乱码的终极解决方案 <http://blog.csdn.net/rehung/archive/2007/09/21/1794293.aspx>`__

{% highlight vim %} language mes zh_CN.GBK set langmenu=zh_CN.UTF-8 set
fileencodings=utf-8,cp936,big5,euc-jp,utf-bom,iso8859-1 set
encoding=cp936 set termencoding=cp936 set fileencoding=utf-8 {%
endhighlight %}

正则式very magic
~~~~~~~~~~~~~~~~

`enchanted.vim <http://www.vim.org/scripts/script.php?script_id=4849>`__
让vim正则式一直very magic，省敲字

需要预先安装\ `CRDispatcher.vim <http://www.vim.org/scripts/script.php?script_id=4856>`__

very magic
参考：\ `vim-regexes-are-awesome <http://briancarper.net/blog/448/vim-regexes-are-awesome>`__
