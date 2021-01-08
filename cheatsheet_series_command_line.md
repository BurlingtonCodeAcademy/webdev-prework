# Command Line Structure

When working as a programmer, many tools and services offer a CLI (command line interface) that allow you to quickly integrate them into your work flow without having to include the additional cruft, like additional applications or web services. Moreso, consolidating everything to the command line will save you time and headaches. These CLIs can be invoked just as you would any native commands on your computer; through the command line! Below is a general breakdown of the anatomy of potential command inputs, as well as some of the most common (native) commands.

## The Prompt

The prompt is what you see before any commands are input by the user. Depending on the operating system, it provides various additional information, like the current user or directory.

### On Windows, it displays the current directory:
```
C:\Users\admin
```

### On Linux and Mac, you might see something like this:
```
admin@LAPTOP-JULHSBL9:~$```
```
Which follows the pattern:
```
[user]@[host]:[directory]$
```

The prompt will often be represented in doccumentation as the `$` character, as other information is specific to your particular environment.

## The CLI Output

The display is the text output the command line presents to a user after an input has been provided. It is often referred to as `STDOUT` (standard output) and is the default channel in which information is presented after a user's input. 

For example, when a user enters `pwd` as a command, it will print the name of the current directory:
```
$ pwd
C:\Users\admin
```

## Input

The input is the text entered by the user to get a desired result. There are three aspects to the input. They are, broadly speaking, **command, option, and argument**

### Commands

The command is the actual behavior you will be dealing with. Think of this as the "verb" of your input. `pwd`, for example, stands for "print working directory". It is the desired action, which informs what the result will be. **This is required to perform your command line action.** There are many commands used for a variety of purposes, like deleting files and making new directories. Common commands are found at the end of this document.

```
$ pwd
C:\Users\admin
```

#### **A Note on CLIs**
When a program offers a CLI (command line interface) you can incorporate that into your available list of commands. If you download the Heroku CLI, for example, you can access the specific commands and behaviors it offers by adding `heroku` before the desired command. 

In this example, `status` is the command called through the `heroku` CLI. 

```
$ heroku status
Apps:      No known issues at this time.
Data:      No known issues at this time.
Tools:     No known issues at this time.
```

### Options
Options are additional bits of information you may include in your input to further inform the desired behavior. They are context specific, in that certain options are only available to certain commands. Let's take the *list* command, represented as `ls`. When entered as a command on its own, it lists all visible files or directories in the current working directory:

```
$ ls
assets/  index.html  node_modules/  package.json  package-lock.json  style.css  test.js
```

But `ls` has many available options, too. Enter `--help` as an option to see a full list of other options available to the `ls` command:

```
$ ls --help
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
      --block-size=SIZE      with -l, scale sizes by SIZE when printing them;
                               e.g., '--block-size=M'; see SIZE format below
  -B, --ignore-backups       do not list implied entries ending with ~
  -c                         with -lt: sort by, and show, ctime (time of last
                               modification of file status information);
                               with -l: show ctime and sort by name;
                               otherwise: sort by ctime, newest first
  -C                         list entries by columns
      --color[=WHEN]         colorize the output; WHEN can be 'always' (default
                               if omitted), 'auto', or 'never'; more info below
  -d, --directory            list directories themselves, not their contents
  -D, --dired                generate output designed for Emacs' dired mode
  -f                         do not sort, enable -aU, disable -ls --color
  -F, --classify             append indicator (one of */=>@|) to entries
      --file-type            likewise, except do not append '*'
      --format=WORD          across -x, commas -m, horizontal -x, long -l,
                               single-column -1, verbose -l, vertical -C
      --full-time            like -l --time-style=full-iso
  -g                         like -l, but do not list owner
      --group-directories-first
                             group directories before files;
                               can be augmented with a --sort option, but any
                               use of --sort=none (-U) disables grouping
  -G, --no-group             in a long listing, don't print group names
  -h, --human-readable       with -l and -s, print sizes like 1K 234M 2G etc.
      --si                   likewise, but use powers of 1000 not 1024
  -H, --dereference-command-line
                             follow symbolic links listed on the command line
      --dereference-command-line-symlink-to-dir
                             follow each command line symbolic link
                               that points to a directory
      --hide=PATTERN         do not list implied entries matching shell PATTERN
                               (overridden by -a or -A)
      --hyperlink[=WHEN]     hyperlink file names; WHEN can be 'always'
                               (default if omitted), 'auto', or 'never'
      --indicator-style=WORD  append indicator with style WORD to entry names:
                               none (default), slash (-p),
                               file-type (--file-type), classify (-F)
  -i, --inode                print the index number of each file
  -I, --ignore=PATTERN       do not list implied entries matching shell PATTERN
  -k, --kibibytes            default to 1024-byte blocks for disk usage;
                               used only with -s and per directory totals
  -l                         use a long listing format
  -L, --dereference          when showing file information for a symbolic
                               link, show information for the file the link
                               references rather than for the link itself
  -m                         fill width with a comma separated list of entries
  -n, --numeric-uid-gid      like -l, but list numeric user and group IDs
  -N, --literal              print entry names without quoting
  -o                         like -l, but do not list group information
  -p, --indicator-style=slash
                             append / indicator to directories
  -q, --hide-control-chars   print ? instead of nongraphic characters
      --show-control-chars   show nongraphic characters as-is (the default,
                               unless program is 'ls' and output is a terminal)
  -Q, --quote-name           enclose entry names in double quotes
      --quoting-style=WORD   use quoting style WORD for entry names:
                               literal, locale, shell, shell-always,
                               shell-escape, shell-escape-always, c, escape
                               (overrides QUOTING_STYLE environment variable)
  -r, --reverse              reverse order while sorting
  -R, --recursive            list subdirectories recursively
  -s, --size                 print the allocated size of each file, in blocks
  -S                         sort by file size, largest first
      --sort=WORD            sort by WORD instead of name: none (-U), size (-S),
                               time (-t), version (-v), extension (-X)
      --time=WORD            with -l, show time as WORD instead of default
                               modification time: atime or access or use (-u);
                               ctime or status (-c); also use specified time
                               as sort key if --sort=time (newest first)
      --time-style=TIME_STYLE  time/date format with -l; see TIME_STYLE below
  -t                         sort by modification time, newest first
  -T, --tabsize=COLS         assume tab stops at each COLS instead of 8
  -u                         with -lt: sort by, and show, access time;
                               with -l: show access time and sort by name;
                               otherwise: sort by access time, newest first
  -U                         do not sort; list entries in directory order
  -v                         natural sort of (version) numbers within text
  -w, --width=COLS           set output width to COLS.  0 means no limit
  -x                         list entries by lines instead of by columns
  -X                         sort alphabetically by entry extension
  -Z, --context              print any security context of each file
  -1                         list one file per line.  Avoid '\n' with -q or -b
      --append-exe           append .exe if cygwin magic was needed
      --help     display this help and exit
      --version  output version information and exit

