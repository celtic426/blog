---
layout: post
title: "Using Two SSH Keys with Git"
tags: [SSH, GitHub, code]
---

I have two GitHub accounts, one that hosts my website on a custom domain and the other which holds my projects. I was able to get SSH working on both accounts with the following steps.

### Generate the keys

Running the `ssh-keygen` command will allow you generate an SSH keypair.

1. In terminal, run `ssh-keygen -t rsa -C "youremail@gmail.com"`
2. Type a location and name for the file, such as `/Users/tim/.ssh/id_rsa_primary`
3. Leave the passphrase empty and hit Enter
4. To generate a second keypair, repeat steps 1-3 providing a different name in step 2, such as `/Users/tim/.ssh/id_rsa_secondary`

### Copy keys to GitHub

1. Navigate to your SSH directory `cd ~/.ssh`
2. Run `ls -a` to show the keys you generated
3. Copy the output of `cat id_rsa_primary.pub`
4. Paste this public key into a new SSH key in your GitHub settings
5. Repeat steps 3-4 for your secondary key and second GitHub account

### Create config file

1. Still in your ~/.ssh folder, create a config file: `touch config`
2. Using the following template, only change 'primary' and 'secondary' with your names

```
Host primary.github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_primary

Host secondary.github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_secondary
```

### Add keys to your system

1. (Optional) You can delete all previous cached keys with `ssh-add -D`
2. To activate the first key on your system `ssh-add ~/.ssh/id_rsa_primary`
3. Repeat for second account `ssh-add ~/.ssh/id_rsa_secondary`
4. You can confirm they have been added using `ssh-add -l`

```
2048 SHA256:8moy5Zmdc1XDMv64mh1LHG/13zcmbYCPaY9sFwkWuFM /Users/tim/.ssh/id_rsa_primary (RSA)
2048 SHA256:NOlGpixtyoCK7RyWoVTd7z6k/PFyEaEEeV9YpIij8Sc /Users/tim/.ssh/id_rsa_secondary (RSA)
```

### Test connection

Connect to GitHub using your aliases and you should receive a success message.

```
$ ssh -T git@primary.github.com
Hi tim! You've successfully authenticated, but GitHub does not provide shell access.

$ ssh -T git@secondary.github.com
Hi tim! You've successfully authenticated, but GitHub does not provide shell access.
```

### Edit git config

I still had to make one more change in order to push to my secondary account.

1. Navigate to and open the git config file inside your repo folder `cd project/.git/.config`
2. Overwrite the 'origin' section with the following.

* `secondary` = the host alias in your ssh config file (my aliases are 'primary' and 'secondary')
* `username` = your github username associated with this repos
* `project` = the name of the repo

```
[remote "origin"]
	url = git@secondary.github.com:username/project.git
```

### Conclusion



### Additional resources

* [YouTube - Mulitple SSH Keys on a Mac](https://www.youtube.com/watch?v=9u4QPEMFK4A)
* [StackOverflow - Mulitple GitHub Accounts & SSH Config](https://stackoverflow.com/questions/3225862/multiple-github-accounts-ssh-config)
* [Gist by jexchan](https://gist.github.com/jexchan/2351996)
