## Shell scripting

### Return codes

```echo $?``` echos the last return code (RC)

### Control operators example

If command1 exits with a return code of 0, then execute command2, otherwise execute command3: 
```
command1 && command2 || command3 ;
```

### Logical operators

```
if [ arg1 operator arg2 ]
  then 
  command1
elif [ arg1 operator arg2 ]
  then
  command2
else 
  command3
fi
```

### String comparison operators

| Operator                                    | Description                                            |
| --------------------------------------------| ------------------------------------------------------ |
| `-z string`                                 | True if the length of string is zero                   |
| `-n string`                                 | True if the length of string is non-zero               |
| `string1 = string2` or `string1 == string2` | True if the strings are equal (1 `=` for POSIX)        |
| `string1 != string2`                        | True if the strings are not equal                      |
| `string1 < string2`                         | True if string1 sorts before string2 lexicographically |
| `string1 > string2`                         | True if string1 sorts after string2 lexicographically  |

### Numeric comparison operators

| Operator         | Description                                           |
| -----------------| ----------------------------------------------------- |
| `arg1 -eq arg2`  | True if arg1 equals arg2                              |
| `arg1 -ne arg2`  | True if arg1 is not equal to arg2                     |
| `arg1 -lt arg2`  | True if arg1 is less than arg2                        |
| `arg1 -le arg2`  | True if arg1 is less than or equal to arg2            |
| `arg1 -gt arg2`  | True if arg1 is greater than arg2                     |
| `arg1 -ge arg2`  | True if True if arg1 is greater than or equal to arg2 |

### Loops syntax

The below will print the numbers from 1 to 9 each on a new line.

```
for counter in 1 2 3 4 5 6 7 8 9 ; do echo $counter ; done
```

While and until loops syntax: 
```
while [ expression ] ; do command1 ; done
until [ expression ] ; do command1 ; done
```

While iterates as long as the expression is true. Until itterates until the expression evaluates to true.

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
