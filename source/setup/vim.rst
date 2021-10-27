============================================================
``Vim``
============================================================

Basic environment setup for Vim.

vimrc
=======

1. Dir navigation: NERDTree
2. Full text search: fzf


.. code-block:: bash

   call plug#begin('~/.vim/plugged')
   Plug 'scrooloose/nerdtree'
   Plug 'junegunn/fzf', { 'do': { -> fzf#install() } }
   Plug 'junegunn/fzf.vim'
   Plug 'python-mode/python-mode', { 'for': 'python', 'branch': 'develop' }
   call plug#end()

   filetype plugin indent on

   set paste
   set tabstop=2
   set shiftwidth=2
   set softtabstop=2
   set expandtab
   set encoding=utf8

   setlocal indentkeys+=0.

cheatsheet
==========

.. code-block:: bash

   :%s/pattern/to/g #replace
   v #visual mode
   y #yank
   p #paste
   :FZF fzf file search
   :Ag pattern #full text search
   :Rg pattern #full text search