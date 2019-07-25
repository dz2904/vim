Vim 配置文件
#############################

首先，安装 Vundle 插件管理器 ``git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim`` 。
然后，将配置文件复制到 ``～/.vimrc`` 中。
最后，打开 vim 键入 ``:PluginInstall`` 命令安装所以插件。

要求：

- vim 8.0 及以上版本
- git 支持
- vim python3 支持

.. note::
    
    Powerline 需要参考官方文档安装插件及字体， `参考链接 <https://powerline.readthedocs.io/en/latest/installation/linux.html>`_ 。
    在 Debian 10 环境中，配置文件直接放入 /etc/fonts/conf.d/ 目录下。

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
    syntax enable
    set scrolloff=3
    " set cursorline
    
    highlight BadWhitespace ctermbg=red guibg=darkred
    au BufRead,BufNewFile *.py,*.pyw,*.c,*.h match BadWhitespace /\s\+$/
    
    au BufNewfile,BufRead *.py
    \ set tabstop=4 |
    \ set shiftwidth=4 |
    \ set expandtab |
    \ set textwidth=79 |
    \ set fileformat=unix
    
    au BufNewfile,BufRead *.js, *.html, *.css, *.htm
    \ set tabstop=2 |
    \ set shiftwidth=2 |
    \ set expandtab
    
    Plugin 'scrooloose/nerdtree'
    autocmd vimenter * NERDTree
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif
    map <C-f> :NERDTreeToggle<CR>
    let NERDTreeWinPos='left'
    let NERDTreeWinSize=25
    
    "split navigations
    nnoremap <C-J> <C-W><C-J>
    nnoremap <C-K> <C-W><C-K>
    nnoremap <C-L> <C-W><C-L>
    nnoremap <C-H> <C-W><C-H>
    
    Plugin 'maralla/completor.vim'
    let g:completor_python_binary = '/path/to/python/with/jedi/installed'
    
    " Plugin 'Lokaltog/powerline'
    set rtp+=/home/xiao/.local/lib/python3.7/site-packages/powerline/bindings/vim/
    set laststatus=2
    set noshowmode
    set t_Co=256

