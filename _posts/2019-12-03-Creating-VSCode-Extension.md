---
layout: post
title: 'How to Create a VSCode Extension'
tags: [VSCode, extension, terminal]
---

It's easy to get started developing VSCode extensions!

## How to Create a VSCode Extension

## Scaffolding the Project

Follow these steps to generate a project folder with a working extension.

- `npm install -g yo generator-code` - install pre-reqs
- `yo code` - start the project generator
- Choose options (e.g. JavaScript or TypeScript and give it a name)

## Developing

Press 'F5' or click "Run Extension" in the status bar to run the extension. This will open a new window which has your extension activated.

If you `console.log` something, it will appear in the new window's console. You can open the console under _Help --> Toggle Developer Tools_.

## When the Extension should Run

By default the extension only runs when the command is run. If you want the extension to run upon startup, change the `activationEvents` field in **package.json**:

```js
  "activationEvents": [
    "*"
  ],
```

## Publishing

- Install the publishing tool with `npm install -g vsce`
- Create a personal access token using [these steps](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#get-a-personal-access-token)
- Create a publisher with `vsce create-publisher (publisher name)` (requires access token created in previous step)
- Add your publisher name to your **package.json** file: `"publisher": "my-publisher-name",`
- `vsce package`
- `vsce publish`

## Updating Your Extension

- Run the publish command followed by your choice of version incrementor: `vsce publish [minor | major | patch]`

In addition to updating your extension on the VSCode Marketplace, this command also increments the version number in your **package.json** and creates a new git commit with the version number as the commit message.

## Get Inspiration

Browse samples projects created by Microsoft [here](https://github.com/microsoft/vscode-extension-samples). For example, [this extension](https://github.com/microsoft/vscode-extension-samples/blob/master/statusbar-sample/src/extension.ts) shows how to create a status bar item which shows how many characters are selected.
