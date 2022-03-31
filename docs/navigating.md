# Navigating Files and Directories

The part of the operating system responsible for managing files and
directories is called the **file system**. It organizes our data into
**files**, which hold information, and **directories** (also called
"folders"), which hold files or other directories.

Let's have a look at how the file system as a whole is organized.

![Standard Unix filesystem
hierarchy](C:/Users/vladi/Nextcloud/Nowick_Lab/Master_course_Bioinformatics_for_Biologists/SoSe2020/Standard-unix-filesystem-hierarchy.svg){width="100%"}

At the top is the **root directory** that holds everything else. We
refer to it using a slash character `/` at the front of a file or
directory name. However, most of the `/` characters appear inside a
path, and they symbolize a separator.

Inside the root directory, there are several other directories:
`bin`(which is where some built-in programs are stored), `usr` (where
users' personal directories i.e. **home directory** are located), and so
on.

Typically, when we open a new command prompt we will be in our **home
directory** (also called a *login directory*). We refer to the home
directory by character `~`.

Directories are like rooms in a huge building (i.e. computers file
system) - at any time while we are using the shell we are in exactly one
room, called the **current working directory**. We refer to the current
directory with a dot `.`. Most commands by default read and write files
in the current working directory, so knowing where we are before running
a command is very important!

------------------------------------------------------------------------

## Locate yourself `pwd`

We can locate ourselves by running a command `pwd` (short for *print
working directory*).

::: {.alert .alert-warning}
<strong>TASK:</strong>

------------------------------------------------------------------------

Type `pwd` in your current directory.
:::

------------------------------------------------------------------------

## List files and directories `ls`

We can see what's in our home directory by running `ls`, (short for
*list*):

::: {.alert .alert-warning}
<strong>TASK:</strong>

------------------------------------------------------------------------

Type `ls` in your current directory.
:::

`ls` will print the names of the files and directories in the current
directory. We can make its output more comprehensible by using the `-F`
**option** (also known as a *switch* or a *flag*), which tells `ls` to
classify the output by adding a marker to file and directory names to
indicate what they are (directories will end with `/`, links with `@`,
and executable with `*`). Depending on your default options, the shell
might also use colors to differentiate files and directories:

```{bash, echo = T, eval =F}
ls -F /
```

    bin@             lib@         opt/   tmp/
    boot/            lib32@       proc/  usr/
    dev/             lib64@       root/  var/
    etc/             libx32@      run/   vmlinuz@
    home/            lost+found/  sbin@  vmlinuz.old@
    initrd.img@      media/       srv/
    initrd.img.old@  mnt/         sys/

By convention, in Unix systems **hidden files** have a name beginning
with a `.` The `-a` option of `ls` will shows all the files, including
the hidden ones. Your home folder might contain several hidden
configuration files (e.g. `.bashrc`, `.conf`, `.cache`). We can ignore
them for the moment.

::: {.alert .alert-warning}
<strong>TASK:</strong>

------------------------------------------------------------------------

Exploring more `ls` options. <br />a) What does the command `ls` do when
used with the `-l` option? <br />b) What about if you use both the `-l`
and the `-h` option? <br />c) What about if you use both the `-r` and
the `-t` option? <br />d) Which option can be passed to `ls` to sort
files by size? <br />e) What does **SYNOPSIS** in `man ls` tells us?
<br />f) How can we show the contents of a directory recursively with
`ls`? <br />g) What does `ls / ~ .` do?
:::

------------------------------------------------------------------------

## Changing Directories `cd`

The command `cd` allows us to change the **current working directory**
to the desired directory specified in the commands argument.

Let's move from our home directory `~` to
`/opt/evop/public/BIOINFORMATICS/unix_intro/exercises`. Now we can type
`ls` to see what is in there.

```{bash, echo = T, eval = F}
cd /opt/evop/public/BIOINFORMATICS/unix_intro/exercises
ls
```

    01_browsing_textfiles.txt  1_browsing_textfiles.txt  2_searching_patterns.txt  creatures  genes  multiplefiles

