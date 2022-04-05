# Wildcards and Regular Expressions (regex)

**Wildcards** are useful in many ways! We can use them in commands to
perform actions on more than one file at a time or to find part of a
phrase in a text file. There are many uses for wildcards, but in
general, we can group them into two different major ways that wildcards
are used as:

-   **globbing patterns/standard wildcards** that are often used by the
    shell
-   **regular expressions** which are popular with many other commands
    and popular for use with text searching and manipulation.

Note that **wildcard patterns are not regular expressions**, although they are a bit similar. There are two major differences:

1.  **Wildcard patterns** match **filenames**, while **regular expressions** match **text**.
   
2.  The conventions are not the same: for example, in a **regular expression** `*` means zero or more copies of the preceding thing, while as a **wildcard** it matches any character zero or more times.

!!! tip
    If you have a file with **wildcard** expressions in it then you can use
    **single quotes** (`' '`) to stop bash expanding them or use
    **backslashes** (escape characters `\`), or both. But keep in mind that
    we should avoid creating files with names that contain wildcards.

------------------------------------------------------------------------

## Standard Wildcards (globbing patterns)

**Standard wildcards** (also known as **globbing patterns**) are used by
nearly any command (including `mv`, `cp`, `rm` and many others) to work
with multiple files. For the manual page type: `man glob`.

**Wildcard pattern** is a string that contains one of the special
characters such as: `?`, `*`, `[`...\
**Globbing** is the operation that expands a wildcard pattern into the
list of pathnames matching the pattern.

------------------------------------------------------------------------

-   `?` <br />represents **any single character**. <br /> e.g. for `hd?`
    Linux would look for `hda`, `hdb`, `hdc` and every other
    letter/number between a-z, 0-9.

------------------------------------------------------------------------

-   `*` <br />represents **any number of characters including none**,
    (in other words zero or more characters). <br /> e.g. If we specify
    a `cd*` it would use `cda`, `cdrom`, `cdrecord` and anything that
    starts with `cd` also including `cd` itself. `m*l` could by `mill`,
    `mull`, `ml`, and anything that starts with an `m` and ends with an
    `l`.

------------------------------------------------------------------------

-   `[ ]` <br />represents a **specified range** within the brackets.
    This kind of wildcard specifies an **OR** relationship. <br />e.g.
    If we do `m[a,o,u]m` it can become: `mam`, `mum`, `mom`; <br />if we
    do `m[a-d]m` it can become anything that starts and ends with `m`
    and has any character `a` to `d` in between (e.g. these would work:
    `mam`, `mbm`, `mcm`, `mdm`).

------------------------------------------------------------------------

-   `{ }` <br />represents **anything that matches either wildcard(s),
    or exact name(s)** (an **"OR"** relationship, one or the other).
    Multiple terms are separated by commas `,` and each term must be the
    name of something or a wildcard. <br />e.g. `cp {*.doc,*.pdf} ~`
    will copy anything ending with `.doc` or `.pdf` to the user's home
    directory (`~`). Note that **spaces are not allowed** after the
    commas (or anywhere else).

------------------------------------------------------------------------

-   `[!]` <br />This construct is similar to the `[ ]` construct, except
    rather than matching any characters inside the brackets, it'll
    **match any character that is not listed in the brackets**. This is
    a **logical NOT**. <br />e.g. `rm myfile[!9]` will remove all files
    starting with `myfiles` (ie. `myfiles1`, `myfiles2` etc.) but won't
    remove a file with the number 9 **anywhere** within its name.

------------------------------------------------------------------------

-   `\` <br />is used as an **"escape" character**, i.e. to protect a
    subsequent special character. Thus, `\\` searches for a backslash.
    Note you may need to use quotation marks and backslash(es).

------------------------------------------------------------------------

Wildcards can be used in combination with each other e.g. `?_*txt`
matches one character followed by `_` followed by any number of
characters including nothing and finally ending with `txt`. Thus this
pattern would give us `1_browsing_textfiles.txt`,
`2_searching_patterns.txt` in `~/unix_intro/exercises` directory.

!!! question
    When in the `~/unix_intro/exercises/genes` directory, which `ls`
    command(s) will produce `example.bed` and `mgat_genes.gb` as the output?
    <br />a) `ls *.*` 
    <br />b) `ls *b*` 
    <br />c) `ls *.b*` 
    <br />d)
    `ls ??a*` 
    <br />e) `ls *a*e*b*`
    
    ??? note "Click for Answer"
        Correct answers are: b), d) and e)



!!! question "Task"
    From `~/unix_intro/exercises/genes` directory, copy all files that are
    ending with 3 characters after the dot (i.e. `.???`) to your `~/backup`
    directory.
    ??? note "Click for Answer"
        ```
        cp ~/unix_intro/exercises/genes/*.??? ~/backup
        ```

------------------------------------------------------------------------

## Regular expression (regex)

A **regular expression** or **regex** is a pattern that matches a set of
strings. They can be described as a type of globbing pattern used when
working with **text**. They are used for any form of manipulation of
multiple parts of text and by various programming languages (e.g.
`grep`, `find`, `awk`, and many others) that work with text. For the
manual page type: `man regex`.

!!! tip
    If your regular expressions don't seem to be working then you probably
    need to use single quotation marks (`' '`) over the sentence and then
    use backslashes (`\`) on every single special character.

------------------------------------------------------------------------

-   `.` <br />matches any single character, equivalent to `?` in
    standard wildcard expressions. <br />e.g. `m.a` matches `mpa` and
    `mea` but not `ma` or `mppa`

------------------------------------------------------------------------

-   `[ ]` <br />matches any of the characters within parenthesis. It
    specifies a range. <br />e.g. `m[a,o,u]m` cmatches `mam`, `mum`,
    `mom`; while `m[a-d]m` matches anything that starts and ends with
    `m` and has any character `a` to `d` in between, e.g. `mam`, `mbm`,
    `mcm`, `mdm`. This kind of wildcard specifies an **or** relationship
    (you only need one to match)

------------------------------------------------------------------------

-   `.*`\
    <br />matches any character, any number of times, it is equivalent
    to `*` in standard wildcards. <br />e.g. `m.*` mathces anything
    starting with `m`

------------------------------------------------------------------------

-   `*` <br />matches zero or more times. <br />e.g. `n*` matches `n`,
    `nn`, `nnnn`, `nnnnnnn` but not `na` or any other character.

------------------------------------------------------------------------

-   `^`\
    <br />matches the beginning of the line. <br />e.g. `^a` matches a
    line starting with an `a`.

------------------------------------------------------------------------

-   `$`\
    <br />matches the end of the line. <br />e.g. `a$` matches a line
    ending with an `a`.

------------------------------------------------------------------------

-   `|`\
    <br /> performs a **logical OR relationship between wildcards**. We
    can use it to search for something or something else (possibly using
    two different regular expressions). We may need to add a `\`
    (backslash) before this command to work, because the shell may
    attempt to interpret this as a pipe. <br />e.g. `^a\|^b` matches a
    line starting with an `a` or with an `b`.

------------------------------------------------------------------------

-   `[^]`\
    <br /> matches anything that is **not** listed within square
    brackets. It is the equivalent of `[!]` in standard wildcards.
    <br />e.g. `rm myfile[^9]` will remove all `myfiles*` (i.e.
    `myfiles1`, `myfiles2` etc.) but won't remove a file with the number
    9 anywhere within its name.

------------------------------------------------------------------------