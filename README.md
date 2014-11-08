report-with-gnome-terminal-vim-gnuplot-latex
============================================

Personal setup/conf used when I need to write reports with my Ubuntu boxes. Nothing very special, but saves me a lot of time by using: 
 - gnome-terminal tabs for separating between types of tasks
 - make for all compilation
 - gnuplot for all plotting
 - version control with git
 - cozy background picture in terminal (ok, not time saving but soul saving)

In .bashrc:

```bash
PATH=$PATH:/home/torbjorn/scripts/init-rapport
alias show='mupdf rap.pdf'
alias raptabs='gnome-terminal --tab --title "1 Vim Source" --tab --title "2 Generate/Collect data" --tab --title "3 Vim Gnuplot" --tab --title "4 Gnuplot" --tab --title "5 Vim rap.tex" --tab --title "6 make, git, mupdf"; exit'
```

In .vimrc:
```vim
" Make Vim get Alt- keybindings even when invoked in terminal
let c='a'
while c <= 'z'
  exec "set <A-".c.">=\e".c
  exec "imap \e".c." <A-".c.">"
  let c = nr2char(1+char2nr(c))
endw
set timeout ttimeoutlen=50

" Make yanking easier across instances of vim...
set clipboard=unnamedplus
" Save gnome-terminals titles...
set notitle
```
