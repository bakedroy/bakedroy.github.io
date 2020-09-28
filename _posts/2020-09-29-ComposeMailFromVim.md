---
layout: post
title: Compose Mail from Vim
date: 2020-09-29 00:40:00 +0900
---

I'm happy if I could compose an email from vim but not realistic. I'm currently using Thunderbird as the primary mail program, and he/she has a command-line interface. Thunderbird is a good mailer, and vim has a better editing environment. So I found that writing a draft in vim and transferring it to Thunderbird will give me an excellent experience.

The following code in vimscript is my option. It works well, but not perfect. It is just my first step.

```vimscript
function! ComposeMessage(cmdpat)
    let [l:qr, l:qt] = [getreg('"'), getregtype('"')] 
    silent norm! gvy
    let l:body = substitute(@", '\n', '\r\n', 'g')
    let l:bodyfile= 'Path-To-Temp-File'
    if writefile([l:body], l:bodyfile)
        echom 'Failed to write to a temp file.'
    else
        let l:cmd = printf(a:cmdpat, l:bodyfile)
        call setreg('"', l:qr, l:qt)
        echo system(l:cmd)
        if v:shell_error
            echol ErrorMsg | echom 'Failed to run ' . l:cmd | echol NONE
        endif
    endif
endfunction
vnoremap ,th :<c-u>call ComposeMessage('"Path-To-Thunderbird-Exe" -compose "format=2,message=%s"')<CR>
```

To transfer a composed message from vim's buffer to Thunderbird, just visually select the text and type `,th` (means THunderbird), then a composing window will appear with the body filled.

See also: (ib's answer in stackoverflow really helped me!)
- [Command line arguments - Thunderbird](http://kb.mozillazine.org/Command_line_arguments_(Thunderbird))
- [How to call external program from vim with visual marked text as param?](https://stackoverflow.com/questions/4192626/how-to-call-external-program-from-vim-with-visual-marked-text-as-param)
