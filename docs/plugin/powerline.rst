Powerline 状态栏美化
####################################

Powerline 是 vim、zsh、bash、tmux、IPython、Awesome、bar、fish、lemonbar、pdb、rc、shell、tcsh、wm、i3 和 Qtil 中的一个状态栏插件。它给程序提供了状态栏，并使程序更好看。

.. image:: ../images/powerline01.png

它用 Python 写成，非常轻便不需要任何第三方的依赖，只需要一个 Python 解释器。

最初该状态栏只在 vim 中可用，随后项目进化为许多 Linux 程序如 zsh、bash、tmux、IPython、Awesome、i3 和 Qtil 提供状态栏。

其配置以及配色方案用 JSON 写成。它是一种标准简易的文件格式，可以让用户配置 Powerline 支持的程序。


安装和配置
************************************


安装插件
====================================

在 Linux 系统上安装 Powerline 需要 Python 和 Git 支持（请自行安装）。然后在终端中输入以下命令：

.. highlight:: none

::

    pip install --user powerline-status

其他系统版本安装请参考 `官方文档 <https://powerline.readthedocs.io/en/latest/installation.html>`_ 。


安装字体
====================================

1. 下载符号字体和 fontconfig 文件：

::

    wget https://github.com/powerline/powerline/raw/develop/font/PowerlineSymbols.otf
    wget https://github.com/powerline/powerline/raw/develop/font/10-powerline-symbols.conf

2. 将符号字体移动到有效的字体路径。可以使用 ``xset q`` 列出有效的字体路径：

::

    mv PowerlineSymbols.otf ~/.local/share/fonts/

3. 更新字体移动到的路径的字体缓存（可能需要root权限来更新系统范围路径的缓存）：

::

    fc-cache -vf ~/.local/share/fonts/

4. 安装 fontconfig 文件。对于较新版本的 fontconfig，配置路径为 ``~/.config/fontconfig/conf.d/`` ，对于旧版本，它是 ``~/.fonts.conf.d/`` ：

::

    mv 10-powerline-symbols.conf ~/.config/fontconfig/conf.d/


.. hint:: 安装字体补丁

    在 Gnome 终端下安装完之后箭头显示乱码，让人非常郁闷。需要安装支持 Powerline 的 `字体 <https://github.com/powerline/fonts>`_ ，然后在终端中设置字体后显示正常。


配置
====================================

在 ``~/.vimrc`` 文件中加入配置信息（路径信息请根据自己的系统环境调整）：

::

    set  rtp+=~/.local/lib/python3.9/site-packages/powerline/bindings/vim/
    set laststatus=2
    set t_Co=256



