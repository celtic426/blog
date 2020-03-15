---
layout: post
title: 'VSCode Extensions for JavaScript Developers'
tags: [VSCode, Extensions, Productivity]
---

VSCode is the most popular code editor currently, thanks in part to its Marketplace for extensions. Most of the following list is universally applicable, with some specifically targeting Front End web development.

## Basics

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) - Standard linter for JavaScript and TypeScript

- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - Code formatter for JavaScript and TypeScript

- [Gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) - Adds git blame to lines/files. Highliy customizable with a settings editor UI

- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme) (or any icon theme) - Icon themes make files look more appealing

- [Atom Keybindings](https://marketplace.visualstudio.com/items?itemName=ms-vscode.atom-keybindings) - Adds useful keyboard shortcuts if coming from the Atom editor

## Importing & Intellisense

- [npm Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.npm-intellisense) - Autocomplete for NPM module import statements

- [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense) - Autocomplete for local import statements

- [SCSS Intellisense](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-scss) - Autocomplete and 'Go To' functionality for SCSS

- [Auto-import](https://marketplace.visualstudio.com/items?itemName=steoates.autoimport) - Auto-import TypeScript modules

- [Microsoft Intellicode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode) - Smarter Intellisense gives you more relevant suggestions

## Editor Enhancements

- [Reopen Closed Tab](https://marketplace.visualstudio.com/items?itemName=uyiosa-enabulele.reopenclosedtab) - Adds menu item and keyboard shortcut (Cmd + Shift + T) to reopen closed tabs

- [File Utils](https://marketplace.visualstudio.com/items?itemName=sleistner.vscode-fileutils) - Adds 'Duplicate File' functionality

- [Active File in Status Bar](https://marketplace.visualstudio.com/items?itemName=RoscoP.ActiveFileInStatusBar) - Shows the path of the current file in the status bar

- [Bracket Pair Colorizer 2](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer-2) - Matching brackets are identified with colors

- [Zoombar](https://marketplace.visualstudio.com/items?itemName=wraith13.zoombar-vscode) - Control the window's zoom level from the status bar and command pallette

- [Terminal Zoom](https://marketplace.visualstudio.com/items?itemName=trybick.terminal-zoom) - Control the terminal font size from the status bar and command pallette. I made this one :)

- [Alphabetical Sorter](https://marketplace.visualstudio.com/items?itemName=ue.alphabetical-sorter) - Sort lists alphabetically

## Specific Filetypes

- [Mardown Lint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) - Provides linting for Markdown files

- [Shell Format](https://marketplace.visualstudio.com/items?itemName=foxundermoon.shell-format) - Syntax highlighting and formatting to shell scripts, Docker files, and more

- [Dotenv](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv) - Color theming for dotenv files

- [MDX](https://marketplace.visualstudio.com/items?itemName=silvenon.mdx) - Color theming for mdx files

## 🎂 MVPs 🎂

- [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) - Sync your settings, keyboard shortcuts, extensions and more to your GitHub account. Next time you setup a new computer, this is the only thing you have to worry about.

- [Activitus Bar](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.activitusbar) - Moves the sidebar (usually on the left) to the bottom status bar (see picture). More space!
<img src="https://i.imgur.com/KUU4IN6.png" alt="Activitus Bar example" style="padding-left: 20px; padding-bottom: -10px"/>

- [Wrap Console Log](https://marketplace.visualstudio.com/items?itemName=midnightsyntax.vscode-wrap-console-log) - Insert console log statements for highlighted text using a keyboard shortcut. You may want to add a keyboard shortcut like this:

```json
{
  "key": "cmd+l",
  "command": "console.log.wrap.down.prefix",
  "when": "editorTextFocus"
}
```

## Tips

- Install 'code' command in PATH - [Microsoft](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)

- Enable format-on-save with the setting `"editor.formatOnSave": true,`

- Remove clutter with the right-click menu on the status bar - [View demo](https://code.visualstudio.com/updates/v1_36#_hide-individual-status-bar-items)

- Enormous guide with more - [Microsoft](https://code.visualstudio.com/docs/getstarted/tips-and-tricks)
