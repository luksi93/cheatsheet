# cheatsheet

- [ExifTool](#ExifTool)
- [Git](#Git)
- [iTerm](#iTerm)
- [Shell scripting](#Shell-scripting)

## ExifTool

### Renaming picture files based on creation date

The first command only displays a preview of how the files will be renamed. The second one actually renames the files.
The files will be renamed to `IMG-YYYYMMDD-HHMMss-CC.ext` with CC being an incrementing counter and ext the original file extension in lowercase.

```
exiftool -fileOrder createdate -d IMG-%Y%m%d-%H%M%S%%-2.c.%%le "-testname<CreateDate" path/to/folder_or_file
exiftool -fileOrder createdate -d IMG-%Y%m%d-%H%M%S%%-2.c.%%le "-filename<CreateDate" path/to/folder_or_file
```
CMD I currently use:
```
exiftool "-FileName<CreateDate" -d %Y-%m-%d_Location_Description_%%4.c.%%ue -fileOrder CreateDate path/to/folder_or_file
```

### Moving .nef files that do not have a corresponding .jpg file in the current directory

After downloading pictures from the camera I usually go through the jpgs and remove the ones I don't like. This command makes life a lot easier to also get rid of the corresponding raw files.

```
exiftool -ext nef -directory=deleted -tagsfromfile %d%f.jpg -directory .
```

## Git

### Show the git config (global and local if in a repo). It also shows from where each property comes.

```git config --list --show-origin```

### Useful commands for investigating project history

```git shortlog -e -n -s [path]``` prints the list of contributors in the specified [path] ordered by number of contributions.

```git effort --above [number]``` will print the files affected for a number of commits greater than [number] ([Part of git-extras](https://github.com/tj/git-extras)).

```git blame [file]``` will output the [file] content alongside with author for a particular line, and commit hash for the same line.

```git grep [regexp]``` will print the lines in all the tracked files where the regexp is present.

```git log -G [regexp]``` will output the commits where [regexp] is present on the diff associated to the commit.

```git log --follow -- filename``` will output the history of a particular file.

```git log [--since=date] [--until=date]``` Well, this is self-explanatory.

```git diff-tree --no-commit-id --name-status -r [commit id]``` Shows the files that were affected by the given commit.

## iTerm

### Shortcuts

| Description                                    | Shortcut                             |
| ---------------------------------------------- | ------------------------------------ |
| Close current pane                             | `⌘ Cmd` + `w`                        |
| Close current window with all panes            | `⌘ Cmd` + `⇧ Shift` + `w`            |
| Split pane                                     | `⌘ Cmd` + `d`                        |
| Split pane horizontally                        | `⌘ Cmd` + `⇧ Shift` + `d`            |
| Resize pane                                    | `⌘ Cmd` + `⌃ Ctrl` + `arrow key`     |
| Switch pane                                    | `⌘ Cmd` + `⌥ Option` + `arrow key`   |
| Maximize pane                                  | `⌘ Cmd` + `⇧ Shift` + `↵ return key` |

## Shell scripting

See [shell scripting cheatsheet](https://github.com/luksi93/cheatsheet/blob/master/SHELL_SCRIPTING.md)


