# Working with tabular files

The `awk` provides a scripting language for text processing.

There are three variations of `awk`:<br /> 
1. `awk` (the very old and original from AT&T),<br /> 
2. `nawk` (a newer, improved version from AT&T), and<br /> 
3. `gawk` (the Free Software foundation's version). All of `awk`'s features are in `nawk` and `gawk`, but they do have some incompatibilities.<br />

*Why is `awk`so important?* <br /> With `awk` scripting language, we can
define variables, use string and arithmetic operators, use control flow
and loops, generate formatted reports... But here we will focus on using
`awk` for working with tabular files as `awk` allows us to search and
manipulate tabular files quite easily. Many Unix utilities generate
*rows* and *columns* of information, and `awk` is an excellent tool for
processing these rows and columns, and it is easier to use it than most
conventional programming languages. With `awk`, we can extract specific
columns of a file, do numerical operations, change the order of the
columns, and many others.

------------------------------------------------------------------------

## Example of tabular file

The advantage of a command-line tool over graphical software is that the
memory footprint is much lower. So we can access and modify large files
in a fraction of the time that it would take with Excel. Not even to
mention that some of the files which you might be working on will be
much bigger than Excel can handle. So get ready to learn basics with
`awk`!

First, let's take a look at the example of a tabular file (e.g. "GFF3""
format). We can find it in `~/unix_intro/exercises/genes`.

```
cd ~/unix_intro/exercises/genes
head chr8.gff
```
??? note "Click to see the output"
    ```
    ##gff-version 3
    ##source-version rtracklayer 1.34.1
    ##date 2017-02-27
    ##genome-build .        hg19
    chr8    rtracklayer     sequence_feature        18248755        18258723        .       +       .       gene_id=10;symbol=NAT2;exerc1=FALSE;ID=10
    chr8    rtracklayer     sequence_feature        100549014       100549089       .       -       .       gene_id=100126309;symbol=MIR875;exerc1=FALSE;ID=100126309
    chr8    rtracklayer     sequence_feature        144895127       144895212       .       -       .       gene_id=100126338;symbol=MIR937;exerc1=FALSE;ID=100126338
    chr8    rtracklayer     sequence_feature        145619364       145619445       .       -       .       gene_id=100126351;symbol=MIR939;exerc1=FALSE;ID=100126351
    chr8    rtracklayer     sequence_feature        91970706        91997485        .       -       .       gene_id=100127983;symbol=C8orf88;exerc1=FALSE;ID=100127983
    chr8    rtracklayer     sequence_feature        74332309        74353753        .       +       .       gene_id=100128126;symbol=STAU2-AS1;exerc1=FALSE;ID=100128126
    ```

