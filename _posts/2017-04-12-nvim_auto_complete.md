---
layout: post
title:  NVim auto complete
date:   2017-04-12 00:00:00
author: pratz
permalink: /nvim-auto-complete
description: Neovim auto complete
categories:
    - neovim-as-ide
tags:
    - nvim
    - deoplete
---

#### Intro:
Initially I used [YouCompleteMe](https://github.com/Valloric/YouCompleteMe) and [Neocomplete](https://github.com/Shougo/neocomplete.vim) for auto-completion with Vim. But then I made a move from [Vim](http://www.vim.org/) to [Neovim](https://neovim.io/). While browsing I stumbled upon [Deoplete](https://github.com/Shougo/deoplete.nvim), an auto-complete for Neovim and boy!! I was surprised by its performance. Actually, Neocomplete and Deoplete are created by the same author, first for Vim and later for Neovim. I must say, Deoplete leverages Neovim's async feature very well to provide an excellent performance.

Deoplete is a general asynchronous auto-completion framework, however, it provides language specific auto-completion through different sources. Two of which, for [Python](https://github.com/zchee/deoplete-jedi) and [Go](https://github.com/zchee/deoplete-go), are shown below, as those are the once which I use.

#### Deoplete in action:
<img src="./assets/posts/nvim_as_ide/deoplete.gif" alt="Deoplete" title="Deoplete">

#### Deoplete [python source](https://github.com/zchee/deoplete-jedi):
<img src="./assets/posts/nvim_as_ide/deoplete_python.gif" alt="Deoplete python" title="Deoplete python">

#### Deoplete [go source](https://github.com/zchee/deoplete-go):
<img src="./assets/posts/nvim_as_ide/deoplete_go.gif" alt="Deoplete go" title="Deoplete go">

#### Deoplete settings:
- Below are few Deoplete settings that I use

        let g:deoplete#enable_at_startup = 1
        let g:deoplete#enable_ignore_case = 1
        let g:deoplete#sources#go = 'vim-go'
        let g:deoplete#sources#python = 'jedi-vim'
