# cheat-sheets
- [exiftool](https://github.com/luksi93/cheat-sheets/blob/master/README.md#renaming-files-based-on-creation-date)
## exiftool
### Renaming files based on creation date
> exiftool -fileOrder createdate -d MKF-%Y%m%d-%H%M%S%%-2.c.%%e "-filename<CreateDate" path/to/folder_or_file
