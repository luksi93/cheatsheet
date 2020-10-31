# cheat-sheets

- [ExifTool](#ExifTool)
- [Git](#Git)
- [Shell scripting](#Shell-scripting)

## ExifTool

### Renaming picture files based on creation date

The first command only displays a preview of how the files will be renamed. The second one actually renames the files.
The files will be renamed to `IMG-YYYYMMDD-HHMMSS-CC.EXT` with CC being an incrementing counter and EXT the original file extension.

```
exiftool -fileOrder createdate -d IMG-%Y%m%d-%H%M%S%%-2.c.%%e "-testname<CreateDate" path/to/folder_or_file
exiftool -fileOrder createdate -d IMG-%Y%m%d-%H%M%S%%-2.c.%%e "-filename<CreateDate" path/to/folder_or_file
```

## Git

## Shell scripting

### Ask for confirmation

```
read -q "REPLY?Do you want to ... ?"
if [[ $REPLY =~ ^[Yy]$ ]] then ... fi
```

### Shell script control flow 

This part is 'forked' from [ffraenz/cheatsheet](https://github.com/ffraenz/cheatsheet)

| Description                                    | Structure                          |
| ---------------------------------------------- | ---------------------------------- |
| String `$a` equals `$b`                        | `if [ $a = $b ]; then ... fi`      |
| String `$a` does not equal `$b`                | `if [ $a != $b ]; then ... fi`     |
| `$string` is empty `-z` / not empty `-n`       | `if [ -z $string ]; then ... fi`   |
| `$path` exists                                 | `if [ -e $path ]; then ... fi`     |
| `$path` is a file `-f` / directory `-d`        | `if [ -f $path ]; then ... fi`     |
| `$path` is readable `-r` / `-w` / `-x` by user | `if [ -r $path ]; then ... fi`     |
| `$a` is newer `-nt` / older `-ot` than `$b`    | `if [ $a -nt $b ]; then ... fi`    |
| For loop over values                           | `for i in 1 2 3 4 5; do ... done`  |
| For loop over files                            | `for PATH in /foo/*; do ... done`  |
| For loop over directories                      | `for PATH in /foo/*/; do ... done` |
| While loop                                     | `while [ condition ]; do ... done` |


