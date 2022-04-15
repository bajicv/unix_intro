# Print lines matching a pattern

`grep` is one of many standard Unix utilities. It searches files for
specified words or patterns. The `grep` command is *case sensitive*.

___________________________________________________________________________

## Using `grep` on a single file

The instructions for the `grep` exercises are stored in the
`2_searching_patterns.txt` file. If we look at this file with `head` or
`less`, we will see that there is no obvious meaning in its content.
This is only because the instructions are hidden in the file, just so we
can practice the `grep` command. To find out what is inside we have to
search for the lines containing the word *"start"*. To find them, let's
use `grep`:

```
cd unix_intro/exercises
grep start 2_searching_patterns.txt
```

Now the document told us to `grep` the word *"help"* to continue:

```
grep help 2_searching_patterns.txt
```

For the next exercise, we need to open `grep`'s documentation and
identify two options:

-   the option for *case-insensitive* searches
-   the option for *counting the number of matching lines*, instead of
    printing them to the screen.

Once we have identified these options, let's do a case-insensitive
search on this file for the word *"ignorecase"*, then we will count the
number of lines.

If we do a search for *"ignorecase"* without any option, we only get
some of the lines.

```
grep ignorecase 2_searching_patterns.txt
```

The `-i` option allows to do a **case-insensitive** search.

```
grep -i ignorecase 2_searching_patterns.txt
```

To solve the exercise, we also have to **count the number of output
lines**. This can be done with the `-c` option:

```
grep -ic ignorecase 2_searching_patterns.txt
```

Solution: how to find the instructions for the next exercise

```
grep 21 2_searching_patterns.txt
```

___________________________________________________________________________

## Using `grep` on multiple files

`grep` is useful to search over multiple files in a single command. The
directory `~/exercises/multiplefiles/` contains 50 randomly generated
files. You can see their contents with
`head ~/unix_intro/exercises/multiplefiles/*` or with `less` command on
each of them.

One of these files contains the word *"regex"* in it. Are you able to
find it?

We can use the `*` character to specify multiple files:

```
cd unix_intro/exercises
grep 'regex' multiplefiles/*
```
___________________________________________________________________________

## Searching multiple patterns with piping system

We can combine `grep` with pipes (`|`) to search for multiple patterns
(i.e. we can use one `grep` command, and then pipe the output of it to
another `grep` and so on) like this:
`grep (first pattern) myfile.txt | grep (second pattern)`

Let's practice this on the genbank file called `mgat_genes.gb` in
`~/unix_intro/exercises/genes` directory. Take a look at this file and
notice how this format is well suited for grep searches:

```
cd unix_intro/exercises/genes
head mgat_genes.gb
```

Let's say that we are interested in finding all the lines where
**"ORGANISM"** is **"Homo sapiens"**.

We can do it with two grep commands:

```
cd unix_intro/exercises/genes
grep ORGANISM mgat_genes.gb | grep 'Homo sapiens'
```

Notice that searching for *"Homo sapiens"* alone would not be enough, as
there are other lines where the word "Homo sapiens" is present. The file
contains sequences from two other organisms apart from Homo sapiens. Can
you guess which one to search for the next exercise? Try "bos taurus":

```
cd unix_intro/exercises/genes
grep ORGANISM mgat_genes.gb | grep taurus
```

------------------------------------------------------------------------

## Regular Expressions (regex) in `grep`

As we learned before a **regular expression** or **regex** is a pattern
that matches a set of strings. A pattern consists of operators,
constructs literal characters, and meta-characters, which have special
meaning. `grep` supports three regular expression syntaxes:

-   **Basic** (`-G` or `--basic-regexp`),
-   **Extended** (`-E` or `--extended-regexp`), and
-   **Perl-compatible** (`-P` or `--perl-regexp`).

In its simplest form, when no regular expression type is given, `grep`
interpret search patterns as **basic regular expressions**. To interpret
the pattern as an extended regular expression, we should use the option
`-E` ( or `--extended-regexp`) option.

Now let's go to `unix_intro/exercises/genes` direcotry and use `grep` to
identify all the sequences containing **three As**, followed by any
**two characters**, followed by **three Ts** in the file called
`sequences.fasta`?

```
cd unix_intro/exercises/genes
grep 'AAA..TTT' sequences.fasta
```

If we use the `-B1` `grep` option, we can retrieve the names of these
sequences:

```
cd unix_intro/exercises/genes
grep -B1 'AAA..TTT' sequences.fasta
```

The `-B` option will print specified number of lines of leading context
before matching lines (e.g. `-B1` one line before matched line, `-B9`
nine lines before matched line, and so on).

Now, let's **pipe** an additional `grep '>'` to see a cow:

```
cd unix_intro/exercises/genes
grep -B1 'AAA..TTT' sequences.fasta | grep '>'
```

!!! question "Task"
    How would you use `grep` on file `sequences.fasta` that is located in `~/unix_intro/exercises/genes` to find:<br /> 
    <br />a) lines starting with an `G` and ending with an `C`?<br /> 
    <br />b) lines starting with an `G` and ending with an `C` or lines starting with an `C` and ending with an `T`?
    (Hint: use regex for logical OR relationship between wildcards `\|`)<br />
    <br />c) lines starting with an `G` and ending with an `C`, and contain in them `N` followed with an `T`. 
    (Hint: pipe from one grep to another)<br />

    ??? note "Click for Answer"
        <br />a) `grep '^G.*C$' sequences.fasta` 
        <br />b) `grep '^G.*C$\|^C.*T$' sequences.fasta` 
        <br />c) `grep '^G.*C$' sequences.fasta | grep 'NT'`