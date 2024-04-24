# Interesting Plugins and APPs

> some interesting plugins and APPs in zsh

## tree

`tree` is a recursive directory listing command that produces a depth indented listing of files.

### Installation

To install the latest version, use homebrew:

```
brew install tree
```

### Usage

Running `tree` will produce output like this:

```
$ tree

.
├── Apps
│   ├── Octave.md
│   ├── README.md
│   ├── Settings.md
│   ├── araxis-merge.jpg
│   ├── beyond-compare.png
│   ├── delta-walker.jpg
│   ├── filemerge.png
│   └── kaleidoscope.png
├── CONTRIBUTING.md
├── Cpp
│   └── README.md
├── Docker
│   └── README.md
├── Git
│   ├── README.md
│   └── gitignore.md
└── Go
    └── README.md

5 directories, 14 files
```

To limit the recursion you can pass an `-L` flag and specify the maximum depth `tree` will use when searching.

```
tree -L 1
```

will output:

```
.
├── Apps
├── CONTRIBUTING.md
├── Cpp
├── Docker
├── Git
└── Go

5 directories, 1 files
```

## fzf

[`fzf`](https://github.com/junegunn/fzf) is a general-purpose command-line fuzzy finder. On it's own it's not very useful but when combined with other tools it becomes super powerful.

### Installation

Use [Homebrew](https://sourabhbajaj.com/mac-setup/Homebrew/README.html) to install `fzf`:

```
brew install fzf
```

If you want to use shell extensions (better shell integration):

```
/usr/local/opt/fzf/install
```

which gives you:

- Key bindings (`CTRL-T`, `CTRL-R`, and `ALT-C`) (available for _bash_, _zsh_ and _fish_)
- Fuzzy auto-completion (available for _bash_ and _zsh_)

### Example Usages

Add any of these functions to your shell configuration file and apply the changes to try them out. Or just paste the function in your terminal if you just want to try it out without saving it.

```
# fd - cd to selected directory
fd() {
  local dir
  dir=$(find ${1:-.} -path '*/\.*' -prune \
                  -o -type d -print 2> /dev/null | fzf +m) &&
  cd "$dir"
}
```

```
# fh - search in your command history and execute selected command
fh() {
  eval $( ([ -n "$ZSH_NAME" ] && fc -l 1 || history) | fzf +s --tac | sed 's/ *[0-9]* *//')
}
```

**For more fuzzy search examples see the [official repo](https://github.com/junegunn/fzf#fuzzy-completion-for-bash-and-zsh).**

#### Chrome history from your terminal

**Note**: original [blog post](https://junegunn.kr/2015/04/browsing-chrome-history-with-fzf/)

Open up your shell config and add following function:

```
# ch - browse chrome history
ch() {
  local cols sep
  cols=$(( COLUMNS / 3 ))
  sep='{::}'

  cp -f ~/Library/Application\ Support/Google/Chrome/Profile\ 1/History /tmp/h

  sqlite3 -separator $sep /tmp/h \
    "select substr(title, 1, $cols), url
     from urls order by last_visit_time desc" |
  awk -F $sep '{printf "%-'$cols's  \x1b[36m%s\x1b[m\n", $1, $2}' |
  fzf --ansi --multi | sed 's#.*\(https*://\)#\1#' | xargs open
}
```

**Note**: Ensure that path to `History` file is correct; read more information on [StackOverflow](https://stackoverflow.com/a/16742333/1564365).

## ack

`ack` is a search tool designed for code. It's built to be a replacement for `grep` with higher speed and more options.

### Installation

To install the latest version, use homebrew.

```
brew install ack
```

### Why use `ack` over `grep`

- Faster
- Skips unimportant files by default
- It searches recursively by default
- Customizable

### Usage

```
ack [OPTION]... PATTERN [FILES OR DIRECTORIES]
```

Let's say you want to find all JavaScript files that are using the module `pancakes` in your project, with `ack` it's as easy as

```
ack --js pancakes
```

Or you may want to find all files that _does not_ contain the word _brew_

```
ack -L brew
```

### Customization

You can customize `ack` to behave the way you want it to, this configuration i s stored in `/.ackrc`.

For example, you can add a custom type to use as a flag when searching. The following configuration will allow you to only search in `.md`, `.mkd` and `.markdown` files using the `--markdown` flag.

```
--type-set=markdown=.md,.mkd,.markdown
```

You can also tell ack to always sort and use colors in the result.

```
--sort-files
--color
```

To see what configuration `ack` uses you can use the `dump` flag.

```
ack --dump
```

### Alternatives to `ack`

There's [The Silver Surfer](https://github.com/ggreer/the_silver_searcher) which describes itself as a

> A code searching tool similar to `ack`, with a focus on speed.

## htop

showcase all the PID and CPU processing currently

```bash
brew install htop
```

## lsd

showcase the flies and folders with more intuitive in terminal

```bash
brew install lsd
```

## duf

showcase the occupation in terminal

```bash
brew install duf
```

```bash
+------------------------------------------------------------------------------------------+
| 9 local devices                                                                          |
+-----------------+--------+--------+--------+---------------------+------+----------------+
| MOUNTED ON      |   SIZE |   USED |  AVAIL |         USE%        | TYPE | FILESYSTEM     |
+-----------------+--------+--------+--------+---------------------+------+----------------+
| /               | 926.4G | 180.3G | 746.1G | [#.........]  19.5% | apfs | /dev/disk3s1s1 |
| /System/Volumes | 926.4G | 180.3G | 746.1G | [#.........]  19.5% | apfs | /dev/disk3s5   |
| /Data           |        |        |        |                     |      |                |
| /System/Volumes | 500.0M |  22.8M | 477.2M | [..........]   4.6% | apfs | /dev/disk1s3   |
| /Hardware       |        |        |        |                     |      |                |
| /System/Volumes | 926.4G | 180.3G | 746.1G | [#.........]  19.5% | apfs | /dev/disk3s2   |
| /Preboot        |        |        |        |                     |      |                |
| /System/Volumes | 926.4G | 180.3G | 746.1G | [#.........]  19.5% | apfs | /dev/disk3s4   |
| /Update         |        |        |        |                     |      |                |
| /System/Volumes | 926.4G | 180.3G | 746.1G | [#.........]  19.5% | apfs | /dev/disk3s1   |
| /Update/mnt1    |        |        |        |                     |      |                |
| /System/Volumes | 926.4G | 180.3G | 746.1G | [#.........]  19.5% | apfs | /dev/disk3s6   |
| /VM             |        |        |        |                     |      |                |
| /System/Volumes | 500.0M |  22.8M | 477.2M | [..........]   4.6% | apfs | /dev/disk1s1   |
| /iSCPreboot     |        |        |        |                     |      |                |
| /System/Volumes | 500.0M |  22.8M | 477.2M | [..........]   4.6% | apfs | /dev/disk1s2   |
| /xarts          |        |        |        |                     |      |                |
+-----------------+--------+--------+--------+---------------------+------+----------------+
+---------------------------------------------------------------------------------+
| 1 special device                                                                |
+------------+--------+--------+-------+---------------------+-------+------------+
| MOUNTED ON |   SIZE |   USED | AVAIL |         USE%        | TYPE  | FILESYSTEM |
+------------+--------+--------+-------+---------------------+-------+------------+
| /dev       | 198.5K | 198.5K |    0B | [##########] 100.0% | devfs | devfs      |
+------------+--------+--------+-------+---------------------+-------+------------+
  ~                                                                                     01:34:04
❯
```

## gping

```bash
brew install gping
```

```bash
gping + URL
```

## lsd

[lsd](https://github.com/lsd-rs/lsd) is a rewrite of GNU ls with lots of added features like colors, icons, tree-view, more formatting options etc. The project is heavily inspired by the super colorls project.

```bash
brew install lsd
```

## Parallels Desktop Crack

[PD](https://github.com/XiaoCC/ParallelsDesktopCrack) is commonly used in our daily develop

## QuickRecorder

[QuickRecorder](https://github.com/lihaoyun6/QuickRecorder) is a lightweight screen recorder based on ScreenCapture Kit for macOS 

```bash
brew install lihaoyun6/tap/quickrecorder
```

## BLEUnlock

[This plugin](https://github.com/ts1/BLEUnlock) is a small menu bar utility that locks and unlocks your Mac by proximity of your iPhone, Apple Watch, or any other Bluetooth Low Energy device.

## stats

[stats](https://github.com/exelban/stats) is a replacement of _iStat Menus_

It's a macOS system monitor in your menu bar


## bartender 5

[bartender](https://www.macbartender.com/)  is an award-winning app for macOS that for more than 10 years has superpowered your menu bar, giving you total control over your menu bar items, what's displayed, and when, with menu bar items only showing when you need them.  
Bartender improves your workflow with quick reveal, search, custom hotkeys and triggers, and lots more.

暴力开源版：[bartender-ru](https://appstorrent.ru/133-macbartender.html)



## some cool lists

- [awesome-mac](https://github.com/jaywcjlove/awesome-mac)
- [modern-Unix](https://github.com/ibraheemdev/modern-unix)
