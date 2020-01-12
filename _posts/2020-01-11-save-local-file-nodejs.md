---
layout: post
title: 'Save a file to local machine with Node.js'
tags: [save, persist, file, node.js, script]
---

Find out how to store data in a file on a user's machine and retrieve it later using Node.js. This might be useful if you need to store a token and reference it later (although this is not secure since it's stored in plain text).

## Creating the file

```javascript
const storage = require('node-persist');

async function saveToDisk(dataToSave) {
  await storage.init({ dir: '/Applications/my-app' }).catch(err => console.error(err));
  await storage.setItem('myData', dataToSave);
}
```

Here we create a function which we can provide a string to save. After running this command you should have a file in the specified folder containing text of the key-pair values given.

## Retrieving the data

```javascript
await storage.init({ dir: '/Applications/my-app' }).catch(err => console.error(err));
const item = await storage.getItem('myData');
```

To access the data we saved, the same init command is called followed my the `getItem` method, while specifying the key you used while saving.

## Summary

[node-persist](https://github.com/simonlast/node-persist)
