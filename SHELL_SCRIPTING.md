## Shell scripting

### Return codes

```echo $?``` echos the last return code (RC)

### Control operators example

If command1 exits with a return code of 0, then execute command2, otherwise execute command3: 
```
command1 && command2 || command3 ;
```

### Ask for confirmation

```
read -p REPLY -n 1 -r
if [[ $REPLY =~ ^[Yy]$ ]] then ... fi
```

### Always return the absolute path to the directory the script is located

```
echo $(cd `dirname $0` && pwd)
```
Note that although the change directory command (cd) is used, the script will not change directory and any other calls within it are still relative to the current working directory.

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
