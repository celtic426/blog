---
layout: post
title: "Blaze Through Commits with Git Aliases"
tags: [Git, command line, shortcuts, aliases]
---

When you're forced to stop and make a commit after reaching a milestone, sometimes using Git can feel like a crutch rather than a tool. If you sharpen your commit tool to the point where committing is a breeze, you can have more organized code with less chance of losing work.

## Save More than a Few Keystrokes

Here's an example of a quick commit with aliases for `git status`, `git add .`, and `git commit --message`.

<p align="center">
  <img src="https://i.imgur.com/2IyWwkF.png" alt="Git aliases example"/> <br>
  <i>Streamline your workflow to be faster and more productive.</i>
</p>

**Explanation**:
* `git status` becomes `gs`
* `git add .` becomes `gaa`
* `git commit -m` becomes `gcm`

**Other examples**:
* `git checkout -b` becomes `gcob`
* `git commit --amend --no-edit` becomes `gcane`
* `git log --oneline --decorate` becomes `gll`

You can also make shortcuts for any Git command or any other terminal command.

## How to Add Aliases

*Simply add the following to your .bashrc file.*

1. Navigate to your home directory `cd ~`.
2. Enter `ls -a` and you should see a file called `.bashrc`. (or `.bash_profile` if you don't have `.bashrc`)
3. Open the file with `open .bashrc` or `nano .bashrc`.
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
alias glo='git log --oneline --decorate'
alias gld='git log --pretty=format:"%h %ad %s" --date=short --all'
alias gs='git status'
alias gco='git checkout'
alias gcob='git checkout -b'
alias gd='git diff'
alias gds='git diff --staged'
alias gcane='git commit --amend --no-edit'
```

All new windows will have these aliases enabled. You can also run `. ~/.bashrc` in an existing window/tab to enable them.

## Bonus - Add Colors and Features

If you like to add more features and colors to terminal, check out [Bash-Git-Prompt](https://github.com/magicmonty/bash-git-prompt) which can be installed with Homebrew.

<p align="center">
  <img width="90%" src="https://i.imgur.com/6mFqjJJ.png"/> <br>
  <i>Example of Bash-Git-Prompt features</i>
</p>

### Additional Resources

* [Jon Suh - Git Command-Line Shortcuts](https://jonsuh.com/blog/git-command-line-shortcuts/)
* [Medium - Git on the Command Line — Improving the Experience](https://medium.com/ag-grid/git-on-the-command-line-improving-the-experience-5a604cb14cf6)