As you can see, `.gff` (standing for General Feature Format) is a
tab-separated file. You can find GFF format specifications defined
[here](https://genome.ucsc.edu/FAQ/FAQformat.html#format3), but in
short:

-   **col1** contains chromosome name,
-   **col2** describes the tool or resource that generated the
    annotation,
-   **col3** describes the type of feature (e.g. gene, transcript, exon,
    TF binding site, Histone Acetylation mark, etc...
-   **col4** and **col5** contain genomic coordinates (start and end)
-   **col9** column contains several fields, separated by a semicolon `;`

------------------------------------------------------------------------

## Basic `awk` syntax

The basic `awk` syntax is the following:
`awk options 'selection _criteria {action }' input-file`

------------------------------------------------------------------------

## `awk` options

Some of the options we can give to `awk` can be:

-   `-F fs` To specify a file **separator(s)**.
-   `-f file` To specify a **file** that contains `awk` script.
-   `-v var=value` To declare a **variable**.

`awk` is quite smart at recognizing the field separator, and by default
assumes they are separated by `spaces` or `Tabs`. In case we would like
to use some other characters as separators we can define them with
option `-F` (e.g. `-F','` indicated that separator is comma `,`).

------------------------------------------------------------------------

## Using `awk` variables to extract specific columns

`awk` assigns some variables for each column of the file, and we can
refer to them with the dollar sign (`$`) followed by the number of
column (e.g. `$1` would be the first column, `$2` the second, and so on,
while `$0` refers to all columns).

Now, let's check this example and see how `awk` processes it:

```
cd ~/unix_intro/exercises/genes
awk '{print $1}' chr8.gff
```

The above example prints the first column of the file `chr8.gff`.

Sometimes the separator in some files is not `Space` nor `Tab` but
something else. We can use `-F` option to specify separators, or we can
use it to extract part of a file after some special character. Let's
assume we wanna extract gene_id which is contained in the 9th column of
the file `chr8.gff`. If we look carefully this information is contained
between `=` and `;` so we can use them as separators to extract it from
the file. As we mentioned before, we can specify separators using `-F`
option, and if we want to specify more than one we can separate them
with `|` (e.g. `-F"=|;"`):

```
cd ~/unix_intro/exercises/genes
awk -F"=|;" '{print $2}' chr8.gff
```

!!! question
    Using the above command as a template, how would you extract column with the symbol?

    ??? note "Click for Answer"
        We can simply modify the column we want to print out:
        ```
        awk -F"=|;" '{print $4}' chr8.gff
        ```
------------------------------------------------------------------------

## Conditional expressions in `awk`

| Operator | Meaning                     |
|----------|-----------------------------|
| `==`     | Is equal                    |
| `!=`     | Is not equal to             |
| `>`      | Is greater than             |
| `>=`     | Is greater than or equal to |
| `<`      | Is less than                |
| `<=`     | Is less than or equal to    |

`awk` scripting language supports **if conditional statement**.

    awk '{if ($4 > 146098183) print $0}' chr8.gff

We can change the `if` statement to a **condition** in order to shorten
the code:

    awk '$4 > 146098183 {print $0}' chr8.gff | head

## And/Or/Not

We can combine conditional expressions with the "or" or "and" operators:
`&&` and `||`, as well as the unary not operator: `!`.

-   AND (`&&`)
-   OR (`||`)\
-   NOT (`!`)

Now imagine that we need to extract the lines belonging to chromosome 8,
between the coordinates 100000 and 200000. We can do that like this:

```
cd ~/unix_intro/exercises/genes
awk '$1=="chr8" && $4 > 100000 && $5 < 200000' chr8.gff
```

!!! question "Task"
    Using the above command as a template, print all the lines between 5000000 and 10000000.

    ??? note "Click for Answer"
        ```
        awk '$4 > 5000000 && $5 < 10000000' chr8.gff
        ```
------------------------------------------------------------------------

## Doing operations with columns `awk`

We can use `awk` to do algebraic operations on columns.

To illustrate let's print *the first column* and *the sum of the fourth
and third*. We can **pipe** the output to `head` or `less`, to make it
easier to visualize:

```
cd ~/unix_intro/exercises/genes
awk '{print $1, $5-$4}' chr8.gff | head
```

------------------------------------------------------------------------

## Regular expressions in `awk`

`awk` can also be used to search by a *regular expression*. The syntax
for using regular expressions to match lines in `awk` is:
`word ~ /match/`, while the inverse of that is not matching a pattern:
`word !~ /match/`

For example, the following code will print all the lines in which the
symbol starts with *"MIR"*:

```
cd ~/unix_intro/exercises/genes
awk '$9 ~ /symbol=MIR/ {print $0}' chr8.gff | head
```

Now let's remove the header of the file:

```
cd ~/unix_intro/exercises/genes
awk '$0 !~ /#/' chr8.gff | head
```

or even shorter: `awk '!/#/' chr8.gff`

!!! question "Task"
    a)  Calculate the **length** of the gene **POU5F1B** in `chr8.gff` file.<br /><br />
    b) Once you calculated it, find the gene in `chr8.gff` file whose **gene_id** is equal to that number (i.e. length of POU5F1B).
    ??? note "Click for Answer"
        <br />a) for `awk '$9 ~ /POU5F1B/ {print $5-$4}' chr8.gff` the output is: **1584** 
        <br />b) Than we run `awk '$9 ~ /gene_id=1584/ {print $0}' chr8.gff` and find that gene CYP11B1 had gene_id=1584