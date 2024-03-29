配置按键映射
####################################

Vim 强大的一个重要原因是它的高度可配置性。你可以自定义各种快捷键，让它用起来更符合自己的使用习惯从而更得心应手。

vim 里最基本的映射配置有 map、noremap、unmap、mapclear 几种。

:map: 递归的映射

:noremap: 非递归的映射

:unmap: 删除某个映射

:mapclear: 清除某个映射

同 Vim 下的其他命令一样，map 命令的名字往往由好几段组成。在不同的模式下，同一组按键可以被映射到不同的组合上，前缀作为命令本身的修饰符，微调命令的效果。map 有以下几种前缀：

:n: 在普通模式下生效

:v: 在可视模式下生效

:i: 在插入模式下生效

:c: 在命令行模式下生效


递归和非递归的映射
************************************

递归的映射其实很好理解，也就是如果键 a 被映射成了 b，c 又被映射成了 a，如果映射是递归的，那么 c 就被映射成了 b。

.. highlight:: none

::

    :map a b
    :map c a

对于 c 效果等同于：

::

    :map c b

默认的 map 就是递归的。如果遇到 nore 这种前缀，比如 :noremap，就表示这种 map 是非递归的。


命令模式下的实例
************************************

新建一个 mapping，将 b 映射成 a。在普通模式下，按下 b，会进入插入模式：

::

    :nmap b a

新建一个 mapping，赶紧进入插入模式，输入 bug 这个单词吧！

::

    :imap b a

注意如果向上边那样，按 b 输入的确是 a，那么恭喜，你已经把 vim 的按键弄得乱七八糟了，试着用 unmap 和 mapclear 清除这些 mapping 吧。


写入配置文件
************************************

把常用的快捷键操作写入 ``.vimrc`` 中，使其永久生效是个不错的主意,这样每次打开 vim 就会自动准备好。一般自定义的快捷键映射都使用非递归的方式。下边的快捷键定义在普通模式下按 Ctrl 和相应的上下左右键，跳转到分割的屏幕上。

::

    "split navigations
    nnoremap <C-J> <C-W><C-J>
    nnoremap <C-K> <C-W><C-K>
    nnoremap <C-H> <C-W><C-H>
    nnoremap <C-L> <C-W><C-L>


阅读更多
************************************

VIM 键映射 http://vimcdoc.sourceforge.net/doc/map.html#:imap
