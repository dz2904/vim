Vim 配置文件
#############################

同时安装 vim 和 gvim，vim 主要用于在终端中修改文件和编程，gvim 主要用于输入中文的文本编辑。

环境要求：

- vim 8.0 及以上版本
- vim python3 支持
- gvim 图形界面
- git 支持
- gnome 桌面和 ibus 输入法

首先，安装 Vundle 插件管理器 

.. highlight:: none

::

    git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim

然后，将配置文件复制到 ``～/.vimrc`` 中。

最后，打开 vim 键入 ``:PluginInstall`` 命令安装所以插件。

.. note::
    
    - :doc: `Powerline <../plugin/powerline.rst>`_ 需要安装合适的字体才能完美运行，建议使用 ``Source Code Pro for Powerline`` 字体
    - :doc: `completor.vim <../plugin/completor.rst>`_ 需要 jedi 支持
    - solarized 配色文件（solarized.vim）需要手动配置到系统目录


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
    
    set encoding=utf-8
    set number
    set autoindent
    set scrolloff=3
    " set cursorline
    syntax enable

    " search setting
    set hlsearch
    set incsearch

    highlight BadWhitespace ctermbg=red guibg=darkred
    au BufRead,BufNewFile *.py,*.pyw,*.c,*.h match BadWhitespace /\s\+$/


    Plugin 'scrooloose/nerdtree'
    " autocmd vimenter * NERDTree
    wincmd w
    autocmd VimEnter * wincmd w
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif
    nnoremap <C-T> :NERDTreeToggle<CR>
    let g:NERDTreeDirArrowExpandable = '+'
    let g:NERDTreeDirArrowCollapsible = '-'
    let NERDTreeWinPos='left'
    let NERDTreeWinSize=25

    "split navigations
    nnoremap <C-J> <C-W><C-J>
    nnoremap <C-K> <C-W><C-K>
    nnoremap <C-H> <C-W><C-H>
    nnoremap <C-L> <C-W><C-L>

    Plugin 'maralla/completor.vim'
    let g:completor_python_binary = '/path/to/python/with/jedi/installed'

    " 显示状态栏
    set laststatus=2
    set noshowmode

    Plugin 'tmhedberg/SimpylFold'
    set foldmethod=indent
    set foldlevel=99
    nnoremap <space> za
    let g:SimpylFold_docstring_preview=1

    Plugin 'Vimjas/vim-python-pep8-indent'
    Bundle 'altercation/vim-colors-solarized'

    " 使用 fcitx5 输入法自动切换中英文输入
    " autocmd InsertLeave * :silent !fcitx5-remote -c
    " autocmd InsertEnter * :silent !fcitx5-remote -o

    " 禁用响铃
    set vb t_vb=

    if(has("gui_running"))
        set guifont=CamingoCode\ 16
        colorscheme solarized
        " 打开文件时修改默认路径为文件所在路径
        exec 'cd' '%:p:h'
        " 自动切换中英文输入法
        autocmd GUIEnter * :silent !ibus engine xkb:us::eng
        autocmd InsertLeave * :silent !ibus engine xkb:us::eng
        autocmd InsertEnter * :silent !ibus engine libpinyin
        autocmd VimLeave * :silent !ibus engine libpinyin
        " 复制粘贴
        nnoremap <C-V> "+p
        vnoremap <C-C> "+y
    else
        set guifont=CamingoCode\ 16
        " Powerline
        set  rtp+=~/.local/lib/python3.9/site-packages/powerline/bindings/vim/
        au BufNewfile,BufRead *.py,*.pyw,*.rst
        \ set tabstop=4 |
        \ set shiftwidth=4 |
        \ set expandtab |
        \ set textwidth=79 |
        \ set fileformat=unix
        
        au BufNewfile,BufRead *.js,*.html,*.css,*.htm
        \ set tabstop=2 |
        \ set shiftwidth=2 |
        \ set expandtab
    endif
