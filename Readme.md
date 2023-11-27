# File permissions in Linux

## Project Description

In this project, we have a directory that contains various text files and various levels of write, read, and execute permissions. The practice has demonstrated the use of various Linux commands and understanding the permission string of `drwxrwxrwx`. To get a better understanding of the string, we will exhibit commands that use all three levels of the directory listing, with the user, group, and other.

## Check file and directory details

We’ve started with changing directories from `/home/researcher2/` to `/home/researcher2/projects/`.

Afterwards, we use the `ls -l` and `ls -la` commands to read the directory and hidden files.

Within this command, we can see all five text files and their various permission settings, in addition to the `drafts` subdirectory.

## Describe the permissions string

Permissions string is interpreted as follows (`drwxrwxrwx`):
- `Drwxrwxrwx` – D = Directory
- `drwxrwxrwx` – User; r = read, w = write, x = execute
- `drwxrwxrwx` – Group; r = read, w = write, x = execute
- `drwxrwxrwx` – Other; r = read, w = write, x = execute

A string that is read as `-rw-rw-r--` will tell us that the text file has:
- User; read and write permission, but not execute
- Group; Read and Write permission, but not execute
- Other; only has a Read permission, but not write, nor does it have execute.

## Change file permissions

Here, we will remove the write permissions for others on `project_k.txt` by using the following command:
`chmod o-w project_k.txt`

You can see in the image the permissions for `project_k.txt` started at `-rw-rw-rw-`, but ended at `-rw-rw-r--`

## Change file permissions on a hidden file

As there are hidden files in the `/projects/` directory, the command `ls -la` will show all hidden files along with the normally visible files. The hidden file is exhibited by the filename starting with a period (`.`).

I will remove the write permissions on this `.project_x.txt` file of the user and group, but also add a read permission for the group as well. To do this I will execute the following command:
`chmod u-w,g-w,g+r .project_x.txt`

Now the file `.project_x.txt` only has read permissions for the user and the group, but no other write or execute permissions.

## Change directory permissions

We will change the `drafts` directory to remove the execute permission for the group. The current directory permissions for `drafts` is `drwx--x---`

To remove the group execute permission, we will run the following command:
`chmod g-x drafts`

And now `drafts` has a permission string of `drwx------` which only gives read, write, and execute permission to the user.

## Summary

Overall, we have been able to touch on many different commands that are used in file permissions in Linux. We can understand the permission string `drwxrwxrwx` and adjust the permissions using the `chmod` command.
