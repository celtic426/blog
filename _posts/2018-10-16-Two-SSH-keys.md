---
layout: post
title: "Using Two SSH Keys with Git"
tags: [code]
---

I have two GitHub accounts, one that hosts my website on a custom domain and the other which holds my projects. I was able to get SSH working on both accounts with the following steps.

### Generate two pairs of keys

Running the `ssh-keygen` command will allow you to name and save an SSH keypair.

1. In terminal, run `ssh-keygen -t rsa -C "youremail@gmail.com"`
2. The default save location is `/Users/tim/.ssh/id_rsa` but you can give it a name like `/Users/tim/.ssh/id_rsa_main`
3. Leave the passphrase empty and hit Enter

You now have a public and private key saved in your `~/.ssh folder. Repeat steps 1-3 providing a different name in step 2, such as `id_rsa_secondary`.




[Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/markup-syntax-highlighting).

### GFM Code Blocks

GitHub Flavored Markdown [fenced code blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/) are supported. To modify styling and highlight colors edit `/_sass/syntax.scss`.

```css
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
```

### Code Blocks in Lists

Indentation matters. Be sure the indent of the code block aligns with the first non-space character after the list item marker (e.g., `1.`). Usually this will mean indenting 3 spaces instead of 4.

1. Do step 1.
2. Now do this:

   ```ruby
   def print_hi(name)
     puts "Hi, #{name}"
   end
   print_hi('Tom')
   #=> prints 'Hi, Tom' to STDOUT.
   ```

3. Now you can do this.
