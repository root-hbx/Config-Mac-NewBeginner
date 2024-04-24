# Basic Configuration Software

Reference
- [MacGuide](https://sourabhbajaj.com/mac-setup/)

This guide covers the basics of setting up a development environment on a new Mac. 
Whether you are an experienced programmer or not, this guide is intended for everyone to use as a reference for setting up your environment.

> XCode and Homebrew

## Xcode

[Xcode](https://developer.apple.com/xcode/) is an integrated development environment for macOS containing a suite of software development tools developed by Apple for developing software for macOS, iOS, watchOS and tvOS.

Download and install it from the App Store or from [Apple's website](https://developer.apple.com/xcode/).

For installing Xcode command line tools run:

```
xcode-select --install
```

It'll prompt you to install the command line tools. Follow the instructions and you'll have Xcode and Xcode command line tools both installed.

### XQuartz

XQuartz is Apple Inc.'s version of the X server, a component of the X Window System for macOS. It might be useful if you are developing software for macOS, it's available for download [here](http://xquartz.macosforge.org/landing/).

## Homebrew

[Homebrew](https://brew.sh/) calls itself _The missing package manager for macOS_ and is an essential tool for any developer.

### Installation

Before you can run Homebrew you need to have the **Command Line Tools for Xcode** installed. It include compilers and other tools that will allow you to build things from source, and if you are missing this it's available through the App Store > Updates. You can also install it from the terminal by running the following:

```
sudo xcode-select --install
```

To install Homebrew run the following in a terminal:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

hit **Enter**, and follow the steps on the screen.

### Setting up your `PATH`

To make the Homebrew-installed programs available in your shell, you need to add your Homebrew installation location to your `$PATH`. This is done for you already on macOS 10.14 Mojave and newer. For older versions of macOS, do the following:

You change your path by adding `/usr/local/bin` to your `PATH` environment variable. This can be done on a per-user basis by adjusting `PATH` in your `~/.bash_profile`. To do this, run:

```
echo 'PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile
```

(If you're using `zsh`, you should do this for `~/.zshrc` in addition to `~/.bash_profile`.)

Alternatively, you can also insert `/usr/local/bin` before the first line of `/etc/paths` to change the global default paths order, for all users and all major shells. An admin password will be required if you modify the file.

Then, to be able to use `brew` you need to start a new terminal session. After that you should make sure everything is working by running:

```
brew doctor
```

If everything is good, you should see no warnings, and a message that you are "ready to brew!".

### Using Homebrew

To install a package (or **Formula** in Homebrew vocabulary) simply type:

```
brew install <formula>
```

To update Homebrew's directory of formulae, run:

```
brew update
```

**Note**: If that command fails you can manually download the directory of formulas like this:

```
cd /usr/local/Homebrew/
git fetch origin
git reset --hard origin/master
```

To see if any of your formulas need to be updated:

```
brew outdated
```

To update a formula:

```
brew upgrade <formula>
```

Homebrew keeps older versions of formulas installed on your system, in case you want to roll back to an older version. That is rarely necessary, so you can do some cleanup to get rid of those old versions:

```
brew cleanup
```

If you want to see what formulae Homebrew would delete _without actually deleting them_, you can run:

```
brew cleanup --dry-run
```

To see what you have installed (with their version numbers):

```
brew list --versions
```

To search for formulas you run:

```
brew search <formula>
```

To get more information about a formula you run:

```
brew info <formula>
```

To uninstall a formula you can run:

```
brew uninstall <formula>
```

### Homebrew-Cask

[Homebrew-Cask](https://github.com/Homebrew/homebrew-cask) extends Homebrew and allows you to install large binary files via a command-line tool. You can for example install applications like Google Chrome, Dropbox, VLC and Spectacle. No more downloading `.dmg` files and dragging them to your Applications folder!

#### Search

To see if an app is available on Cask you can search on the [official Cask website](https://formulae.brew.sh/cask/). You can also search in your terminal:

```
brew search <package>
```

#### Example Applications

##### Quick Look plugins

These plugins add support for the corresponding file type to Mac Quick Look (In Finder, mark a file and press Space to start Quick Look). The plugins includes features like syntax highlighting, Markdown rendering, preview of JSON, patch files, CSV, ZIP files and more.

```
brew install --cask \
    qlcolorcode \
    qlstephen \
    qlmarkdown \
    quicklook-json \
    qlprettypatch \
    quicklook-csv \
    betterzip \
    webpquicklook \
    suspicious-package
```

##### App Suggestions

Here are some useful apps that are available on Cask.

```
brew install --cask \
    alfred \
    android-file-transfer \
    appcleaner \
    caffeine \
    cheatsheet \
    colloquy \
    docker \
    doubletwist \
    dropbox \
    google-chrome \
    google-hangouts \
    flux \
    1password \
    rectangle \
    sublime-text \
    superduper \
    transmission \
    valentina-studio \
    vlc
```

