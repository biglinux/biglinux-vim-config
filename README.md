# Vim Configuration

This repository contains a custom Vim configuration designed to enhance usability, provide flexible indentation settings for various file types, and improve the overall coding experience.

## Features

- **Search and Encoding**:
  - Highlights all matches in search results (`hlsearch`).
  - Ignores case in search patterns (`ignorecase`).
  - Disables incremental search, highlighting matches only after pressing Enter (`noincsearch`).
  - Sets file encoding to UTF-8 (`encoding=utf8`).
  - Always displays the status line at the bottom of the screen (`laststatus=2`).

- **Mouse Support**:
  - Enables mouse functionality in visual mode (`set mouse=v`), if supported.

- **Cursor Highlighting**:
  - Highlights the entire line where the cursor is positioned for better focus (`cursorline`).

- **Vi Compatibility**:
  - Ensures Vim is not in compatibility mode with Vi, enabling modern features (`nocompatible`).

- **Color Scheme**:
  - Sets the color scheme to `codedark` for a modern look.

- **Filetype-Specific Indentation**:
  - **HTML**: 2 spaces for tabs and indentation.
  - **Python**: 4 spaces for tabs and indentation.
  - **YAML**: 2 spaces for tabs and indentation with custom indent keys.

- **Autocommands**:
  - Exits Insert mode automatically if idle for a defined period (`CursorHoldI`).
  - Applies filetype-specific indentation settings when opening files.

- **Status Line**:
  - Displays detailed information, including file name, working directory, cursor position, and more.

## Configuration Details

```vim
syntax on
filetype plugin indent on

" Search and encoding settings
set noincsearch                        " Disables incremental search; highlights only on Enter
set ignorecase                         " Ignores case in search patterns for easier matching
set encoding=utf8                      " Sets file encoding to UTF-8 for better compatibility
set laststatus=2                       " Always displays the status line at the bottom of the screen
set hlsearch                           " Highlights all matches for search results to improve visibility
set showmatch                          " Briefly highlights matching parentheses, brackets, or braces
set cursorline                         " Highlights the entire line where the cursor is positioned for better focus
set nocompatible                       " Ensures Vim is not in Vi mode

" Color Scheme
colorscheme codedark

" Enables mouse support if available
if has("mouse")
    set mouse=v                        " Enables mouse support in visual mode
endif

" Filetype-specific indentation
function HtmlConfig()
    set tabstop=2 softtabstop=2 expandtab shiftwidth=2
endfunction

function PythonConfig()
    set tabstop=4 softtabstop=4 expandtab shiftwidth=4
endfunction

function YamlConfig()
    set tabstop=2 softtabstop=2 expandtab shiftwidth=2
    set indentkeys-=0# indentkeys-=<:>
endfunction

" Autocommands
autocmd CursorHoldI * stopinsert       " Exit Insert mode if idle
autocmd FileType html call HtmlConfig()
autocmd FileType python call PythonConfig()
autocmd FileType yaml,yml call YamlConfig()

" Status line configuration
set statusline=\ File:\ %F%m%r%h\ %w\ \ Working\ Directory:\ %r%{getcwd()}%h\ -\ Line:\ %l\ -\ Column:\ %c

" Prevent defaults.vim from overwriting these settings
let g:skip_defaults_vim = 1