# Vim Configuration

This repository contains a custom Vim configuration designed to enhance usability, provide flexible indentation settings for various file types, and improve the overall coding experience.

## Features

- **Search and Encoding**:
  - Highlights all matches in search results.
  - Ignores case in search patterns (`ignorecase`).
  - Sets file encoding to UTF-8.
  - Disables incremental search (`noincsearch`).

- **Mouse Support**:
  - Enables mouse functionality if available.

- **Filetype-Specific Indentation**:
  - HTML: 2 spaces for tabs and indentation.
  - Python: 4 spaces for tabs and indentation.
  - YAML: 2 spaces for tabs and indentation with custom indent keys.

- **Autocommands**:
  - Exits Insert mode if idle for a defined period.
  - Automatically applies filetype-specific indentation.

- **Status Line**:
  - Displays file information, working directory, and cursor position.

## Configuration Details

```vim
syntax on
filetype plugin indent on

" Search and encoding settings
set noincsearch                        " Disables incremental search
set ignorecase                         " Ignores case in search patterns
set encoding=utf8                      " Sets file encoding to UTF-8
set laststatus=2                       " Always display the status line
set hlsearch                           " Highlights all matches in search results
set showmatch                          " Highlights matching parenthesis/brackets

" Mouse support
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

" Status line
set statusline=\ File:\ %F%m%r%h\ %w\ \ Working\ Directory:\ %r%{getcwd()}%h\ -\ Line:\ %l\ -\ Column:\ %c

" Prevent defaults.vim from overwriting these settings
let g:skip_defaults_vim = 1
