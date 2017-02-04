---
layout: post
title:  Vim fugitive (git wrapper)
date:   2016-02-09 00:00:00
author: pratz
permalink: /vim-fugitive-cheat-sheet
description: Vim plugin fugitive to effective manage git
categories:
    - editor
tags:
    - git
    - vim
    - fugitive
---

#### Quick start guide to use vim fugitive:

- `Glog` if current file is opened then show logs for it else show all commit logs.
- `Gstatus` gives the status.
- `Gcommit` commit the changes (Note: first you need to stage them, do this with "-").
- `Gwrite` writes current file to index i.e to staging area.
- `Gread` reverts back the current file to the latest commit state.
- `Gremove` removes the current file.
- `Gmove <target_path>` moves the current file to the given target_path
- `Gblame` shows the blame line by line


#### Browse git objects:

- `Gedit <branch_name:file_path>` shows the file on specified branch_name.
- `Gedit <commit_id>` shows the specified commit


#### Exploring git history:

- `Gedit` shows the current file in current state.
- `Glog -10` shows only latest 10 logs.
- `Glog --` shows all commits in quick fix list.
- `Glog -- %` shows all commits only where current file is included.
- `Glog --grep=findme --` search for ‘findme’ in all ancestral commit messages
- `Glog --grep=findme -- %` search for ‘findme’ in all ancestral commit messages that touch the currently active file
- `Ggrep <search_string> (branch|commitid)` search for the search_string and shows in quick fix list.


#### Quick fix:

- `copen` open quick fix window
- `cnext` next quick fix window
- `cprev` next quick fix window
- `cfirst` first quick fix window
- `clast` last quick fix window


### Notes:
- When a commit is displayed, you can hit "enter" to get tree, blob, commits etc.
