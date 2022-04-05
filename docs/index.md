# Index

This is tutorial for UNIX.

!!! question "Task"
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

    ??? note "Click for Tip" 
        We have to know that `awk` and `bash` have different ways of calling variables so just as a hint - we will have to use `awk` option that passes `bash` variables to `awk` script `-v`.

    ??? note "Click for Answer"
        our `print_lines_between.sh` should contain this code:
        ```
        awk -v from=$2 -v to=$3 '$1=="chr8" && $4 > from && $5 < to' $1
        ```

        We are passing `bash` variable `$2` to shell with `-v` option and by
        defining that term `from` is a variable within `awk` script, the same
        logic applies for for `-v to=$3`.