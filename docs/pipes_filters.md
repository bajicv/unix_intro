# Pipes and Filters

Now that we know a few basic commands, we can finally look at the
shell's most powerful feature: the ease with which it lets us combine
existing programs in new ways. We'll start with the directory called
`~/unix_intro/exercises/multiplefiles` that contains 50 randomly
generated files.

------------------------------------------------------------------------

## Redirect `>`

The greater than symbol `>`, tells the shell to redirect the command's
output to a *file* instead of printing it to the *screen*.

```{bash, echo = T, eval=F}
cd ~/unix_intro/exercises/multiplefiles
wc -l *.txt > ~/lengths.txt
```

------------------------------------------------------------------------

## Append `>>`

We have seen the use of `>`, but there is a similar operator `>>` which
works slightly differently. We'll learn about the differences between
these two operators by printing some strings. We can use the `echo`
command to print strings e.g.

```
echo 'I absolutely adore WHALES and echo command helps me in expressing my love for them!'
```

Now run each of the commands twice to reveal the difference between `>`
and `>>`:

```
echo 'I love whales!' > ~/redirect.txt
echo 'I love whales!' > ~/redirect.txt
```

and:

```
rm ~/append.txt
echo 'I love whales!' >> ~/append.txt
echo 'I love whales!' >> ~/append.txt
```

Now let's see what's in the files:

```
cd ~
head redirect.txt append.txt 
```

In the first example with `>`, the string *"I love whales!"* is written
to `redirect.txt`, but the file gets **overwritten** each time we run
the command.

In the second example with `>>`, the string *"I love whales!"* is
written to `append.txt`, but the string is **appended** to the file
every time we repeat the command with the same file name at the end.

------------------------------------------------------------------------

## Pipe `|`

The vertical bar `|` between the two commands is called a **pipe**. It
tells the shell that we want to use the output of the command on the
left as the input to the command on the right.

Nothing prevents us from chaining pipes consecutively. That is, we can,
for example, send the output of `wc` directly to `sort`, and then the
resulting output to `head`.

```
cd  ~/unix_intro/exercises/multiplefiles
wc -w *.txt | sort -n | head -n 1
```

------------------------------------------------------------------------

## Filters

A **filter** is a program (e.g. `wc`, `sort`, `grep`, `uniq`, `cat`,
`head`, `tale`...) that transforms a stream of input into a stream of
output. Almost all of the standard Unix tools can work this way: unless
told to do otherwise, they read from standard input, do something with
what they've read, and write to standard output.

------------------------------------------------------------------------