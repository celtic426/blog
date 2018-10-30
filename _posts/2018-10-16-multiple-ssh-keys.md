---
layout: post
title: "Using SSH with Two GitHub Accounts"
tags: [SSH, GitHub, Code]
---

This guide walks through setting up two SSH keys on your Mac for use with two different GitHub accounts. You can then seamlessly push to and clone repos on both accounts.

**Note**: If you just need push access to another account's repo, you can use the [Collaborators](https://help.github.com/articles/inviting-collaborators-to-a-personal-repository/) feature on GitHub.

### Generate Keys

*The 'ssh-keygen' command allows you to generate a public and a private keypair.*

1. Create an SSH keypair: `ssh-keygen -t rsa -C "youremail@gmail.com"`.
2. Type a location and name for the file, such as `/Users/yourname/.ssh/id_rsa_primary` (replacing `primary` with desired name).
3. Hit `Enter` twice, leaving the passphrase empty.
4. Repeat steps 1-3 to create a second keypair, providing a different name in step 2, such as `/Users/tim/.ssh/id_rsa_secondary`.

### Copy Keys to GitHub

*The public RSA key is copied to GitHub while the private key lives on your machine.*

1. Navigate to your SSH directory: `cd ~/.ssh`.
2. Running `ls -a` should list your new keys.
3. Enter `cat id_rsa_primary.pub` and copy the output. It should start with `ssh-rsa` and end with your email address.

```terminal
tim@mac .ssh $ cat id_rsa_primary.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC33kfdi1KmASCcBrPn7wh0CjHpqu2rnlCptYQFIS21pFeF9aitpYCnZINJE91srJUjElAHzXRgLpvcROwx1wWOrULzd0dgx/8ocw0wKB26wqcSM3bWTXGd+/1/ena5SPdzfK8ZCUasIIYOYAR7YoxeBfB1aimaI/j/mE6vr57oACsWJnAdh9FV/i6XAMQJwxNccQYsAm2nG+5WwPphMv2/v7YjaLmD0L9JMuwZGyB1EZucldZLnvbvkZx6YEOG2k+dygfV8+jplC6GQ5D/RmMB5DPD/+tpHcpVQtkcEkkGZcUc5afJDj4dFkZtveD35gzOdFbvoRJDjfE+qMW7UlU1 email@gmail.com
```
4. In your GitHub account settings, create a new SSH key and paste the output from the previous step.
5. Repeat steps 3-4 with your secondary key and second GitHub account.

### Create Config File

1. In your ~/.ssh folder, create a file called 'config': `touch config`.
2. Use the following template replacing 'primary' and 'secondary' with your accounts.

*The first 'Host' block makes your ssh keys persist across reboots. The next two blocks setup an alias which points to an ssh key.*

```bash
Host *
	AddKeysToAgent yes
	UseKeychain yes
	IdentityFile ~/.ssh/id_rsa_primary //replace primary
  IdentityFile ~/.ssh/id_rsa_secondary //replace secondary

Host primary.github.com // replace primary
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_primary // replace primary

Host secondary.github.com // replace secondary
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_secondary // replace secondary
```

### Add keys to your system

*The 'ssh-add' command activates a key on your system.*

1. (Optional) You can delete all previous cached keys with `ssh-add -D`.
2. To activate the first key on your system: `ssh-add -K ~/.ssh/id_rsa_primary`.
3. Repeat for second account: `ssh-add -K ~/.ssh/id_rsa_secondary`.
4. You can confirm they have been added with `ssh-add -l`.

```terminal
2048 SHA256:8moy5Zmdc1XDMv64mh1LHG/13zcmbYCPaY9sFwkWuFM /Users/tim/.ssh/id_rsa_primary (RSA)
2048 SHA256:NOlGpixtyoCK7RyWoVTd7z6k/PFyEaEEeV9YpIij8Sc /Users/tim/.ssh/id_rsa_secondary (RSA)
```

### Test the connection

*Connect to GitHub and you should receive a success message.*

1. Enter `ssh -T git@primary.github.com`.
2. Repeat step 1 for your second account.

```terminal
$ ssh -T git@primary.github.com
Hi tim! You've successfully authenticated, but GitHub does not provide shell access.

$ ssh -T git@secondary.github.com
Hi tim! You've successfully authenticated, but GitHub does not provide shell access.
```

### Edit git config

*You might need one more change in order to push to your secondary account's repos.*

1. Navigate to and open the git config file inside your repo folder `cd projectname/.git/.config`
2. Overwrite the 'origin' section with the following.

```bash
[remote "origin"]
	url = git@secondary.github.com:username/project.git
```

* `secondary` = the host alias in your ssh config file
* `username` = your github username associated with this repo
* `project` = the name of this repo

### Conclusion
If you made it this far, congrats!


### Additional resources

* [YouTube - Mulitple SSH Keys on a Mac](https://www.youtube.com/watch?v=9u4QPEMFK4A)
* [StackOverflow - Mulitple GitHub Accounts & SSH Config](https://stackoverflow.com/questions/3225862/multiple-github-accounts-ssh-config)
* [Gist by jexchan](https://gist.github.com/jexchan/2351996)
