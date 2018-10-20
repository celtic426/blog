---
layout: post
title: "Blaze Through Commits with Git Aliases"
tags: [Git, command line, shortcuts, aliases]
---

When you're forced to stop and make a commit after reaching a milestone, sometimes using Git can feel like a crutch rather than a tool. If you sharpen your commit tool to the point where committing is a breeze, you can have more organized code with less chance of losing work.

## Save More than a Few Keystrokes

The commit process I use involves an alias for these three git commands: `git status`, `git add .`, `git commit --message`.

<p align="center">
  <img src="https://i.imgur.com/2IyWwkF.png" alt="Git aliases example"/> <br>
  <i>Streamline your workflow to be faster and more productive.</i>
</p>

While this is an example for git commits, aliases allow you to make shortcuts for any command.

## How to Add Bash Aliases

*Simply add the following to your .bashrc file.*

1. Navigate to your home directory `cd ~`.
2. Enter `ls -a` and you should see a file called `.bashrc`.
3. Run `open .bashrc` (or `nano .bashrc` if you prefer the terminal).
4. Paste in the following, making changes as needed.

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

All new windows will have these aliases enabled. You can also run `. ~/.bashrc` in an existing window/tab to enable them.