Now move to the **parent directory** and do `ls`:

```{bash, echo = T, eval=F}
cd ..
ls
```

    exercises

------------------------------------------------------------------------

## Absolute vs Relative Paths

A **path** is a unique location to a file or a folder in a file system
of an OS. A path to a file is a combination of `/` and alpha-numeric
characters.

### Absolute path

An **absolute path** is defined as the location of a file or directory
**from the root directory** (`/`). In other words, an absolute path
could be seen as a complete path from the start of the actual file
system from `/` directory.

### Relative path

A **relative path** is defined as the location of a file or directory
**from the present working directly** (`.`). The relative path starts at
our current directory and never starts with a `/`.

#### Directories `.` and `..`

UNIX offers a shortcut in the relative pathname that uses either the
**current** or **parent directory** as a reference and specifies the
path relative to it. A **relative path-name** uses one of these symbols:

-   `.` representing the **current directory**.
-   `..` representing the **parent directory**.

------------------------------------------------------------------------

## Search for files in a directory hierarchy `find`

We can use `find` command to find files and directories. It has a lot of
options, and here we will show how the simplest ones work.

For our first command, let's run `find .` from directory
`/opt/evop/public/BIOINFORMATICS/unix_intro/exercises`.

```{bash, echo = T, eval=F}
cd /opt/evop/public/BIOINFORMATICS/unix_intro/exercises
find .
```

<details>

<summary>

```Click here to see the output:```

</summary>

    .
    ./1_browsing_textfiles.txt
    ./multiplefiles
    ./multiplefiles/file42.txt
    ./multiplefiles/file7.txt
    ./multiplefiles/file4.txt
    ./multiplefiles/file0.txt
    ./multiplefiles/file27.txt
    ./multiplefiles/file14.txt
    ./multiplefiles/file33.txt
    ./multiplefiles/file1.txt
    ./multiplefiles/file45.txt
    ./multiplefiles/file5.txt
    ./multiplefiles/file34.txt
    ./multiplefiles/file12.txt
    ./multiplefiles/file49.txt
    ./multiplefiles/file37.txt
    ./multiplefiles/file3.txt
    ./multiplefiles/file17.txt
    ./multiplefiles/file2.txt
    ./multiplefiles/file24.txt
    ./multiplefiles/file18.txt
    ./multiplefiles/file38.txt
    ./multiplefiles/file30.txt
    ./multiplefiles/file23.txt
    ./multiplefiles/file29.txt
    ./multiplefiles/file41.txt
    ./multiplefiles/file19.txt
    ./multiplefiles/file16.txt
    ./multiplefiles/file46.txt
    ./multiplefiles/file40.txt
    ./multiplefiles/file6.txt
    ./multiplefiles/file43.txt
    ./multiplefiles/file36.txt
    ./multiplefiles/file31.txt
    ./multiplefiles/file47.txt
    ./multiplefiles/file13.txt
    ./multiplefiles/file35.txt
    ./multiplefiles/file26.txt
    ./multiplefiles/file20.txt
    ./multiplefiles/file28.txt
    ./multiplefiles/file48.txt
    ./multiplefiles/file11.txt
    ./multiplefiles/file39.txt
    ./multiplefiles/file10.txt
    ./multiplefiles/file25.txt
    ./multiplefiles/file15.txt
    ./multiplefiles/file22.txt
    ./multiplefiles/file21.txt
    ./multiplefiles/file32.txt
    ./multiplefiles/file9.txt
    ./multiplefiles/file44.txt
    ./multiplefiles/file8.txt
    ./genes
    ./genes/mgat_genes.gb
    ./genes/chr9.gff
    ./genes/example.bed
    ./genes/sequences.fasta
    ./genes/chrX.gff
    ./genes/chr8.gff
    ./creatures
    ./creatures/minotaur.dat
    ./creatures/unicorn.dat
    ./creatures/basilisk.dat
    ./01_browsing_textfiles.txt
    ./2_searching_patterns.txt

