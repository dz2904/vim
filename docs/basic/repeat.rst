重复上次命令
####################################

在编辑文本时，应该尽量地避免重复的操作，在 Vim 中 ``.`` 命令来重复上一个修改操作。点命令是最简单的命令，然而又是减少重复操作最为有用的命令。

.. note:: 什么是修改操作？

    “修改”可以指很多东西，如删除、修改、增加等，一次修改的单位可以是字符、整行，甚至是整个文件。

    每次进入插入模式时，也会形成一次修改。从进入插入模式的那一刻起（例如，输入 i），直到返回普通模式时为止（输入 <Esc>），Vim 会记录每一个按键操作。做出这样一个修改后再用 ``.`` 命令的话，它将会重新执行所有这些按键操作。

    在 Vim 里，修改操作是不包括移动命令的，因为移动命令不会更新缓冲区的内容。但是以操作开头的命令可以包含移动命令（例如：d2j，删除两行）。


简单的重复
************************************

在 Vim 的普通模式下，先进行修改，然后在输入 ``.`` 命令：

.. highlight:: none

::

    there is somerhing grong here
    x

    here is something wrong here


    here is somerhing grong here
    .

    ere is something wrong here


    ere is somerhing grong here
    .

    re is something wrong here



    there is somerhing grong here
    dw

    is something wrong here


    is somerhing grong here
    .

    something wrong here


    somerhing grong here
    .

    wrong here




    there is somerhing grong here
    ione <esc>

    one there is somerhing grong here


    one there is somerhing grong here
                              .

    one there is one somerhing grong here


使用 ``.`` 命令的最佳编辑模式：用一键移动，另一键执行，即按一次键把光标移到下一个目标上，然后执行重复上次修改。


查找并手动替换
************************************

Vim 中提供了 :substitute 命令专门用于查找替换任务，不过用上面介绍的技术，也可以手动修改第一处地方，然后再一个个地确认替换。

::

    ...We're waiting for content before the site can go live...
    ...If you are content with this, let's go ahead with it...
    ...We'll launch as soon as we have the content...

假设想用单词“copy”来替代“content”。但是，“If you are ‘copy’ with this,”有不是一个句子。所以不能批量的替换，最好的办法就是逐一确认然后在替换。

::

    # 首先搜索单词 content
    /content
    
    ...We're waiting for content before the site can go live...
                                             cwcopy<esc>
    ...If you are content with this, let's go ahead with it...
    ...We'll launch as soon as we have the content...


    ...We're waiting for copy before the site can go live...
                                             n
    ...If you are content with this, let's go ahead with it...
    ...We'll launch as soon as we have the content...


    ...We're waiting for copy before the site can go live...
    ...If you are content with this, let's go ahead with it...
                             n
    ...We'll launch as soon as we have the content...


    ...We're waiting for copy before the site can go live...
    ...If you are content with this, let's go ahead with it...
    ...We'll launch as soon as we have the content...
                                                                                   .

