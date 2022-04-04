# Loops

**Loops** are a programming construct which allows us to repeat a
command or set of commands for each item in a list. As such they are key
to productivity improvements through automation. Similar to
**wildcards** and **tab completion**, using loops also reduces the
amount of typing required (and hence reduces the number of typing
mistakes).

Suppose we have several hundred genome data files named `basilisk.dat`,
`minotaur.dat`, and `unicorn.dat`. For this example, we'll use the
`~/unix_intro/exercises/creatures` directory which only has three
example files, but the principles can be applied to many many more files
at once.

The structure of these files is the same: the common name,
classification, and date of the update are presented on the first three
lines, with DNA sequences on the following lines. Let's look at the
files:

```
cd ~/unix_intro/exercises/creatures
head -n 5 basilisk.dat minotaur.dat unicorn.dat
```

We would like to print out the *classification for each species*, which
is given on the second line of each file. For each file, we would need
to execute the command `head -n 2` and *pipe* this to `tail -n 1`. We'll
use a **loop** to solve this problem.

Before we do it let's get familiar with the **general form of a loop**:

```
for thing in list_of_things
do
    operation_using $thing    # Indentation within the loop is not required, but aids legibility
done
```

Now we can apply this to our example like this:

```
for filename in basilisk.dat minotaur.dat unicorn.dat 
do 
    head -n 2 $filename | tail -n 1 
done
```

??? note "Click to see the output"
    ```
    CLASSIFICATION: basiliscus vulgaris
    CLASSIFICATION: bos hominus
    CLASSIFICATION: equus monoceros
    ```

The shell **prompt** changes from `$` to `>` and back again as we were
typing in our loop. The second prompt `>`, is different to remind us
that we haven't finished typing a complete command yet. A semicolon `;`,
can be used to separate two commands written on a single line (i.e.
`for filename in basilisk.dat minotaur.dat unicorn.dat; do head -n 2 $filename | tail -n 1; done`).

When the shell sees the keyword `for`, it knows to repeat a command (or
group of commands) once for each item in a list. Each time the loop runs
(called an iteration), an item in the list is assigned in sequence to
the **variable**, and the commands inside the loop are executed, before
moving on to the next item in the list. Inside the loop, we call for the
variable's value by putting `$` in front of it. The `$` tells the shell
interpreter to treat the variable as a variable name and substitute its
value in its place, rather than treat it as text or external command.

In this example, the list is three filenames: `basilisk.dat`,
`minotaur.dat`, and `unicorn.dat`. Each time the loop iterates, it will
assign a file name to the variable `filename` and run the `head`
command.

The first time through the loop, `$filename` is `basilisk.dat`. The
interpreter runs the command `head` on `basilisk.dat` and pipes the
first two lines to the `tail` command, which then prints the second line
of `basilisk.dat`.

For the second iteration, `$filename` becomes `minotaur.dat`. This time,
the shell runs `head` on `minotaur.dat` and pipes the first two lines to
the `tail` command, which then prints the second line of `minotaur.dat`.

For the third iteration, `$filename` becomes `unicorn.dat`, so the shell
runs the `head` command on that file, and `tail` on the output of that.
Since the list was only three items, the shell exits the for loop.

When using variables it is also possible to put the names into curly
braces to clearly delimit the variable name: `$filename` is equivalent
to `${filename}`, but is different from `${file}name`. You may find this
notation in other people's programs.

We have called the variable in this loop `filename` in order to make its
purpose clearer to human readers. The shell itself doesn't care what the
variable is called; if we wrote this loop as:

```
for x in basilisk.dat minotaur.dat unicorn.dat
do
    head -n 2 $x | tail -n 1
done
```

or:

```
for temperature in basilisk.dat minotaur.dat unicorn.dat
do
    head -n 2 $temperature | tail -n 1
done
```

it would work exactly the same way. Don't do this. Programs are only
useful if people can understand them, so meaningless names (like `x`) or
misleading names (like `temperature`) increase the odds that the program
won't do what its readers think it does.

------------------------------------------------------------------------
