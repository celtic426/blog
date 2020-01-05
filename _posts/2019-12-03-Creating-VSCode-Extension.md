---
layout: post
title: 'Creating a VSCode Extension'
tags: [VSCode, extension, terminal]
---

Get up and running in minutes creating your own VSCode extension with these tools and examples.

## Generating Project Files

Install the pre-requisities: `npm install -g yo generator-code`. These tools create a working VSCode extension which you will be able to edit.

Run the wizard: `yo code`. You will be asked to enter your project details like the name and your choice of either JavaScript or TypeScript.

## Developing

As soon as the files are generated, you have a working extension you can try out. Press 'F5' or click "Run Extension" in the status bar to run the extension. This will open a new window which has your extension activated. You can begin testing the pre-built "Hello World" command.

The main file to get started with is `extension.ts`. If you `console.log` something from here, it will appear in the new window's console. You can open the console under _Help --> Toggle Developer Tools_.

If you want your code to run as soon as VSCode is laucnhed, instead of the default which only runs when your commands are called, then change the `activationEvents` field in _package.json_ to `["*"]`.

## Get Inspiration

Browse samples projects created by Microsoft [here](https://github.com/microsoft/vscode-extension-samples). For example, [this extension](https://github.com/microsoft/vscode-extension-samples/blob/master/statusbar-sample/src/extension.ts) shows how to create a status bar item which shows how many characters are selected.

My extension [Terminal Zoom](https://github.com/trybick/vscode-terminal-zoom/blob/master/src/extension.ts) is a good example of creating status bar items, registering commands, and using quick pick menus.

## Publishing

- Install the publishing tool with `npm install -g vsce`
- Create a personal access token using [these steps](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#get-a-personal-access-token)
- Create a publisher with `vsce create-publisher (publisher name)`
- Add your publisher name to your **package.json** file: `"publisher": "my-publisher-name",`
- `vsce package`
- `vsce publish`

## Updating

Once your extension is published and you make updates to your code, you can publish updates easily. Simply run the publish command followed by your choice of version incrementor: `vsce publish [minor | major | patch]`

This command will update your extension on the VSCode Marketplace, increment the version number in *package.json*, and create a new commit with the version number as the commit message.

## Further Reading

- [Microsoft - Your First Extension](https://code.visualstudio.com/api/get-started/your-first-extension)
- [Microsoft - Publishing Extensions](https://code.visualstudio.com/api/working-with-extensions/publishing-extension)
