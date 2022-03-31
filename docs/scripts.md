# Shell Scripts

We can save commands for later re-use in files called **shell scripts**.

Let's start by going back to `~/unix_intro/exercises/creatures` and
creating a new file, `my_first_sh_script.sh` which will become our shell
script:

    ~/unix_intro/exercises/creatures
    nano my_first_sh_script.sh

The command `nano my_first_sh_script.sh` opens creates an empty file
`my_first_sh_script.sh`. Now, we can use `nano`to directly type in the
file - we'll simply insert the following line:

    head -n 15 unicorn.dat | tail -n 5

This is a variation on the pipe we constructed earlier. Keep in mind, we
are not running it as a command just yet: we are putting the commands in
a file `my_first_sh_script.sh` using `nano`. Once we are done typing, we
can save the file (`Ctrl+O`), and exit `nano` (`Ctrl+X`).

Alternatively, we can simply create a file with `echo` command like
this:

    echo "head -n 15 unicorn.dat | tail -n 5" > my_first_sh_script.sh

Check with `ls` if we successfully created a file called
`my_first_sh_script.sh`.

Once we have saved the file, we can ask the shell to execute the
commands it contains. Our shell is called `bash`, so we run the
following command:

    bash my_first_sh_script.sh

What if we want to select lines from an arbitrary file? We could edit
`my_first_sh_script.sh` each time to change the filename, but that would
probably take longer than typing the command out again in the shell and
executing it with a new file name. Instead, let's edit
`my_first_sh_script.sh` and make it more versatile. Open
`my_first_sh_script.sh` with `nano` and replace `unicorn.dat` with the
special variable called `$1`:

    head -n 15 "$1" | tail -n 5

Inside a shell script, `$1` means **the first filename (or other
arguments) on the command-line**. We can now run our script like this:

    bash my_first_sh_script.sh octane.pdb

We still need to edit `my_first_sh_script.sh` each time we want to
adjust the range of lines, though. Let's fix that by using the special
variables `$2` and `$3` for the number of lines to be passed to `head`
and `tail` respectively. Open `my_first_sh_script.sh` with `nano` and
correct the code to look like this:

    head -n "$2" "$1" | tail -n "$3"

Now we can test it (extract first 2 lines with `head` and only the last
one of those 2 with `tail` to get classification):

    bash my_first_sh_script.sh octane.pdb 2 1

So it seems that now script works, but it may take the next person who
reads `my_first_sh_script.sh` a moment to figure out what it does. We
can improve our script by adding some **comments** (A comment starts
with a `#` character and runs to the end of the line) at the top where
we can describe what does this script does. Open `my_first_sh_script.sh`
with `nano` and add comments at the top to look like this:

    # Select desirable lines from a file.
    # Usage: bash my_first_sh_script.sh filename end_line num_lines
    head -n "$2" "$1" | tail -n "$3"

::: {.alert .alert-warning}
<strong>TASK:</strong> <br />

------------------------------------------------------------------------

Previously we used `awk` to print all the lines between 5000000 and
10000000. Let's make this `awk` script into bash script where we can
define which lines we want to print based on the interval which we can
change. To do so:

1.  Move to `~/unix_intro/exercises/genes`
2.  Make new bash script with `nano` named `print_lines_between.sh`
3.  Inside write the code which we can use on any file and in such a way
    that we can select the interval whenever we run the script.
4.  Try your script with different `.gff` files and with different
    intervals (e.g. between 100000 and 200000, or between 500000 and
    1500000 for `chrX.gff` and `chr9.gff`).

Tip: We have to know that `awk` and `bash` have different ways of
calling variables so just as a hint - we will have to use `awk` option
that passes `bash` variables to `awk` script `-v`.

------------------------------------------------------------------------

<details>

<summary>

<strong>Click for Answer</strong>

</summary>

our `print_lines_between.sh` should contain this code:
`awk -v from=$2 -v to=$3 '$1=="chr8" && $4 > from && $5 < to' $1`.

We are passing `bash` variable `$2` to shell with `-v` option and by
defining that term `from` is a variable within `awk` script, the same
logic applies for for `-v to=$3`.

</details>
:::

------------------------------------------------------------------------

<br /><br /><br />
