# Git and SSH

> including
> - Github / Git 工作流配置指南
> - SSH公私钥连接指南

这份教程重点在“Git 的新手入门”，并不是详细指导，如果有想要深入了解git的，欢迎移步至[GitTutorial@bxhu](https://github.com/root-hbx/Git_Tutorial)

## Initialization for Git and GitHub

What's a developer without [Git](http://git-scm.com/)? To install, run:

```
brew install git
```

When done, to test that it installed properly you can run:

```
git --version
```

And `which git` should output `/usr/local/bin/git`.

Next, we'll define your Git user (should be the same name and email you use for [GitHub](https://github.com/)):

```
git config --global user.name "Your Name Here"
git config --global user.email "your_email@youremail.com"
```

They will get added to your `.gitconfig` file.

To push code to your GitHub repositories, we will use the recommended HTTPS method. There are also instructions for using SSH. To prevent `git` from asking for your username and password every time you push a commit you can cache your credentials by running the following command, as described in the [instructions](https://help.github.com/articles/caching-your-github-password-in-git/).

```
git config --global credential.helper osxkeychain
```

In fact, the mail and your name above are of no sense. They will not be used any more in your future. So you can just leave it and go on next.

## Using HTTPS for GitHub (recommended)

These instructions are from [the official documentation](https://help.github.com/en/github/using-git/which-remote-url-should-i-use#cloning-with-https-urls-recommended).

### Clone repositories using HTTPS

After creating a new repo on GitHub, clone it using:

```
git clone https://github.com/<username>/<repo-name>.git
```

- if you had initialized with a README.

If you did not, follow the instructions in the section below.

### Set up a new or existing repo with HTTPS for GitHub

If you are setting up a new repo, add at least one file and commit first. Then, configure the remote and push to GitHub by running:

```
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin master
```

PS:
- You must create a repo on GitHub and then clone it into local devices
- You are not allowed to initialize a local repo as a "git-permitted" one!
- So, follow the steps above and you will be satisfied

## SSH Config for GitHub

These instructions are for those who wish to use SSH and not HTTPS, and are from [the official documentation](https://help.github.com/articles/generating-ssh-keys).

### Check for existing SSH keys

First check for existing SSH keys on your computer by running:

```
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

```bash
# for example (mine)
❯ ls -al ~/.ssh
drwx------ huluobo staff 288 B  Sun Apr 21 17:40:23 2024  .
drwxr-x--- huluobo staff 2.8 KB Thu Apr 25 00:25:47 2024  ..
.rw-r--r-- huluobo staff 303 B  Sat Apr 13 00:11:32 2024  config
.rw------- huluobo staff 2.6 KB Tue Jan 23 15:29:13 2024  id_rsa
.rw-r--r-- huluobo staff 588 B  Tue Jan 23 16:03:16 2024  id_rsa.pub
.rw------- huluobo staff 3.4 KB Sat Feb 24 01:26:25 2024  id_rsa_GithubConnection
.rw-r--r-- huluobo staff 747 B  Sat Feb 24 01:26:25 2024  id_rsa_GithubConnection.pub
.rw------- huluobo staff 2.8 KB Sun Apr 21 17:40:23 2024  known_hosts
.rw------- huluobo staff 2.1 KB Sun Apr 21 17:40:10 2024 󰁯 known_hosts.old

# the missing signal means "lsd" can not be classfied with ASCII, you can ignore it here
 ```

Check the directory listing to see if you have files named either `id_rsa.pub` or `id_dsa.pub`. If you don't have either of those files then read on, otherwise skip the next section.

### Generate a new SSH key

If you don't have an SSH key you need to generate one. To do that you need to run the commands below, and make sure to substitute the placeholder with your email (this time the email should be serious for it's significant in generating your isa). The default settings are preferred, so when you're asked to enter a file in which to save the key, just press Enter to continue.

```
ssh-keygen -t rsa -C "your_email@example.com"
# Creates a new ssh key, using the provided email as a label
```

### Add your SSH key to the ssh-agent

Run the following commands to add your SSH key to the `ssh-agent`.

```
eval "$(ssh-agent -s)"
```

If you're running macOS Sierra 10.12.2 or later, you will need to modify your `~/.ssh/config` file to automatically load keys into the ssh-agent and store passphrases in your keychain:

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

The config file contains all the ssh-keys that you owned, and you must config them well, otherwise you may not be able to contact with the specified Servers or Website.

No matter what operating system version you run you need to run this command to complete this step:

```
ssh-add -K ~/.ssh/id_rsa
```

### Adding a new SSH key to your GitHub account

The last step is to let GitHub know about your SSH key so GitHub can recognize you. Run this command to copy your key to your clipboard:

```
pbcopy < ~/.ssh/id_rsa.pub
```

Then go to GitHub and [input your new SSH key](https://github.com/settings/ssh/new). Paste your key in the "Key" text-box and pick a name that represents the computer you're currently using.

We are now ready to use SSH with GitHub!

### Clone repositories using SSH

After creating a new repo on GitHub, clone it using

```
git clone git@github.com:<username>/<repo-name>.git
```

- if you had initialized with a README.

If you did not, follow the instructions in the section below.

### Set up a new or existing repo with SSH for GitHub

If you are setting up a new repo, add at least one file and commit first. Then, configure the remote and push to GitHub by running:

```
git remote add origin git@github.com:<username>/<repo-name>.git
git push -u origin master
```

