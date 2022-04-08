# Copying files and directories locally and remotely

## Copying files and directories `cp`

`cp file1 file2` is the command which makes a copy of `file1` in the
*current working directory* and calls it `file2`.

Let's copy our first `touch` file and name it same but with adding
"\_copy" (_P.S. don't forget to use `Tab` to auto-complete long names of our files_):

!!! question "Task"
    Copy your first touch file `my_first_touch_file.txt` to `my_first_dir`
    directory, and name it as `my_first_touch_file_copy.txt`.

    ??? question "Click for Answer"
        ```
        cp my_first_touch_file.txt my_first_touch_file_copy.txt
        ```


Now when we learned how to `cp` files, let's copy the exercise
*directory* from `/opt/evop/public/BIOINFORMATICS/unix_intro/exercises`
to your home directory (`~`). We can copy a directory and all its
contents by using the **recursive** option `-r`:

```
cp -r /opt/evop/public/BIOINFORMATICS/unix_intro ~
```

To make sure the files are copied correctly, we can type `ls unix_intro`

Often we would need to copy several files at once. This can be done by
providing a list of individual filenames followed by a directory name
where to copy those files (i.e.
`cp [file1] [file2] ... [Dir where to copy]`).

For this exercise, let's make a directory called `backup`. Now let's
copy files from `~/unix_intro/exercises/` called
`1_browsing_textfiles.txt` and `2_searching_patterns.txt` in it.

```
cd
mkdir backup
cp ~/unix_intro/exercises/1_browsing_textfiles.txt ~/unix_intro/exercises/2_searching_patterns.txt backup
```

---------------------------------------------------------------------------------------

## Secure copy (remote file copy program) `scp`

The files we copied are still in our directories at the FU cluster. We
can copy files and directories to our local machines using `scp` command
(*secure copy*). The `scp` is a remote file copy program that allows us
to securely copy files and directories between remote hosts without
starting an FTP session or logging into the remote systems explicitly.

The syntax for the `scp` command is:

```
scp [options] username1@source_host:directory1/filename1 username2@destination_host:directory2/filename2
```

The location of the source file is specified by
`username1@source_host:directory1/filename1`, which includes the:

-   Name of the account on the host computer (`username1`)
-   A hostname of the computer on which the source file resides
    (`source_host`)
-   Name of the directory containing the source file (`directory1`)
-   A filename of the source file (`filename1`)

The location to which the source file will be copied is specified by
`username2@destination_host:directory2/filename2`, which includes the:

-   Name of the account on the destination computer (`username2`)
-   A hostname of the computer to which the source file will be copied
    (`destination_host`)
-   Name of the directory to which the source file will be copied
    (`directory2`)
-   A filename of the copy (`filename2`)

The tricky part here is that we need to do it in two steps (in reverse
compared to the login process):

1.  First step is copying from `evop-login` to `andorra`. Let's try it,
    open a new terminal session from your local machine, log in to
    `andorra`, and then copy the `unix_intro` directory from
    `evop-login` to the current directory while being logged-in to
    `andorra`:

```
ssh YourID@andorra.imp.fu-berlin.de # enter your password once asked for it
scp -r evop-login:~/unix_intro .
```

2.  Second step is copying it from `andorra` to our `local machines`. To
    do so, open a new terminal session from your local machine go to a
    directory where you wanna save your files (e.g. `Downloads`), and
    then copy the `unix_intro` directory from `andorra` using `scp`:

```
scp -r YourID@andorra.imp.fu-berlin.de:~/unix_intro . # enter your password once asked for it
```

Please note that here we are using our current directory (`.`) at our
local computers as the location to which the file will be copied, and
since we are already logged-in to our computers we do not need to print
the entire paths such as
`username2@destination_host:directory2/filename2`.

## WinSCP for Windows

In case we want to copy our files to a Windows machine, without using
the command-line, we can do it using
[WinSCP](https://winscp.net/eng/download.php). Login is very similar to
the one used with `Putty`. Once logged-in into the server, you will see
`WinSCP` split into two windows. Left (your PC) Right (the server). Just
move the contains from right to left and vice-versa using the mouse.