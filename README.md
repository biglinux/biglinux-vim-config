

# ⚙️ Vim Configuration  

**A custom setup for enhanced coding productivity**  
*Configuração personalizada para produtividade em programação*  

---

## ✨ Features / Funcionalidades  

### 🔍 Search & Encoding  
- `hlsearch`: Highlight all matches / Destacar resultados  
- `ignorecase`: Case-insensitive search / Ignorar maiúsculas  
- `noincsearch`: Disable incremental search / Busca não incremental  
- `encoding=utf8`: UTF-8 compatibility / Codificação UTF-8  
- `laststatus=2`: Always show status line / Barra de status fixa  

### 🖱️ Mouse & Interface  
- `mouse=v`: Mouse in visual mode / Mouse no modo visual  
- `cursorline`: Highlight cursor line / Destacar linha do cursor  
- `codedark`: Modern dark theme / Tema escuro moderno  

### 📐 Smart Indentation  
- **HTML**: 2 spaces / 2 espaços  
- **Python**: 4 spaces (PEP8) / 4 espaços  
- **YAML**: 2 spaces + custom rules / 2 espaços + regras personalizadas  

### ⚡ Automation  
- Auto-exit Insert mode / Sai do modo Inserção automaticamente  
- Filetype-specific settings / Configurações por tipo de arquivo  

---

## 🚀 Installation / Instalação  
```bash  
git clone https://github.com/your-user/vim-config.git  
cp vim-config/.vimrc ~/.vimrc  
```  
*(Optional/Opcional)* Install theme:  
```vim  
Plug 'tomasiser/vim-code-dark'  " Via plugin manager  
```

---

## ⚙️ Configuration Details  
```vim  
" === Core Settings ===  
syntax on  
filetype plugin indent on  " Syntax + filetype detection  

" 🔍 Search/Encoding  
set noincsearch ignorecase  
set encoding=utf8 hlsearch  
set showmatch cursorline  

" 🎨 Interface  
colorscheme codedark  
set laststatus=2 nocompatible  

" 🖱️ Mouse  
if has("mouse")  
    set mouse=v  " Visual mode only  
endif  

" 📐 Indentation Rules  
function! HtmlConfig()  
    set tabstop=2 softtabstop=2 expandtab shiftwidth=2  
endfunction  

autocmd FileType html call HtmlConfig()  
autocmd FileType python call PythonConfig()  
autocmd FileType yaml,yml call YamlConfig()  

" 📊 Status Line  
set statusline=\ File:\ %F%m%r%h\ %w\ Dir:\ %{getcwd()}\ -\ Line:\ %l\ Col:\ %c  

" 🛡️ Prevent Overrides  
let g:skip_defaults_vim = 1  
```  

---

## 🇧🇷 Versão em Português  
<details>  
<summary>Clique para expandir</summary>  

### ✨ Funcionalidades  
- **🔍 Busca e Codificação**  
  - Destaque de resultados (`hlsearch`)  
  - Busca case-insensitive (`ignorecase`)  
  - Codificação UTF-8 garantida  

- **🖱 Interface**  
  - Suporte a mouse no modo visual  
  - Tema `codedark` para melhor visibilidade  

- **📐 Indentação Inteligente**  
  - Configurações específicas para HTML/Python/YAML  

### ⚙️ Detalhes Técnicos  
```vim  
" === Autocomandos ===  
autocmd CursorHoldI * stopinsert  " Sai do modo inserção após inatividade  

function! YamlConfig()  
    set tabstop=2 softtabstop=2  
    set indentkeys-=0#  " Ignora # em YAML  
endfunction  
```  

</details>  

---

## 📜 License / Licença  
MIT License - Free to use and modify.  
