---
layout: post
title: "Blaze Through Commits with Git Aliases"
tags: [Git, command line, shortcuts, aliases]
---

When you're forced to stop and make a commit after reaching a milestone, sometimes using Git can feel like a crutch rather than a tool. If you could sharpen your commit tool to the point where committing is a breeze, you could have more organized code with less chance of losing work.

This is a process I used on a project recently where I racked up 140 commits over a 4-day period:

1. You finish working on a feature
2. `gs` *Confirm the modified file is correct*
3. `gaa` *Stage your changes*
4. `gcm "Add center-text to table header in App.js"` *Commit and add a message*


You're not just saving a few keystrokes, you're streamlining your workflow to be faster and more productive. 

to add bash aliases for git commands.

location: ~/.bashrc
run after edit: . .bash_profile

1. Navigate to your home directory `cd ~`.
2. Enter `ls -a` and you should see a file called `.bashrc`.
3. Run `open .bashrc` (or `nano .bashrc` if you prefer the terminal).
4. Use the following template, making changes as needed.

```bash
#Aliases - general
alias c='clear'

# Alias - git
alias ga='git add'
alias gaa='git add .'
alias gb='git branch'
alias gc='git commit'
alias gcm='git commit --message'
alias gl='git log'
alias gll='git log --oneline --decorate'
alias gs='git status'
alias gco='git checkout'
alias gcob='git checkout -b'
alias gd='git diff'
alias gds='git diff --staged'
alias gcane='git commit --amend --no-edit'
```
