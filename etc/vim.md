1. Install vim Vundle
```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

2. set vim Pugins..
```
set nocompatible
filetype off

set rtp+=~/.vim/bundle/Vundle.vim

call vundle#begin()

Plugin 'VundleVim/Vundle.vim'
Plugin 'scrooloose/nerdtree'
Plugin 'vim-airline/vim-airline'
Plugin 'airblade/vim-gitgutter'
Plugin 'tpope/vim-fugitive'
Plugin 'scrooloose/syntastic'
Plugin 'ctrlpvim/ctrlp.vim'
Plugin 'altercation/vim-colors-solarized'

call vundle#end()
filetype plugin indent on

" Syntax Highlighting
if has("syntax")
    syntax on
endif

" Auto dindent
set autoindent
set cindent

" Display Line
set nu

" Set color scheme
colorscheme solarized

" Set indent size
set ts=2
set shiftwidth=2

" Save last cursor
au BufReadPost *
\ if line("'\"") > 0 && line("'\"") <= line("$") |
\ exe "norm g`\"" |
\ endif

" ignore directory indexing (ctrlpvim/ctrlp.vim)
let g:ctrlp_custom_ignore = {
  \ 'dir':  '\.git$\|public$\|log$\|tmp$\|vendor$',
  \ 'file': '\v\.(exe|so|dll)$'
\ }

" Mapping nt -> :NERDTree
map <Leader>nt <ESC>:NERDTreeToggle<CR>

```
