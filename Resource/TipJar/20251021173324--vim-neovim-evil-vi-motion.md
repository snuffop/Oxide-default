---
id: 20251021173324--vim-neovim-evil-vi-motion
aliases:
  - VIM Neovim Evil vi motion
tags:
  - resource
  - tipjar
date: Tuesday October 21st 2025
---
# VIM Neovim Evil vi motion

## VIM Neovim Evil vi motion Highlights

### Substitut all * for # at the beginning of the lines

``` vim
:%s/^\*\+/\=repeat('#', len(submatch(0)))/g
```

