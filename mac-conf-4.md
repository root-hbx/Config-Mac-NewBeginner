# Commonly Used Text Editor and IDEs

> IDE and text editor

## Vim

[Vim](http://www.vim.org/) is a highly configurable text editor built to make creating and changing any kind of text very efficient. It is included as "vi" with most UNIX systems and with Apple macOS.

### Installation

To install the latest version, use homebrew:

```
brew install vim
```

### The Ultimate vimrc

[The Ultimate vimrc](https://github.com/amix/vimrc) is a collection of vimrc configurations to make easy the usage of vim.

To download the The Ultimate vimrc, you need to install the git client. If you need install it, use home brew:

```
brew install git
```

Now, download the vimrc files:

```
git clone https://github.com/amix/vimrc.git ~/.vim_runtime
```

To install the complete version, run:

```
sh ~/.vim_runtime/install_awesome_vimrc.sh
```

To install the _basic_ version, run:

```
sh ~/.vim_runtime/install_basic_vimrc.sh
```

#### Update

To update the vimrc scripts, run:

```
cd ~/.vim_runtime && git pull --rebase && cd -
```

### Maximum Awesome

[Maximum Awesome](https://github.com/square/maximum-awesome) is a collection of vim configuration and plugins, like a configuration manager for the vim environment.

#### Installation

To install it, just make a clone of the repository with the git client:

```
git clone https://github.com/square/maximum-awesome.git
```

Then install it:

```
cd maximum-awesome
rake
```

> **NOTE:** the rake command will install all dependencies needed

### My Configuration of Vim

You can gain an insight into Vim Configuration in [Vim-Conf @bxhu](https://github.com/root-hbx/Config-Vim-Neovim)

## NeoVim

- You can gain an insight into Vim Configuration in [Neovim-Conf @bxhu](https://github.com/root-hbx/Config-Vim-Neovim)
- And you can learn some details on [LazyVim](https://www.lazyvim.org/)

## Emacs

[Emacs](https://www.gnu.org/software/emacs/) is a family of text editors that are characterized by their extensibility. The manual for the most widely used variant, GNU Emacs, describes it as the extensible, customizable, self-documenting, real-time display editor.

Development of the first Emacs began in the mid-1970s, and work on its direct descendant, GNU Emacs, continues actively as of 2017.

### Installation

There are many Emacs clients on macOS. The recommended version on macOS is Emacs Mac Port, but others are good as well.

#### [Emacs Mac port](https://bitbucket.org/mituharu/emacs-mac/overview) (Recommended)

Many useful features are built with Emacs Mac Port, e.g. environment variables, full screen, visual enhancements and so on.

Link the Homebrew tap first.

```
brew tap railwaycat/emacsmacport
```

- Method 1: Install with `brew cask`.

```
brew install --cask emacs-mac
```

There are three available versions, `emacs-mac`, `emacs-mac-official-icon`, `emacs-mac-spacemacs-icon`.

- Method 2: Install using `brew`.

```
brew install emacs-mac [options]
```
  
#### [Emacs plus](https://github.com/d12frosted/homebrew-emacs-plus#emacs-plus)

Start off by tapping the official emacs-plus cask.

```
brew tap d12frosted/emacs-plus
```

Emacs Plus contains separate formulas for different Emacs versions:

- emacs-plus - installs Emacs 26, current release version.

```
brew install emacs-plus [options]
```

- emacs-plus@27 - installs Emacs 27, next release version.

```
brew install emacs-plus@27 [options]
```

- emacs-plus@28 - installs Emacs 28, development version.

```
brew install emacs-plus@28 [options]
```

Click here to see available options:  
  
> **Note**: 1) You might want to install [exec-path-from-shell](https://github.com/purcell/exec-path-from-shell) if you are using Emacs plus. It takes care of your environment variables. 2) To have the title bar match your theme background color, consider using instead: `brew install emacs-plus --HEAD --with-natural-title-bars`

### Spacemacs

[Spacemacs](https://github.com/syl20bnr/spacemacs/blob/master/README.md) is a new way to experience Emacs -- a sophisticated and polished set-up focused on ergonomics, mnemonics and consistency.

Spacemacs can be used naturally by both Emacs and Vim users -- you can even mix the two editing styles. Switching easily between input styles makes Spacemacs a great tool for pair-programming.

#### Installation

1. If you have an existing Emacs configuration, back it up first:
    
    ```
    cd ~
    mv .emacs.d .emacs.d.bak
    mv .emacs .emacs.bak
    ```
    
    Don't forget to backup and _remove_ `~/.emacs` file otherwise Spacemacs **WILL NOT** load since that file prevents Emacs from loading the proper initialization file.
    
2. Clone the repository:
    
    ```
    git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
    ```
    
    `master` is the stable branch and it is _immutable_, **DO NOT** make any modification to it or you will break the update mechanism. If you want to fork Spacemacs safely use the `develop` branch where you handle the update manually.
    
3. (Optional) Install the [Source Code Pro](https://github.com/adobe-fonts/source-code-pro) font.
    
    If you are running in terminal you'll also need to change font settings of your terminal.
    
4. Launch Emacs. Spacemacs will automatically install the packages it requires. If you get an error regarding package downloads then you may try to disable the HTTPS protocol by starting Emacs with
    
    ```
    emacs --insecure
    ```
    
    Or you can set the `dotspacemacs-elpa-https` to `nil` in your dotfile to remove the need to start Emacs with `--insecure` argument. You may wish to clear out your `.emacs.d/elpa` directory before doing this, so that any corrupted packages you may have downloaded will be re-installed.
    
5. Restart Emacs to complete the installation.


You can learn more on [Spacemacs Tutorial Video](https://www.youtube.com/watch?v=hCNOB5jjtmc&list=PLhqJJNjsQ7KFkMVBunWWzFD8SlH714qm4)

## Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/) is a lightweight code editor with support for many programming languages through [extensions](https://code.visualstudio.com/docs/editor/extension-gallery)

### Installation

To install the latest version, use Homebrew:

```
brew install --cask visual-studio-code
```

### macOS integration

Launch VS Code from the [command line](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).

After that, you can launch VS Code from your terminal:

- `code .` will open VS Code in the current directory
- `code myfile.txt` will open `myfile.txt` in VS Code

### Useful Extensions

#### Python

- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - Python code highlighting
    
    To enable auto-formatting on "Save", i.e. `⌘ + S`, configure the following:
    
    1. Change the default formatter to `Black` instead of `Autopep8`. Critical to avoid large diffs. Go to _Preferences_ -> _User Settings_ and update the setting `python.formatter.provider` to `Black`
        
    2. Enable `Format on Save` Setting: _Editor: Format On Save_ setting on _Code_ -> _Preferences_ -> _Settings_
        

#### JavaScript

- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) - Useful to check JavaScript errors and helps in auto-formatting the code
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) - JavaScript code formatter

#### SQL

- [PostgreSQL formatter](https://marketplace.visualstudio.com/items?itemName=bradymholt.pgformatter)

#### Markdown

- [Markdown Preview](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced) - Read Markdown files in VSCode

#### GitLens

- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) - Supercharge the Git capabilities built into VSCode

#### Docker

- [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) - Create, manage, and debug images from within VSCode

#### JSON

- [Paste JSON as Code](https://marketplace.visualstudio.com/items?itemName=quicktype.quicktype) - Infers types from sample JSON data, then outputs strongly typed models and serializers for working with that data in your desired programming language

#### Live Server

- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) - Launches a local development server with live reloading for both static and dynamic

#### VS Code Icons

- [vscode-icons](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons) - Adds unique icons to distinguish different file extensions (easier to glance through your directories)

### Configuration of C++ and some commonly used language

reference
- mainly copied from [Yunfi's Blog](https://yfi.moe/post/vscode-clang-clangd/)

本文主要应用场景是**单文件的编译**。如果使用 CMake 等工具，则本文中的一部分配置并不一定兼容。

主要分为两步操作，使用 clang/lldb 编译和调试，以及使用 clangd 进行补全和检查，这两者应该是互相独立的，可以只使用其中一个，但是找到的大多数教程好像都是两个混在一起搞得。

本文的配置**不使用 C/C++ 插件 和 Code Runner 插件**！！请禁用或者卸载它们。由于 VSCode 和 C/C++ 插件的一些 bug，我选择绕开它们，使用 CodeLLDB 和 Clangd 来替代。

>我的环境：MacOS Sonoma 14.3

#### 使用 clang/lldb 进行单文件编译和调试

1. 确保 `clang++` 已经正确安装（通过 `clang++ -v` 可以验证）
    
    - 对于 macOS，运行 `xcode-select --install` 可以安装好本文用到的所有包
    - 对于 Linux，下载 llvm 包，大概率包含了本文用到的所有包
2. vscode 已启用 CodeLLDB 插件（报错无法下载可以先按报错给的 url 用浏览器下载，然后手动安装）
    
3. **卸载微软提供的 C/C++ 插件！！！也不要使用 Code Runner 插件。**
    
4. tasks.json，放入.vscode 文件夹中

```bash
{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "shell",
      "label": "C/C++: clang++ build active file",
      "command": "/usr/bin/clang++", // `which clang++` may help you find this path
      "args": [
        "--std=c++17",
        "-fcolor-diagnostics",
        "-fansi-escape-codes",
        "-g",
        "${file}",
        "-o",
        "${workspaceFolder}/.build/${fileBasenameNoExtension}"
        "-fstandalone-debug", // to enable viewing std::string etc. when using lldb on Windows or Linux 
      ],
      "options": {
        "cwd": "${fileDirname}"
      },
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "detail": "Task generated by Debugger."
    }
  ]
}
```

>我的习惯是把所有的可执行文件放到 `./build/` 文件夹下，如果不这么做的话，改变 3、4 步中的文件路径，以及忽略第五步

5. launch.json，放入.vscode 文件夹中

```bash
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "C/C++: clang++ build and debug active file customize",
      "type": "lldb",
      "request": "launch",
      "program": "${workspaceFolder}/.build/${fileBasenameNoExtension}",
      "args": [],
      "cwd": "${workspaceFolder}",
      "preLaunchTask": "C/C++: clang++ build active file"
    }
  ]
}

```

6. 在文件夹里新建一个 .build 文件夹（ macOS / Linux 必做）
    
7. 按 F5，就可以编译调试了( fn + F5 )
    

> 这样的配置下，右上角不会有运行的那个小按钮。由于未知问题，这个又 C/C++ 插件提供的按钮不会同步 tasks.json 和 launch.json 中的配置，所以放弃使用了那个插件。

#### 使用 clangd 自动补全、代码检查

1. 确保已安装 clangd（应该和 clang++ 在一个包里的，通过 `clangd --version` 检查）
    
2. 安装 VScode 插件 clangd
    
3. 在工作区根目录下新建一个 `compile_flags.txt`，这是用来为 clangd 指定参数的，比如使用的标准或是标准库路径之类。内容就是编译选项，一行一个。这里只写了一个标准作为例子
    
    ```
    --std=c++17
    ```
    

> 一般来说 clangd 的参数是由 compile_commands.json 指定，由 CMake 等构建工具自动生成。但是由于在我的需求中对每一个文件都是相同的编译参数，所以可以手写 compile_flags.txt 统一管理。 具体查看 [JSON Compilation Database Format Specification](https://clang.llvm.org/docs/JSONCompilationDatabase.html#alternatives)

#### 关于 .clang-format 文件

我的习惯是直接放在 `~` 下（如果你的代码都放在你的~和其子文件夹里的话）

生成的话，官方文档的那个网页实在是太丑了，我直接选择去 CLion 里配好，然后导出为 .clang-format，既可视化又方便

贴一下我的.clang-format

```
# Generated from CLion C/C++ Code Style settings
BasedOnStyle: LLVM
AccessModifierOffset: -4
AlignAfterOpenBracket: Align
AlignConsecutiveAssignments: None
AlignOperands: Align
AllowAllArgumentsOnNextLine: false
AllowAllConstructorInitializersOnNextLine: false
AllowAllParametersOfDeclarationOnNextLine: false
AllowShortBlocksOnASingleLine: Always
AllowShortCaseLabelsOnASingleLine: false
AllowShortFunctionsOnASingleLine: All
AllowShortIfStatementsOnASingleLine: Always
AllowShortLambdasOnASingleLine: All
AllowShortLoopsOnASingleLine: true
AlwaysBreakAfterReturnType: None
AlwaysBreakTemplateDeclarations: Yes
BreakBeforeBraces: Custom
BraceWrapping:
  AfterCaseLabel: false
  AfterClass: false
  AfterControlStatement: Never
  AfterEnum: false
  AfterFunction: false
  AfterNamespace: false
  AfterUnion: false
  BeforeCatch: false
  BeforeElse: false
  IndentBraces: false
  SplitEmptyFunction: false
  SplitEmptyRecord: true
BreakBeforeBinaryOperators: None
BreakBeforeTernaryOperators: true
BreakConstructorInitializers: BeforeColon
BreakInheritanceList: BeforeColon
ColumnLimit: 0
CompactNamespaces: false
ContinuationIndentWidth: 8
IndentCaseLabels: true
IndentPPDirectives: None
IndentWidth: 4
KeepEmptyLinesAtTheStartOfBlocks: true
MaxEmptyLinesToKeep: 2
NamespaceIndentation: All
ObjCSpaceAfterProperty: false
ObjCSpaceBeforeProtocolList: true
PointerAlignment: Right
ReflowComments: false
SpaceAfterCStyleCast: true
SpaceAfterLogicalNot: false
SpaceAfterTemplateKeyword: false
SpaceBeforeAssignmentOperators: true
SpaceBeforeCpp11BracedList: false
SpaceBeforeCtorInitializerColon: true
SpaceBeforeInheritanceColon: true
SpaceBeforeParens: ControlStatements
SpaceBeforeRangeBasedForLoopColon: false
SpaceInEmptyParentheses: false
SpacesBeforeTrailingComments: 0
SpacesInAngles: false
SpacesInCStyleCastParentheses: false
SpacesInContainerLiterals: false
SpacesInParentheses: false
SpacesInSquareBrackets: false
TabWidth: 4
UseTab: Never
```

### 故障排除

#### macOS 无法使用集成终端调试

- 具体表现为在 `enternalConsole` 为 false 的时候并不会像在 Windows 中一样出现一个新的集成终端用来输入，导致没有地方输入从而无法调试。
- 这种情况出现于使用了微软提供的 C/C++ 插件，并且 `launch.json` 中 type 为 “cppdbg” 时。这是 VSCode 的 bug，微软文档提供了一种解决方案，但是实测没效果（）
- 解决方案一是将 `enternalConsole` 设为 true，如果接受使用外部终端进行调试的话；
- 解决方案二是不用微软提供的插件，而是使用 `CodeLLDB` 插件提供的调试选项。也就是按照本文进行操作

> 吐槽：VSCode 的 bug 还真不少，在 Windows 上外部终端用不了，Mac 上却又只能用外部终端（）

#### VSCode 在 WSL 中无法正确联网

- 主要原因是 vscode 会在 wsl 中使用在 Windows 下的代理 ip+ 端口（一般是 `127.0.0.1:端口` ），
- 解决方案一：给 WSL 设置 http_proxy 和 https_proxy，把 127.0.0.1 改成局域网下 windows 的 ip
- 解决方案二：关闭系统代理，直接使用 TUN /增强模式

### 懒人直通车(一键配置)
[reference](https://yfi.moe/post/vsc-cpp-speedrun/)

两个脚本，分别VSCode在 Linux 和 Windows 下的一键脚本，轻松配出环境

