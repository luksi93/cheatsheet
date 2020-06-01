# cheat-sheets
- [exiftool](https://github.com/luksi93/cheat-sheets/blob/master/README.md#exiftool)
- [Git](https://github.com/luksi93/cheat-sheets/blob/master/README.md#Git)
## exiftool
### Renaming files based on creation date
The first command only displays a preview of how the files will be renamed. The second one actually renames the files.
The files will be renamed to `IMG-YYYYMMDD-HHMMSS-CC.EXT` with CC being an incrementing counter and EXT the original file extension.
```
exiftool -fileOrder createdate -d IMG-%Y%m%d-%H%M%S%%-2.c.%%e "-testname<CreateDate" path/to/folder_or_file
exiftool -fileOrder createdate -d IMG-%Y%m%d-%H%M%S%%-2.c.%%e "-filename<CreateDate" path/to/folder_or_file
```
## Git
