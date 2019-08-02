NERDTree 文件资源管理器
########################

NERDTree 是 Vim 编辑器的文件系统资源管理器。使用此插件，用户可以直观地浏览复杂的目录层次结构，快速打开文件以进行读取或编辑，以及执行基本的文件系统操作。

.. image:: ../images/nerdtree01.png

用 Vundle 插件管理器快速安装 NERDTree 文件系统资源管理器插件：

.. highlight:: none

::

    Plugin 'scrooloose/nerdtree'

Vundle 安装插件的详细方法请参考 `链接 <vundle.html#id6>`_ 。

快速配置
************************

::

    Plugin 'scrooloose/nerdtree'
    
    " 启动 vim 时自动打开 NERDTree
    autocmd vimenter * NERDTree
    
    " 只剩 NERDTree 窗口时关闭 vim
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

    " 开启/关闭 NERDTree 快捷键
    nnoremap <C-T> :NERDTreeToggle<CR>

    " 不显示 .pyc 文件
    let NERDTreeIgnore = ['\.pyc$']
    
    " 定义窗口位置及窗口大小
    let NERDTreeWinPos='left'
    let NERDTreeWinSize=25
    
    " 定义切换窗口的快捷键
    nnoremap <C-J> <C-W><C-J>
    nnoremap <C-K> <C-W><C-K>
    nnoremap <C-L> <C-W><C-L>
    nnoremap <C-H> <C-W><C-H>


操作命令
************************

=======   ==============
键          说明
=======   ==============
o           打开文件，目录和书签
go          打开所选文件，但将光标留在 NERDTree 中，在当前 NERDTree 中打开所选书签目录
t           在新选项卡中打开选定的节点/书签
T           与't'相同，但将焦点保持在当前选项卡上
i           在拆分窗口中打开所选文件
gi          与i相同，但将光标留在NERDTree上
s           在新的vsplit中打开所选文件
gs          与s相同，但将光标留在NERDTree上
<CR>        用户可定义的自定义打开操作
O           递归打开所选目录
x           关闭当前节点父节点
X           递归关闭当前节点的所有子节点
e           编辑当前目录

D           删除当前书签 

P           跳转到根节点
p           跳转到当前节点parent
K           在当前树深度的内部目录中跳转
J           在当前树深度的内部目录中跳转
<C-J>       跳转到当前目录的下一个兄弟
<C-K>       跳转到当前目录的上一个兄弟

C           将树根更改为选定的目录
u           将树根向上移动一个目录
U           与'u'相同，但旧的根节点保持打开状态
r           递归刷新当前目录
R           递归刷新当前根
m           显示 NERDTree 菜单
cd          将CWD更改为所选节点的目录
CD          将树根更改为CWD

I           切换是否显示隐藏文件
f           切换是否使用文件过滤器
F           切换是否显示文件
B           切换是否显示书签表

q           关闭NERDTree窗口
A           缩放（最大化/最小化）NERDTree窗口
?           切换快速帮助的显示
=======   ==============
