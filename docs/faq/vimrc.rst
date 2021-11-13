Vim 配置文件
#############################

环境要求：

- vim 8.0 及以上版本
- vim python3 支持
- git 支持
- gnome 桌面和 ibus 输入法

首先，安装 Vundle 插件管理器

.. highlight:: none

::

    git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim

然后，将配置文件复制到 ``～/.vimrc`` 中。

最后，打开 vim 键入 ``:PluginInstall`` 命令安装所以插件。

.. note::

    - :doc:`Powerline <../plugin/powerline>`_ 需要安装合适的字体才能完美运行，建议使用 ``Source Code Pro for Powerline`` 字体
    - :doc:`completor.vim <../plugin/completor>`_ 需要 jedi 支持
    - solarized 配色文件（solarized.vim）需要手动配置到系统目录
    - 输入法自动切换添加的文件格式脚本中，最实用


基本配置文件
*****************************

.. highlight:: none

::

    set nocompatible              " be iMproved, required
    filetype off                  " required

    " set the runtime path to include Vundle and initialize
    set rtp+=~/.vim/bundle/Vundle.vim
    call vundle#begin()
    " alternatively, pass a path where Vundle should install plugins
    "call vundle#begin('~/some/path/here')

    " let Vundle manage Vundle, required
    Plugin 'VundleVim/Vundle.vim'

    " The following are examples of different formats supported.
    " Keep Plugin commands between vundle#begin/end.
    " plugin on GitHub repo
    Plugin 'tpope/vim-fugitive'
    " plugin from http://vim-scripts.org/vim/scripts.html
    " Plugin 'L9'
    " Git plugin not hosted on GitHub
    Plugin 'git://git.wincent.com/command-t.git'
    " git repos on your local machine (i.e. when working on your own plugin)
    " Plugin 'file:///home/gmarik/path/to/plugin'
    " The sparkup vim script is in a subdirectory of this repo called vim.
    " Pass the path to set the runtimepath properly.
    Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
    " Install L9 and avoid a Naming conflict if you've already installed a
    " different version somewhere else.
    " Plugin 'ascenator/L9', {'name': 'newL9'}

    " All of your Plugins must be added before the following line
    call vundle#end()            " required
    filetype plugin indent on    " required
    " To ignore plugin indent changes, instead use:
    "filetype plugin on
    "
    " Brief help
    " :PluginList       - lists configured plugins
    " :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
    " :PluginSearch foo - searches for foo; append `!` to refresh local cache
    " :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
    "
    " see :h vundle for more details or wiki for FAQ
    " Put your non-Plugin stuff after this line

    " 基本设置
    set encoding=utf-8
    set number
    set autoindent
    set scrolloff=3
    " set cursorline
    syntax enable
    " 禁用响铃
    set vb t_vb=
    " TAB 替换为空格
    :set expandtab
    :%retab!
    " search setting
    set hlsearch
    set incsearch

    " 高亮不必要的空白字符
    highlight BadWhitespace ctermbg=red guibg=darkred
    au BufRead,BufNewFile *.py,*.pyw,*.rst,*.c,*.h match BadWhitespace /\s\+$/

    " 文件浏览插件
    Plugin 'scrooloose/nerdtree'
    " autocmd vimenter * NERDTree
    wincmd w
    autocmd VimEnter * wincmd w
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif
    nnoremap <C-T> :NERDTreeToggle<CR>
    let g:NERDTreeDirArrowExpandable = '+'
    let g:NERDTreeDirArrowCollapsible = '-'
    let NERDTreeWinPos='left'
    let NERDTreeWinSize=20

    " 重新定义窗口跳转快捷键
    nnoremap <C-J> <C-W><C-J>
    nnoremap <C-K> <C-W><C-K>
    nnoremap <C-H> <C-W><C-H>
    nnoremap <C-L> <C-W><C-L>

    " 代码自动补全插件
    Plugin 'maralla/completor.vim'
    let g:completor_python_binary = '/path/to/python/with/jedi/installed'

    " python 代码格式化
    Plugin 'Vimjas/vim-python-pep8-indent'
    au BufNewFile,BufRead *.py  set textwidth=79
    au BufNewFile,BufRead *.js, *.html, *.css
    \ set tabstop=2 |
    \ set softtabstop=2 |
    \ set shiftwidth=2

    " 代码折叠插件及设置
    Plugin 'tmhedberg/SimpylFold'
    set foldmethod=indent
    set foldlevel=99
    nnoremap <space> za
    let g:SimpylFold_docstring_preview=1

    " 显示状态栏
    set laststatus=2
    set noshowmode

    " Powerline 状态栏美化
    Plugin 'Lokaltog/powerline', {'rtp': 'powerline/bindings/vim/'}
    set  rtp+=~/.local/lib/python3.9/site-packages/powerline/bindings/vim/


    " 打开文件时修改默认路径为文件所在路径
    " exec 'cd' '%:p:h'
    "
    " 使用 fcitx5 输入法自动切换中英文输入
    " autocmd InsertLeave * :silent !fcitx5-remote -c
    " autocmd InsertEnter * :silent !fcitx5-remote -o
    "
    " 使用 ibus 输入法自动切换中英文输入法
    " autocmd GUIEnter * :silent !ibus engine xkb:us::eng
    " autocmd InsertLeave * :silent !ibus engine xkb:us::eng
    " autocmd InsertEnter * :silent !ibus engine libpinyin
    " autocmd VimLeave * :silent !ibus engine libpinyin