```

Using this helpful chart (you can reference any time with `--help`), we can see that `-a` is an option that displays files that do not have their own name, but rather an extension only.

```
$ ls
./   .prettierrc  index.html     package.json       style.css
../  assets/      node_modules/  package-lock.json  test.js
```
This reveals otherwise hidden configuration files!

`--help` is a common option available to MOST commands and CLIs. It is a good reference to have on hand.

### Arguments

Arguments follow options and further inform the command's behavior by providing specific information to the command for its use. They provide concrete information, like file names and passwords, that allow the command to do its thing. Arguments always come after options, unless no options are required, in which case they follow the command. 

For example, the common `echo` command simply prints whatever argument(s) follow it, including whitespace. In this case, there are no options included with the command, so they can be appended immediately after the command:

```
$ echo Hello World!
Hello World!
```

## Common Commands
Commands can be specific to particular operating systems, and as such there is no one answer. However, there are a number of common commands you can familiarize yourself with.

<table>

<th>Command</th>
<th>Purpose</th>
<th>Example</th>

<tr>
<td>cd [directory_name]</td>
<td>changes current directory to provided argument, should it exist within the current one. Can provide full path to navigate directly.</td>
<td>cd Downloads/</td>
</tr>
<tr>
<td>cd ..</td>
<td>Moves current directory up to parent directory.</td>
<td>C:\Users\John => C:\users\</td>
</tr>
<tr>
<td>mkdir [new_directory]</td>
<td>Creates a new directory inside the current one with the given argument as its name.</td>
<td>mkdir my_directory</td>
</tr>
<tr>
<td>mkdir [new_directory]</td>
<td>Creates a new directory inside the current one with the given argument as its name.</td>
<td>mkdir my_directory</td>
</tr>
<tr>
<td>ls</td>
<td>prints a list of all directories and files in the working directory</td>
<td></td>
</tr>
<tr>
<td>mv [file] [path]</td>
<td>Moves the targeted source file into the provided destination path.</td>
<td>mv my_memoir.txt published/</td>
</tr>
<tr>
<td>pwd</td>
<td>prints the current (working) directory</td>
<td></td>
</tr>
<tr>
<td>rm [file]</td>
<td>deletes the file in the current directory with the name matching the provided argument.</td>
<td>rm first_draft.doc</td>
</tr>
<tr>
<td>rm [file]</td>
<td>deletes the file in the current directory with the name matching the provided argument. Options inform what is deleted, and how.</td>
<td>rm first_draft.doc</td>
</tr>
<tr>
<td>PATH</td>
<td>Returns a list of semi-colon separated directories that contain scripts for the command line to execute. This is where your CLI variables will often live.</td>
<td>rm first_draft.doc</td>
</tr>
</table>
