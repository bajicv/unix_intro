# Accessing the content of a file

In this section, we will get familiar with a few commands (`head`,
`tail`, `cat`, `wc`, `less`) that allow us to access the content of a
file.

## Output the first part of files `head`

The `head` command writes the **first** ten lines of a file to the
screen.

```
cd ~/unix_intro/exercises
head 1_browsing_textfiles.txt
```

We can use the `-n` option in `head` command to define a number of first
lines to be printed out. Let's use `-n 40` option to print the first 40
lines of this file:

```
cd ~/unix_intro/exercises
head -n 40 1_browsing_textfiles.txt
```

The letter `n` does not even need to be used at all. Just the hyphen `-`
and the integer (with no intervening space) are sufficient to tell
`head` how many lines to return. Thus, the following would produce the
same result as the above commands:

```
cd ~/unix_intro/exercises
head -40 1_browsing_textfiles.txt
```

!!! tip
    Some commands will expect from us a file which to process. But what
    happens if we do not give it a filename? For example, what if we type
    `head` and press `Enter`, but do not type anything else after the
    command. Since it doesn't have any filenames, `head` assumes it is
    supposed to process input given at the command prompt, so it just sits
    there and waits for us to give it some data interactively. From the
    outside, though, all we see is it sitting there: the command doesn't
    appear to do anything.

    If you make this kind of mistake, you can escape out of this state by
    `Ctrl`+`C` (i.e. holding down the `Ctrl` key (or `Strg` on German
    keyboards) and typing the letter `C` (standing for "cancel") once and
    letting go of the `Ctrl` key). Or if you are using Mac: `Command`+`.`.


------------------------------------------------------------------------

## View the content of a text file one screen at a time `less`

The command `less` writes the contents of a file onto the screen a page
at a time. Thus, `less` allows browsing the contents of a file,
read-only, in a modality similar to what we saw with the `man` pages.

We can use ↑, ↓, ←, → to move line-by-line and left and right, or
`Space` to skip up and down by a full page. To search for a pattern in
the `less` pages, we can use `/` followed by the pattern we are
searching for. Sometimes a search will result in multiple hits. If so,
you can move between hits using `n` (for *next*, for moving to next
instance) and `p` (for moving to the *previous* instance). To *quit* the
`less`, press `q`.

Now, open the `1_browsing_textfiles.txt` file with `less`, scroll down
the file and follow the instructions in the file.

```
less 1_browsing_textfiles.txt
```

------------------------------------------------------------------------


## Output the last part of files `tail`

The `tail` command writes the **last** ten lines of a file to the
screen. Same as for the `head`, we can specify how many lines we want
`tail` to print out. So, let's print last 12 lines of the same file:

```
cd ~/unix_intro/exercises
tail -12 1_browsing_textfiles.txt
```

------------------------------------------------------------------------

## Concatenate files and print on the standard output `cat`

The `cat` (concatenate) command can be used to display the contents of a
file on the screen. The name is derived from its function to
*concatenate* files.

```
cd ~/unix_intro/exercises
cat 1_browsing_textfiles.txt
```

As you can see, the file is longer than the size of the window, so it
scrolls past making it unreadable.

The `cat` command can be very useful to **concatenate** multiple files.
Let's concatenate two text files and write them to a new file:

```
cd ~/unix_intro/exercises
cat 1_browsing_textfiles.txt 2_searching_patterns.txt > new_cat_1_2_file.txt
```

We can also **append** the contents of `2_searching_patterns.txt` to
`01_browsing_textfiles.txt`:

```
cat 2_searching_patterns.txt >> 01_browsing_textfiles.txt
```

!!! question
    Which option of the `cat` command you will use to find out: <br />a) how
    many lines there are in `1_browsing_textfiles.txt` including blank
    likes? <br />b) how many lines there are in `1_browsing_textfiles.txt`
    excluding blank likes? 
    
    ??? note "Click for Answer"
        <br />a) `cat -n 1_browsing_textfiles.txt` gives 81 lines in total
        <br />b) `cat -b 1_browsing_textfiles.txt` gives 57 non-blank lines

------------------------------------------------------------------------

## Word count `wc`

Besides doing `cat -n` we can use very handy `wc` command, short for
*word count*.

To do a **word count** on `1_browsing_textfiles.txt` we can type:

```
wc -w 1_browsing_textfiles.txt
```

To do a **line count** on `1_browsing_textfiles.txt` we can type:

```
wc -l 1_browsing_textfiles.txt
```

!!! question
    Which option of the `wc` command you will use to find out how many **characters** there are in `1_browsing_textfiles.txt`?
    
    ??? note "Click for Answer"
        `wc -m 1_browsing_textfiles.txt` gives 2642 characters.

------------------------------------------------------------------------

