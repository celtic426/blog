---
layout: post
title: 'How to Create a VSCode Extension'
tags: [VSCode, extension, terminal]
---

## Overview

Scaffold the project files
npm install -g yo generator-code
Choose JS or TS and give it a name
This creates all the files you need to get started.

The main file is src/extension.js which by default already contains a working extension you can try out.
Press F5 or click "Run Extension" in the status bar. This opens a new window which has your extension active.
You can open the Developer Tools under Help --> Toggle Developer Tools (console logs will show here).
Change activiationEvents in package json to \*.

## Publishing

npm install -g vsce

Create a personal access token using these steps: https://code.visualstudio.com/api/working-with-extensions/publishing-extension#get-a-personal-access-token
Create a publisher with `vsce create-publisher (publisher name)` (will prompt for access token)
Add your publisher name to your package.json `"publisher": "my-publisher-name",`

vsce package
vsce publish

## Pushing updates after published

vsce publish minor
Running this command will:

- push your latest code to the VSCode marketplace
- auto-increment the version number in your package.json
- creat a git commit with the version number

## Add repo info to package json

Optionally add this information your package.json

```json
  "bugs": {
    "url": "https://github.com/trybick/vscode-terminal-zoom/issues"
  },
  "homepage": "https://github.com/trybick/vscode-terminal-zoom",
  "repository": {
    "type": "git",
    "url": "https://github.com/trybick/vscode-terminal-zoom.git"
  },
  "keywords": [
    "terminal",
    "zoom",
    "font size",
    "status bar"
  ],
```

## Browse sample projects

Microsoft has a repositiry of sample projects. This one is a sample of creating a status bar item: https://github.com/microsoft/vscode-extension-samples/blob/master/statusbar-sample/src/extension.ts
