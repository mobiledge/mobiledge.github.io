[mobilege](/README.md) 
/ [Vim](/vim.md)
    <sub>&nbsp;&nbsp;Documentation</sub>
    <sub>&nbsp;&nbsp;[tldr](https://tldr.inbrowser.app/pages/common/vim)</sub>


# vim

`vim file.txt`

- starts off in Command Mode
- `i` Command Mode -> Insert Mode
- `Esc` Insert Mode -> Command Mode
- `v` Command Mode -> Visual Mode -> Command Mode


###### Command Mode (Esc) - Cut/Copy/Paste
`dd` delete line\
`5dd` delete 5 lines

`yy` yank (copy) line\
`5yy` yank (copy) 5 lines

`p` paste line below\
`P` paste line above

###### Command Mode (Esc) - Navigation
`gg` go to first line\
`5gg` go to line 5\
`G` go to last line

`0` go to beginning of line\
`$` go to end of line

###### Extended Command Mode (:)
`:wq` save & exit\
`:q!` exit without save