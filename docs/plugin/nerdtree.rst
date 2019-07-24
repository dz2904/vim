NERDTree 文件资源管理器
########################

NERDTree 是 Vim 编辑器的文件系统资源管理器。使用此插件，用户可以直观地浏览复杂的目录层次结构，快速打开文件以进行读取或编辑，以及执行基本的文件系统操作。

.. image:: ../images/nerdtree01.png

用 Vundle 插件管理器快速安装 NERDTree 文件系统资源管理器插件：

::

    Plugin 'scrooloose/nerdtree'

Vundle 安装插件的详细方法请参考 `链接 <./vundle.rst>`_ 。

快速配置
************************

.. highlight:: none

::

    " 启动 vim 时自动打开 NERDTree
    autocmd vimenter * NERDTree

    " 只剩 NERDTree 窗口时关闭 vim
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

    " 开启/关闭 NERDTree 快捷键
    map <C-f> :NERDTreeToggle<CR>

    " 不显示 .pyc 文件
    let NERDTreeIgnore = ['\.pyc$']
    
    " 定义窗口位置及窗口大小
    let NERDTreeWinPos='right'
    let NERDTreeWinSize=30
