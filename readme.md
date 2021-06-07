# 你不需要的图形界面

[![社区](https://withspectrum.github.io/badge/badge.svg)](https://spectrum.chat/you-dont-need/GUI)

<details>
开箱即用,有手就行 :)
</details>
<br />
用户图形界面是极其友好的,引入他们可以减小队命令行陡峭学习曲线的感知.

![Xerox Star 8010 workstations](./Xerox_Star_8010_workstations.jpg)

然而, 他们经常需要更多的资源,功能较弱且难以通过脚本实现自动化.
我们知道命令词可能不是那么被记住,所以我们列出以下在图形界面常用的命令.

## 快速跳转
  - [复制文件](#copy-a-file)
  - [duplicate a file](#duplicate-a-file)
  - [copy a directory](#copy-a-directory)
  - [duplicate a directory](#duplicate-a-directory)
  - [move a file](#move-a-file)
  - [rename a file](#rename-a-file)
  - [move a directory](#move-a-directory)
  - [rename a directory](#rename-a-directory)
  - [merge directories](#merge-directories)
  - [create a new file](#create-a-new-file)
  - [create a new directory](#create-a-new-directory)
  - [show file/directory size](#show-filedirectory-size)
  - [show file/directory info](#show-filedirectory-info)
  - [open a file with the default program](#open-a-file-with-the-default-program)
  - [zip a directory](#zip-a-directory)
  - [unzip a directory](#unzip-a-directory)
  - [peek files in a zip file](#peek-files-in-a-zip-file)
  - [remove a file](#remove-a-file)
  - [remove a directory](#remove-a-directory)
  - [list directory contents](#list-directory-contents)
  - [tree view a directory and its subdirectories](#tree-view-a-directory-and-its-subdirectories)
  - [find a stale file](#find-a-stale-file)
  - [show a calendar](#show-a-calendar)
  - [find a future date](#find-a-future-date)
  - [use a calculator](#use-a-calculator)
  - [force quit a program](#force-quit-a-program)
  - [check server response](#check-server-response)
  - [view content of a file](#view-content-of-a-file)
  - [search for a text](#search-for-a-text)
  - [view an image](#view-an-image)
  - [show disk size](#show-disk-size)
  - [check performance of your computer](#check-performance-of-your-computer)
  - [Quick tips](#quick-tips)
  - [Hotkeys](#hotkeys)
  - [I can't remember these cryptic commands](#i-cant-remember-these-cryptic-commands)


## 复制文件

**别再拖拽或Ctrl C了** :-1:

拷贝文件 `readme.txt` 到 `documents` 目录下

```shell
$ cp readme.txt documents/
```

## 复制文件

**停止使用右键复制粘贴** :-1:

```shell
$ cp readme.txt readme.bak.txt
```
更强的功能:
```shell
$ cp readme{,.bak}.txt
# Note: learn how the {} works with touch foo{1,2,3}.txt and see what happens.
```

## 复制文件夹

**请立刻停止你的右键复制行为** :-1:

复制 `myMusic` 文件夹 到 `myMedia` 目录下

```shell
$ cp -a myMusic myMedia/
# or
$ cp -a myMusic/ myMedia/myMusic/
```

## duplicate a directory

将`myMusic` 下的所有文件复制到`myMedia`目录下
```shell
$ cp -a myMusic/ myMedia/
# or if `myMedia` folder doesn't exist
$ cp -a myMusic myMedia/
```

## 移动文件


```shell
$ mv readme.txt documents/
```

**切记** 使用'/' 结尾, [for this reason](http://unix.stackexchange.com/a/50533).

## 重命名


```shell
$ mv readme.txt README.md
```

## 移动文件

```shell
$ mv myMedia myMusic/
# or
$ mv myMedia/ myMusic/myMedia
```

## 重命名文件夹

```shell
$ mv myMedia/ myMusic/
```

## 合并目录

```shell
$ rsync -a /images/ /images2/	# note: may over-write files with the same name, so be careful!
```

## 创建文件


```shell
$ touch 'new file'    # updates the file's access and modification timestamp if it already exists
# or
$ > 'new file'        # note: erases the content if it already exists
```

## 创建文件夹


```shell
$ mkdir 'untitled folder'
# or
$ mkdir -p 'path/may/not/exist/untitled\ folder'
# -p 指定创建路径,如果没有路径则会创建路径
```

## 查看文件或文件夹大小


```shell
$ du -sh node_modules/
```

## 查看文件或文件夹信息

```shell
$ stat -x readme.md   # on macOS
$ stat readme.md      # on Linux
```

## 使用默认程序打开文件或文件夹

```shell
$ open file       # on MacOS
```

## 压缩文件夹

```shell
$ zip -r archive_name.zip folder_to_compress
```

## 解压

```shell
$ unzip archive_name.zip
```
## 删除文件

**STOP RIGHT CLICKING AND DELETE A FILE PERMANENTLY** :-1:

```shell
$ rm my_useless_file
```

IMPORTANT: 永久性删除.

## 删除文件夹

```shell
$ rm -r my_useless_folder
```

## 查看文件夹内容

```shell
$ ls my_folder        # Simple
$ ls -la my_folder    # -l: show in list format. -a: show all files, including hidden. -la combines those options.
$ ls -alrth my_folder # -r: reverse output. -t: sort by time (modified). -h: output human-readable sizes.
```

## 使用树形结构查看目录

**STOP OPENING YOUR FINDER OR FILE EXPLORER** :-1:

```shell
$ tree                                                        # on Linux
$ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'      # on MacOS
# Note: install homebrew (https://brew.sh) to be able to use (some) Linux utilities such as tree.
# brew install tree
```

## find a stale file


Find all files modified more than 5 days ago
****
```shell
$ find my_folder -mtime +5
```

## 展示日历

展示一个日志

```shell
$ cal
```
展示指定年月

```shell
$ cal 11 2018
```

## find a future date

**STOP USING WEBAPPS TO CALCULATE FUTURE DATES** :-1:

What is todays date?

```shell
$ date +%m/%d/%Y
```

What about a week from now?

```shell
$ date -d "+7 days"                                           # on Linux
$ date -j -v+7d                                               # on MacOS
```

## 展示一个计算器

```shell
$ bc
```

## 强制退出程序


```shell
$ killall program_name
```

## check server response

**STOP OPENING A BROWSER** :-1:

```shell
curl -i umair.surge.sh
# curl's -i (--include) option includes HTTP response headers in its output.
```

## 查看文件内容

**STOP DOUBLE CLICKING A FILE** :-1:

```shell
$ cat apps/settings.py
# 如果文件太大,可以用 'pager' (less) ,一次性展示.
$ less apps/settings.py
```

## 文件内搜索

```shell
$ grep -i "Query" file.txt
```

## 查看一张图片

**STOP USING PREVIEW** :-1:

```shell
$ imgcat image.png
# Note: requires iTerm2 terminal.
```

## 查看磁盘大小

```shell
$ df -h
```

## 查看任务占用情况

```shell
$ top
```

## Quick tips

![CLI tips](./cli_tips.jpg)

## Hotkeys

```
 Ctrl + A  Go to the beginning of the line you are currently typing on
Ctrl + E  Go to the end of the line you are currently typing on
Ctrl + L  Clears the Screen, similar to the clear command
Ctrl + U  Clears the line before the cursor position. If you are at the end of the line, clears the entire line.
Ctrl + H  Same as backspace
Ctrl + R  Lets you search through previously used commands
Ctrl + C  Kill whatever you are running
Ctrl + D  Exit the current shell
Ctrl + Z  Puts whatever you are running into a suspended background process. fg restores it.
Ctrl + W  Delete the word before the cursor
Ctrl + K  Clear the line after the cursor
Ctrl + T  Swap the last two characters before the cursor
Esc + T   Swap the last two words before the cursor
Alt + F   Move cursor forward one word on the current line
Alt + B   Move cursor backward one word on the current line
Tab       Auto-complete files and directory names
```

