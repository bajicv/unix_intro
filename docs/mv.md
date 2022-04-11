# Moving, renaming and removing files and directories

## Move (rename) files and directories `mv`

To **move** a file from one place to another or to **rename** it, we can
use the `mv` command. The syntax for the `mv` command is:
`mv file1 file2` - this will move or rename `file1` to `file2`.

Now, let's go to our home directory `cd ~` and **rename**
`my_first_touch_file.txt` with a more compact name `mftf.txt`:

```
mv my_first_touch_file.txt mftf.txt
```

Now, let's **move** `mftf.txt` to `my_first_dir` directory:

```
mv mftf.txt my_first_dir
```
_________________________________________________________________________________________

## Remove file or directories `rm`

To **delete** (remove) a file or directory we can use the `rm` command.
Let's delete `mftf.txt` file which we moved to `my_first_dir` but all
that while being in our home directory. 

!!! tip
    Be aware that the **shell does not have a trash bin** - so, once something is deleted, it's really gone! Be careful what you delete!

```
cd ~
rm my_first_dir/mftf.txt
```

By default `rm` only works on files. `rm` can remove a directory and all
its contents if we use the recursive option `-r`.

Now let's delete `my_first_dir`.

```
rm -r my_first_dir
```