</details>

<br /><br /><br />

As we explained before, the `.` as such means the *current working
directory*, which is where we want our search to start. `find` will
output names of every file and directory under the current working
directory. This can seem useless at first but `find` has many options to
filter the output and in the next couple of minutes, we will discover
some of them.

The first option in our list is `-type d` that means **things that are
directories**. `find` will output names of all directories in our
current working directory `~/unix_intro/exercises`:

```{bash, echo = -1, eval=T}
cd ~/unix_intro/exercises
find . -type d
```

<details>

<summary>

```Click here to see the output:```

</summary>
```{}
.
./multiplefiles
./genes
./creatures
```
</details>

Notice that the objects `find` finds are not listed in any particular
order. If we change `-type d` to `-type f`, we get a listing of all the
**files** instead:

```{bash, echo = -1, eval=F}
cd ~/unix_intro/exercises
find . -type f
```

<details>

<summary>

```Click here to see the output:```

</summary>

    ./1_browsing_textfiles.txt
    ./multiplefiles/file42.txt
    ./multiplefiles/file7.txt
    ./multiplefiles/file4.txt
    ./multiplefiles/file0.txt
    ./multiplefiles/file27.txt
    ./multiplefiles/file14.txt
    ./multiplefiles/file33.txt
    ./multiplefiles/file1.txt
    ./multiplefiles/file45.txt
    ./multiplefiles/file5.txt
    ./multiplefiles/file34.txt
    ./multiplefiles/file12.txt
    ./multiplefiles/file49.txt
    ./multiplefiles/file37.txt
    ./multiplefiles/file3.txt
    ./multiplefiles/file17.txt
    ./multiplefiles/file2.txt
    ./multiplefiles/file24.txt
    ./multiplefiles/file18.txt
    ./multiplefiles/file38.txt
    ./multiplefiles/file30.txt
    ./multiplefiles/file23.txt
    ./multiplefiles/file29.txt
    ./multiplefiles/file41.txt
    ./multiplefiles/file19.txt
    ./multiplefiles/file16.txt
    ./multiplefiles/file46.txt
    ./multiplefiles/file40.txt
    ./multiplefiles/file6.txt
    ./multiplefiles/file43.txt
    ./multiplefiles/file36.txt
    ./multiplefiles/file31.txt
    ./multiplefiles/file47.txt
    ./multiplefiles/file13.txt
    ./multiplefiles/file35.txt
    ./multiplefiles/file26.txt
    ./multiplefiles/file20.txt
    ./multiplefiles/file28.txt
    ./multiplefiles/file48.txt
    ./multiplefiles/file11.txt
    ./multiplefiles/file39.txt
    ./multiplefiles/file10.txt
    ./multiplefiles/file25.txt
    ./multiplefiles/file15.txt
    ./multiplefiles/file22.txt
    ./multiplefiles/file21.txt
    ./multiplefiles/file32.txt
    ./multiplefiles/file9.txt
    ./multiplefiles/file44.txt
    ./multiplefiles/file8.txt
    ./genes/mgat_genes.gb
    ./genes/chr9.gff
    ./genes/example.bed
    ./genes/sequences.fasta
    ./genes/chrX.gff
    ./genes/chr8.gff
    ./creatures/minotaur.dat
    ./creatures/unicorn.dat
    ./creatures/basilisk.dat
    ./01_browsing_textfiles.txt
    ./2_searching_patterns.txt

</details>

<br /><br /><br />

Now let's try **matching by name**:

```{bash, echo = -1, eval=T}
cd ~/unix_intro/exercises
find . -name 1_browsing_textfiles.txt
```

<details>

<summary>

```Click here to see the output:```

</summary>
```{}
./1_browsing_textfiles.txt
```
</details>

------------------------------------------------------------------------

<br /><br /><br />

# Making Files and Directories

