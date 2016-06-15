execute pathogen#infect()
syntax on
" filetype plugin indent on

set nocompatible " be iMproved, required  
filetype off " required

" Some settings to enable the theme:
set number
syntax enable
set background=dark
set nobackup
let g:solarized_termcolors = 256  " New line!!
colorscheme monokai
"color solarized
"colorscheme gruvbox
hi Normal ctermfg=252 ctermbg=none


let mapleader      = ","
let maplocalleader = "z"

" Open NERDTree in the directory of the current file (or /home if no file is
" open)
nmap <silent> <leader>n :call NERDTreeToggleInCurDir()<cr>
function! NERDTreeToggleInCurDir()
    " If NERDTree is open in the current buffer
    if (exists("t:NERDTreeBufName") && bufwinnr(t:NERDTreeBufName) != -1)
        exe ":NERDTreeClose"
    else
        exe ":NERDTreeFind"
    endif
endfunction

"nnoremap <S-Tab> <<
"nnoremap <Tab> >>
" inoremap <S-Tab> <C-d>
map <Tab> >
map <S-Tab> <

map <C-a> ggVG
map m %
map w :w!<CR>
map q :q!<CR>
map W :Gwrite<CR>
map C :Gcommit -m "commit"<CR>
map P :Gpush origin master<CR>
map <LocalLeader>[ 5<C-w>-<Esc>
map <LocalLeader>] 5<C-w>+<Esc>
map <LocalLeader>; :vertical resize +1<CR><CR>
map <LocalLeader>' :vertical resize -1<CR><CR>
map <LocalLeader>w :Hupload<CR>
map <LocalLeader>d :Hdownload<CR>
map <C-h> <C-w>h
map <C-j> <C-w>j
map <C-k> <C-w>k
map <C-l> <C-w>l
map T :tabnext<CR>
map t :tabprevious<CR>
map Y "+y<CR>
map <Leader>a :Tabularize /=<CR>
map <Leader>b :Tabularize /:\zs<CR>
map <C-f> :Ag 
" will run esformatter after pressing <leader> followed by the 'e' and 's'
" keys
nnoremap <silent> <leader>es :Esformatter<CR>
vnoremap <silent> <leader>es :EsformatterVisual<CR>


"NERDTree
"autocmd VimEnter * NERDTreeFind | wincmd p
"autocmd BufWinEnter * NERDTreeMirror

"Powerline
source /usr/local/lib/python2.7/site-packages/powerline/bindings/vim/plugin/powerline.vim

" These lines setup the environment to show graphics and colors correctly.
set nocompatible
set t_Co=256
 
let g:minBufExplForceSyntaxEnable = 1
python from powerline.vim import setup as powerline_setup
python powerline_setup()
python del powerline_setup
 
if ! has('gui_running')
   set ttimeoutlen=10
   augroup FastEscape
      autocmd!
      au InsertEnter * set timeoutlen=0
      au InsertLeave * set timeoutlen=1000
   augroup END
endif
 
set laststatus=2 " Always display the statusline in all windows
set guifont=Inconsolata\ for\ Powerline:h14
set noshowmode " Hide the default mode text (e.g. -- INSERT -- below the statusline)

" set laststatus=2
" set guifont=Inconsolata\ for\ Powerline:h15
let g:Powerline_symbols = 'fancy'
" set encoding=utf-8
" set t_Co=256
set fillchars+=stl:\ ,stlnc:\
set term=xterm-256color
set termencoding=utf-8
" if has("gui_running")
" 	let s:uname = system("uname")
" 	if s:uname == "Darwin\n"
" 		set guifont=Inconsolata\ for\ Powerline:h15
" 	endif
" endif

"Javascript Syntax
let g:javascript_conceal_function   = "ƒ"
let g:javascript_conceal_null       = "ø"
let g:javascript_conceal_this       = "@"
let g:javascript_conceal_return     = "⇚"
let g:javascript_conceal_undefined  = "¿"
let g:javascript_conceal_NaN        = "ℕ"
let g:javascript_conceal_prototype  = "¶"
let g:javascript_conceal_static     = "•"
let g:javascript_conceal_super      = "Ω"
let g:javascript_enable_domhtmlcss = 1

"Multiple Cursor
"Default mapping
let g:multi_cursor_next_key='<C-n>'
let g:multi_cursor_prev_key='<C-p>'
let g:multi_cursor_skip_key='<C-x>'
let g:multi_cursor_quit_key='<C-c>'
let g:multi_cursor_start_key='<C-n>'
let g:multi_cursor_start_word_key='g<C-n>'

"Easymotion
nmap S <Plug>(easymotion-s)
 "Bidirectional & within line 't' motion
omap t <Plug>(easymotion-bd-tl)
" Use uppercase target labels and type as a lower case
let g:EasyMotion_use_upper = 1
" type `l` and match `l`&`L`
let g:EasyMotion_smartcase = 1
" Smartsign (type `3` and match `3`&`#`)
let g:EasyMotion_use_smartsign_us = 1
"nmap f <Plug>(easymotion-s2)
" Gif config
map  / <Plug>(easymotion-sn)
omap / <Plug>(easymotion-tn)

