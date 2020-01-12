---
layout: post
title: 'Creating a VSCode extension'
tags: [VSCode, extension, terminal]
---

Get up and running in minutes creating your own VSCode extension with these tools and examples.

## Generating Project Files

Install the pre-requisites and run the wizard:

```terminal
npm install -g yo generator-code
yo code
```

You will be asked to choose JavaScript or TypeScript and for a project name. This creates a working VSCode extension which you will be able to run straight away.

## Developing

Press _F5_ or go to _Debug ---> Start Debugging_ to run the extension. This opens a new window which has the extension activated. You can begin testing the pre-built "Hello World" command.

The main file to get started with is `extension.ts`. If you `console.log` something, it will appear in the new window's console. You can open the console under _Help --> Toggle Developer Tools_.

If you want your code to run as soon as VSCode is launched, instead of the default which only runs when your commands are called, consider changing the `activationEvents` field in _package.json_ to `["*"]`.

## Getting Inspiration

Browse samples projects created by Microsoft [here](https://github.com/microsoft/vscode-extension-samples). For example, [this extension](https://github.com/microsoft/vscode-extension-samples/blob/master/statusbar-sample/src/extension.ts) shows how to create a status bar item displaying how many characters are selected.

My extension [Terminal Zoom](https://github.com/trybick/vscode-terminal-zoom/blob/master/src/extension.ts) is a good example of creating status bar items, registering commands, and using quick pick menus.

## Publishing

- Install the publishing tool with `npm install -g vsce`
- Create a personal access token using [these steps](https://code.visualstudio.com/api/working-with-extensions/publishing-extension#get-a-personal-access-token)
- Create a publisher with `vsce create-publisher (publisher name)`
- Add your publisher name to *package.json*: `"publisher": "my-publisher-name"`
- `vsce package`
- `vsce publish`

## Updating

Once your extension is published and you make changes to your code, you can push updates by running the publish command followed by your choice of a version incrementor:

```terminal
vsce publish [minor | major | patch]
```

This command updates your extension on the VSCode Marketplace, increments the version number in _package.json_, and creates a new commit with this change.

## Further Reading

- [Microsoft - Your First Extension](https://code.visualstudio.com/api/get-started/your-first-extension)
- [Microsoft - Publishing Extensions](https://code.visualstudio.com/api/working-with-extensions/publishing-extension)