Before we make our first directory and file lets get a few useful tips
for the names of your files.

-   Don't use `Space`, `<`, `>`, `|`, `\`, `:`, `(`, `)`, `&`, `;`, `?`,
    `*`

-   Don't begin the name with a dash (`-`), or a full stop (`.`).

-   The best is to stick with `letters`, `numbers`, a dash (`-`), and an
    underscore (`_`). Try to use a full stop (`.`) only for file
    extensions (e.g. `.pdf`, `.txt`...).

-   Unix is **case sensitive**. So filename `my_first_file.txt`,
    `My_First_File.txt`, `my_FIRST_file.txt`, all are three different
    files.

Complicated names of files and directories can make our lives painful
when working on the command-line. Many [characters have special
meanings](https://www.howtogeek.com/439199/15-special-characters-you-need-to-know-for-bash/)
on the command-line. We already mentioned some and we will learn some
more of them during this course. There are special characters that can
cause your command to not work as expected and can even result in data
loss.

As we learned before Unix commands treat names starting with `-` as
command **options**, and `.` in front of the filename makes it
invisible. Spaces can make a name more meaningful, but since **spaces
are used to separate arguments on the command-line** it is better to
avoid them in names of files and directories. If you use `Space` in a
file/directory name, you will have to treat every space as a special
character. E.g. if we named our directory as `my first dir` in order to
access it we would have to type `my\ first\ dir` to access it, or we can
surround the name in quotes `"my first dir"`. We can also let the `Tab`
auto-completion do the work for us if there are no other
files/directories with a similar name. Instead of `Space`, we can use
`-` or `_` instead.

------------------------------------------------------------------------

## Making directories `mkdir`

Let's create a new **directory** in our home directory (`~`) called
`my_first_dir` using the command `mkdir`.

```{bash, echo = T, eval=F}
cd ~
mkdir my_first_dir 
```

Once you made it, do `ls` to check if it is there.

------------------------------------------------------------------------

## Making files `nano`, `touch`

There are many ways to make a file. Here we will only give some
examples.

------------------------------------------------------------------------

### `nano`

`nano` is a command-line text editor and we can use it to modify and
create text files. Type `nano` in your command-line:

```{bash, echo = T, eval=F}
nano 
```

Ok, don't get afraid. Now we are inside `nano` and you can see basic
commands at the bottom of the window.

Here are some of the useful `nano` commands:

| `nano` command     | description |
|--------------------|-------------|
| `Ctrl`+`O`         | save a file |
| `Ctrl`+`R`         | read a file |
| `Ctrl`+`X`         | exit        |
| `Alt`+`U`          | undo        |
| `Alt`+`E`          | redo        |
| `Alt`+`^`          | copy        |
| `Ctrl`+`U`         | paste       |

Now let's type something (e.g. *"Can't wait for quarantine to end"*) and
press `Ctrl`+`X`. This will close the file, but `nano` will offer us to
save it. When `nano` asks as if we want to save it we have to press `Y`,
and then `nano` will ask as for "File Name to Write:". Let's name it as
`my_first_file.txt`. After you typed it just press `Enter` and the file
will be saved. Check if it is there with command `ls`.

Let's open the file we just created.

```{bash, echo = T, eval=F}
nano my_first_file.txt
```

Let's type in a bit of text (e.g. "*4 real*"). Once we're happy with our
text, we can press `Ctrl`+`O` to save it. We'll be asked "File Name to
Write:" and we can just press the `Enter` and use already existing name
`my_first_file.txt`, or we can make a modified copy by giving it a new
name. After we are done we can close `nano` as before with `Ctrl`+`X`.

------------------------------------------------------------------------

### `touch`

Some programs do not generate output files themselves but instead
require that empty files have already been generated. When the program
is run, it searches for an existing file to populate with its output.
The `touch` command allows us to efficiently generate a blank text file
to be used by such programs.

```{bash, echo = T, eval=F}
touch my_first_touch_file.txt
```