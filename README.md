# Git-resources

## In this repo some instructions and useful tutorials and links on how to work with Git.

#### Copirght (C) 2022 gian.benucci[at]gmail.com MIT License

# Connect your local computer to Github

The first step you need to work with **Git** is to have your computer able to comunicate to **Github**. 

### Autenticate your local computer 

A couple of good guides for Mac, Windows and Linux can be found here: 	
https://docs.github.com/en/authentication
https://happygitwithr.com/rstudio-git-github.html

Check if you have any `ssh` key already present in your `/home` directory
```
ls -al ~/.ssh
```
### Generate *SSH* keys

if not, you have to create keys. In Linux you can do:
```
ssh-keygen -t ed25519 -C "youremailongithub@example.com"
```
then follow the directions. You will be prompted to create a file where to save the keys and also a passphrase.

> **_NOTE_** This guide shows you how to connect trhough `shh` since `hppts` may give you trouble
> with the double factor autentication now needed to access Github.

Similarly, in MacOSX, you can create key pairs this way:

ssh-add --apple-use-keychain ~/.ssh/id_rsa.pub
ssh-add --apple-use-keychain ~/.ssh/id_rsa

Then, if you run MacOS Sierra o higher, you have to add these following lines into your `.ssh/config`.
If you do not have a `config` file just create one within the `.ssh` folder. It should look like this:
```
gian-21@Gians-MacBook-Air ~ % cat ~/.ssh/config
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

### Generate a new SSH key for your computer on Github

Then, go to your **Github** profile and go to *Settings > SSH and GPG keys > New SSH key*. Paste the previously generated key in the specifcied and ad a name that link to it e.g. "Gian Macbook Air".
```
cat .ssh/id_ed25519.pub 
```
You should be now all set and you can start using git.

> **_NOTE_** At the first time you try to `git pull` you may be prompted to inset a password. That password is the passphrase you added when you genrated the keypar and not the github paswword.


