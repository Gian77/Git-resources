# Git-resources

## In this repo some instructions and useful tutorials and links on how to work with Git.

#### Copirght (C) 2022 *gian.benucci[at]gmail.com* MIT License

## 1) Connect your local computer to Github

The first step you need to do to work with **Git** is to have your computer able to comunicate to **Github** or another version control system.

* ### Autenticate your local computer

A couple of good guides for Mac, Windows and Linux can be found here: <bc>
https://docs.github.com/en/authentication
https://happygitwithr.com/rstudio-git-github.html

So, check if you have any `ssh` key already present in your you computer `/home` directory

```
ls -al ~/.ssh
```
* ### Generate *SSH* keys on your local computer

if you don't have `ssh` you have to install it. In Linux (e.g. Ubuntu) you just install it by running
```
sudo apt-get install openssh-server
man git
```
You need to introduce yourself to Git. set up your configuration first. So, for example:

```
git config --global user.name "Gian77"
git config --global user.email "gian.benucci@gmail.com"
git config --list
```
You then have to create keys. In Linux you can do:
```
ssh-keygen -t ed25519 -C "youremailongithub@example.com"
```
Then follow the directions. You will be prompted to create a file where to save the keys and also a passphrase. You can give a name to the key file or leave it as the default name.

> **_NOTE_** This guide shows you how to connect trhough `shh` rather than `hptts` since the last one can give you
> trouble with the double with **Github** double factor autentication.

In MacOSX, you can create key pairs this way:
```
ssh-add --apple-use-keychain ~/.ssh/id_rsa.pub
ssh-add --apple-use-keychain ~/.ssh/id_rsa
```
Then, if you run MacOS Sierra o higher, you have to add these following lines into your `.ssh/config`.
If you do not have a `config` file just create one within the `.ssh` folder. It should look like this:
```
gian-21@Gians-MacBook-Air ~ % cat ~/.ssh/config
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

* ### Generate a new SSH key for your computer on Github

Then, go to your Github profile and go to *Settings > SSH and GPG keys > New SSH key*. Paste the previously generated key in the specifcied and ad a name that link to it e.g. "Gian Macbook Air". You will need an SSH key for each computer you are connecting to Github. For example, copy the key in:
```
cat .ssh/id_ed25519.pub
```
You should be now all set and you can start using git.

> **_NOTE_** At the first time you try to `git pull` you may be prompted to inset a password. That password is the passphrase you added when you genrated the key pair and not the github passwword.


## 2) Creating a repository for your project

Now, go to Githib and create a repo *Repositories > New*. Give the repo a name, make it public, then add a `README.md` file and a `LICENSE` (e.g. MIT), you may want to ad a `.gitingore` and the create.
The .gitignore file is very useful and I suggest you add it in, it helps to specify which files you do not want Git to track.

After that you have two options to link the newly creted repo to your computer.

* ### Clone the repository from Github

In Githib clic on the created repository, click on *Code*, and then copy the ssh link. Then, in from a terminal, navigate to the folder where you want to add your repo, and the clone it. For example:

```
git clone git@github.com:Gian77/How-to-ggplot2.git
```
After that you can `cd` your new git repo.

3) ## Start working with your Git repository

At this point you can start working at you rproject in the repo. When you are ready, you should *stage*, add the files you want to push in Github, *commit*, create a comment of what this push is about, and finally push your new content.

```
git status
git add .
git commit -m "initial commit"
git push
```

## 4) Adding a local repository to GitHub using Git

This is a little more tedious and with two factor authentication or authentication token. You can find good info on how to set it up [here](https://docs.github.com/en/get-started/importing-your-projects-to-github/importing-source-code-to-github/adding-an-existing-project-to-github-using-the-command-line) and [here](https://github.com/donnemartin/gitsome#enabling-bash-completions).

In Github, create a new repository. To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub.

> **_NOTE_** If you want you can create .gitingore, LICENSE and README.md files in the local directory and push them with your first push.

```
git init
```

Add files

```
git add .
```
Commit the files that you've staged in your local repository.

```
git commit -m "First commit"
```
At the top of your repository on GitHub.com's Quick Setup page, click  to copy the remote repository URL. In Terminal, add the URL for the remote repository where your local repository will be pushed.

```
# Sets the new remote URL
git remote add origin  <REMOTE_URL>

# Verifies the new remote URL
git remote -v
```

If you end up having the error:
```
fatal: bad config value for 'color.ui' in /mnt/home/benucci/.gitconfig
```
open `/mnt/home/benucci/.gitconfig` and erasing the [color] section should solve it.

> **_NOTE_**
To permanently add you passphrase to the key just do `ssh-add`
If you want to remove the file from the Git repository and the filesystem, use: `git rm file.txt` and then `git commit -m "remove file.txt"`

# Some useful tips

If you cloned an empty repo, and then you want to push a just created `README.md`, you should specify the branch you need to upload the file into. FOr example, if you want the branch master to be generated then:
```
git push origin master
```

### To visualize branches
Not all commands work in the same version of git.
```
git branch
git rev-parse --abbrev-ref HEAD
git branch --show-current
```

### To pull a specific repo/file
```
git fetch
git checkout HEAD stats/readCounts.txt
```

### Git removing deleted files from tracking
Use git rm to delete a file and make Git recognize the deletion.

```
git rm path/to/file
git commit
git push
```

to undelete deleted a file in git
```
git checkout -- <file>
```
to unstage a deleted file

# Very dangerous commands
```
git clean -f
git reset
```
# Errors and solves
You have not concluded your merge (MERGE_HEAD exists).
Please, commit your changes before you can merge.

```
git merge --abort
git reset --merge
```
# Chnage git default editor to nano

There are two ways in which this can be done. The first is via the terminal; this is useful if you want your editor to be `nano`, for example. The command to do this is `git config --global core.editor "nano"`. You can change the highlighted section with your editor of choice!

Another way to do this is to edit the `.gitconfig` file in your home directory. The location of this file depends on the operating system you're using. 