" Without these mappings, `n` & `N` works fine. (These mappings just provide
" different highlight method and have some other features )
map  n <Plug>(easymotion-next)
map  N <Plug>(easymotion-previous)
" Gif config
map <LocalLeader>l <Plug>(easymotion-lineforward)
map <LocalLeader>j <Plug>(easymotion-j)
map <LocalLeader>k <Plug>(easymotion-k)
map <LocalLeader>h <Plug>(easymotion-linebackward)
imap <C-c> <Esc>
map <S-j> <Esc>

" Paste 
let &t_SI .= "\<Esc>[?2004h"
let &t_EI .= "\<Esc>[?2004l"

inoremap <special> <expr> <Esc>[200~ XTermPasteBegin()

function! XTermPasteBegin()
  set pastetoggle=<Esc>[201~
  set paste
  return ""
endfunction
" End Paste

"
let g:EasyMotion_startofline = 0 " keep cursor colum when JK motion
"
"Undotree
if has("persistent_undo")
    set undodir='~/.undodir/'
    set undofile
endif

map U :UndotreeToggle<CR>:UndotreeFocus<CR>

filetype plugin indent on
set tabstop=4
set shiftwidth=4
set expandtab

"Unicode
if has("multi_byte")
    if &termencoding == ""
        let &termencoding = &encoding
    endif
    set encoding=utf-8
    setglobal fileencoding=utf-8
    setglobal bomb
    set fileencodings=ucs-bom,utf-8,latin1
endif


"ctrlp
let g:ctrlp_map = '<c-p>'
let g:ctrlp_cmd = 'CtrlP'
let g:ctrlp_working_path_mode = 'ra'
set wildignore+=*/tmp/*,*.so,*.swp,*.zip,*.tar,*.jpg,*.png,*.jpeg     " MacOSX/Linux

let g:ctrlp_custom_ignore = '\v[\/]\.(git|hg|svn|tar|dmg)$'
let g:ctrlp_user_command = 'find %s -type f'        " MacOSX/Linux
let g:airline#extensions#tabline#enabled = 1
let g:airline#extensions#tabline#left_sep = ' '
let g:airline#extensions#tabline#left_alt_sep = '|'
let g:airline_powerline_fonts = 1

let g:mta_use_matchparen_group = 0
let g:mta_set_default_matchtag_color = 0
" highlight MatchTag ctermfg=black ctermbg=lightgreen guifg=black guibg=lightgreen
highlight MatchTag ctermfg=red guifg=red

let g:jsx_ext_required = 0

augroup reload_vimrc " {
    autocmd!
    autocmd BufWritePost $MYVIMRC source $MYVIMRC
augroup END " }"

set autoread
" check file change every 4 seconds ('CursorHold') and reload the buffer upon
" detecting change
" set autoread                                                                                                                                                                                    
" au CursorHold * checktime  
"
autocmd BufWritePost * :call SyncUploadFile()
autocmd BufReadPre * :call SyncDownloadFile()

" Track the engine.
"Plugin 'SirVer/ultisnips'

" Snippets are separated from the engine. Add this if you want them:
"Plugin 'honza/vim-snippets'

" Trigger configuration. Do not use <tab> if you use https://github.com/Valloric/YouCompleteMe.
let g:UltiSnipsExpandTrigger="<tab>"
let g:UltiSnipsJumpForwardTrigger="<c-b>"
let g:UltiSnipsJumpBackwardTrigger="<c-z>"

" If you want :UltiSnipsEdit to split your window.
let g:UltiSnipsEditSplit="vertical"

" Vim Javascript
let g:javascript_enable_domhtmlcss = 1
let g:javascript_ignore_javaScriptdoc = 1

" Vim CSS3 Syntax
augroup VimCSS3Syntax
    autocmd!

    autocmd FileType css setlocal iskeyword+=-
augroup END
":highlight VendorPrefix guifg=#00ffff gui=bold
":match VendorPrefix /-\(moz\|webkit\|o\|ms\)-[a-zA-Z-]\+/

"Auto Read
set autoread
augroup checktime
    au!
    if !has("gui_running")
        "silent! necessary otherwise throws errors when using command
        "line window.
        autocmd BufEnter        * silent! checktime
        autocmd CursorHold      * silent! checktime
        autocmd CursorHoldI     * silent! checktime
        "these two _may_ slow things down. Remove if they do.
        autocmd CursorMoved     * silent! checktime
        autocmd CursorMovedI    * silent! checktime
    endif
augroup END

"Vim AG
let g:ag_working_path_mode="r"

"Library Javascript Syntax
let g:used_javascript_libs = 'underscore,angularjs,angularui,angularuirouter'
autocmd BufReadPre *.js let b:javascript_lib_use_jquery = 1
autocmd BufReadPre *.js let b:javascript_lib_use_underscore = 1
autocmd BufReadPre *.js let b:javascript_lib_use_backbone = 1
autocmd BufReadPre *.js let b:javascript_lib_use_angularjs = 1

"Emmet
let g:user_emmet_leader_key='<C-e>'
