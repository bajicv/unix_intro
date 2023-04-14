# Making Files and Directories

Before we make our first directory and file lets get a few useful tips
for the names of your files.

!!! tip
    - **Don't** use `Space`, `<`, `>`, `|`, `\`, `:`, `(`, `)`, `&`, `;`, `?`, `*`

    - **Don't** begin the name with a dash (`-`), or a full stop (`.`).

    - **Do** stick with `letters`, `numbers`, a dash (`-`), and an underscore (`_`). 
            
    - Try to use a full stop (`.`) only for file extensions (e.g. `.pdf`, `.txt`...).

    - Unix is **case sensitive**. So filename `my_first_file.txt`, `My_First_File.txt`, `my_FIRST_file.txt`, all are three **different** files.

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

```
cd ~
mkdir my_first_dir 
```

Once you made it, do `ls` to check if it is there.

------------------------------------------------------------------------

## Making files `nano`, `touch`

There are many ways to make a file. Here we will only give some
examples.

### `nano`

`nano` is a command-line text editor and we can use it to modify and
create text files. Type `nano` in your command-line:

```
nano 
```

Ok, don't get afraid. Now we are inside `nano` and you can see basic
commands at the bottom of the window.

![nano](https://cdn.staticaly.com/gh/Lin-Buo-Ren/nano-snap/24def40f/snap/local/screenshots/main-interface.png)


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

Now let's type something (e.g. *"I love whales!"*) and
press `Ctrl`+`X`. This will close the file, but `nano` will offer us to
save it. When `nano` asks as if we want to save it we have to press `Y`,
and then `nano` will ask as for _"File Name to Write:"_. Let's name it as
`my_first_file.txt`. After you typed it just press `Enter` and the file
will be saved. Check if it is there with command `ls`.

Let's open the file we just created.

```
nano my_first_file.txt
```

Let's type in a bit of text (e.g. _"4 real"_). Once we're happy with our
text, we can press `Ctrl`+`O` to save it. We'll be asked "File Name to
Write:" and we can just press the `Enter` and use already existing name
`my_first_file.txt`, or we can make a modified copy by giving it a new
name. After we are done we can close `nano` as before with `Ctrl`+`X`.


### `touch`

The touch command's primary function is to modify a timestamp. Commonly, the utility is used for file creation, although this is not its primary function. The terminal program can change the modification and access time for any given file. The touch command creates a file only if the file doesn't already exist.

Some programs do not generate output files themselves but instead require that empty files have already been generated. When the program is run, it searches for an existing file to populate with its output. The `touch` command allows us to efficiently generate a blank text file to be used by such programs.


```
touch my_first_touch_file.txt
```

!!! question
     1. What happens when you type `touch test_file_{0..5}.txt` in your home directory? 
     2. What happens when you type `touch test_file_{a..e}.txt` in your home directory? 

!!! tip "Homework"
    Explore `vim`.<br /> 
    [Vim](https://www.vim.org/) is a highly configurable text editor built to make creating and changing any kind of text very efficient. It is included as "vi" with most UNIX systems and with Apple OS X. <br />
    _P.S. In case you are struggling to close it, take a look [here](https://phoenixnap.com/kb/how-to-exit-vim)._

------------------------------------------------------------------------
