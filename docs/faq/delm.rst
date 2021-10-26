删除行尾的 ^M
####################################

在 Windows 操作系统下码的砖，传到 Linux 系统后，用 vim 打开时会出 ``^M`` 结尾符，这是因为：在 DOS/Windows 系统中文本文件的换行符为 ``\r\n`` ，而在 Linux 系统中文本文件的换行符则为 ``\n`` ，所以 DOS/Windows 系统中编辑过的文本文件到了 Linux 系统中，每一行都多了个 ``^M`` 。

.. note::

    在 vim 中，可以使用 ``:set ff?`` 查看当前文件的换行符模式，如果显示 ``fileforma=dos`` 表示是 DOS/Windows 系统，可以使用 ``:set fileformat=unix`` 转化为 Linux 系统，保存后在传到 Linux 系统中。


使用替换模式删除
************************************

1. 使用替换模式删除：

.. highlight:: none

::

    :%s/\r//g

2. 使用替换模式删除 ^M：

::

    :%s/^M//g

.. attention::

    替换命令中的 ``^M`` 时需要使用 <Ctrl+V> 和 <Ctrl+M> 来输入。
