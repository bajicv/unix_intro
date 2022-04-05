# Screen manager

`screen` is a command-line program that we can use to open multiple
virtual terminals ("windows") inside the same session. Processes that we
started running in `screen` will continue to run when their window is
not visible, and even if we get disconnected! This comes very handily
when we are working via ssh on remote machines.

Imagine that we have to run a program that would require 3 full days to
complete the task. If we would run it without `screen` session this
would require us to stay online logged-in for the entire time that the
program needs to complete its task. Instead, we can create a `screen`
session from which we can log out at any time and later on switch off
our local machines, and come back later to the same `screen` session in
3 days or whenever we want to.

Also, imagine that you would like to open a few tabs when you are
logged-in on the remote machine. Whenever you try that you will be
redirected to your local machine terminal and you would have to log in
again and to move yourself to the desired location in the file system.
This can be boring and time-consuming and `screen` can save us some time
there too! We can have multiple "windows" within our `screen` session,
and whenever we open a new "window" we will continue from the same place
where we opened our session.

------------------------------------------------------------------------

## Starting screen session

To **start named** `screen` session with name `my_first_screen_session`
type:

    screen -S my_first_screen_session

P.S. you can also start an unnamed session by just typing `screen` but
we recommend you to name your sessions.

------------------------------------------------------------------------

## Screen commands

When within the `screen` session we can perform tasks that we would do
on a normal terminal (e.g. running programs, doing `ls`, changing
directories or what every you have to do) but also we can direct our
commands to the `screen` program itself (e.g. we can tell `screen`to
move from one to another window, or close screen session, rename and
many others).

By pressing `Ctrl+a` (i.e. while holding down the `Ctrl` key type the
letter `a`) we will redirects our commands to the `screen` program
itself and commands that follow `Ctrl+a` will determine the action that
`screen` program will perform.

Below are some of the most frequently used `screen` commands. Please
note that here we are referring to `a` as a symbol for pressing "Taster
"A" (i.e. `a` = `A`), while with `A` we refer to an action of pressing
"Taster A" together with "Shift" (i.e. `A` = `A`+`Shift`):

| Command           | Explanation                                        |
|-------------------|----------------------------------------------------|
| `Ctrl+a` `c`      | Create a new screen window                         |
| `Ctrl+a` `n`      | Go to the next screen window                       |
| `Ctrl+a` `p`      | Go to the previous screen window                   |
| `Ctrl+a` `d`      | Detach from the screen session                     |
| `Ctrl+a` `k`      | Close the current screen window                    |
| `Ctrl+a` `\`      | Kill all windows and terminate screen              |
| `Ctrl+a` `"`      | List all window                                    |
| `Ctrl+a` `0`      | Switch to window 0 (by number)                     |
| `Ctrl+a` `A`      | Rename the current window                          |
| `Ctrl+a` `S`      | Split current region horizontally into two regions |
| `Ctrl+a` `|`      | Split current region vertically into two regions   |
| `Ctrl+a` `Tab`    | Switch the input focus to the next region          |
| `Ctrl+a` `Ctrl+a` | Toggle between the current and previous region     |
| `Ctrl+a` `Q`      | Close all regions but the current one              |
| `Ctrl+a` `X`      | Close the current region                           |

------------------------------------------------------------------------

## Detaching from screen session

We can **detach** from the screen session at any time by typing:
`Ctrl+a` and `d` After we detach from the screen session all the program
running in the screen session will continue to run.

------------------------------------------------------------------------

## Renaming screen session

To **rename** an existing session open it first, and once inside the
session press `Ctrl+a` then type `:sessionname my_session_name` and
press `Enter`.

------------------------------------------------------------------------

## Resuming and listing running screen sessions

To **resume** `screen` session use the following command:

    screen -r

In case you have multiple screen sessions running on your machine, you
will need to append the screen session name after the `-r` option.

We can **list** the current running screen sessions with:

```
screen -ls
```
```
There are screens on:
        30285.amazing_whales    (04/17/2020 07:19:10 AM)        (Detached)
        30275.love_whales       (04/16/2020 09:28:50 AM)        (Detached)
        28591.pts-0.evop-login  (04/14/2020 08:04:53 AM)        (Detached)
3 Sockets in /run/screen/S-vladimir_bajic.
```

If we would like to resume screen called `30275.love_whales`, then we
would type:

    screen -r love_whales

------------------------------------------------------------------------

## Quitting screen sessions

When in screen session we can **quit** it (i.e. kill all windows and
terminate screen) with this command: `Ctrl+a` `\` or `Ctrl`+`a` then
type `:quit`

When deatached from screen session we can **quit** it:

    screen -X -S my_first_screen_session quit

------------------------------------------------------------------------

## Getting help

When in `screen` session type `Ctrl+a` and `?`. This will show us
commands or parameters on screen.

When outside `screen` you can check for the manual page of `screen`
command by typing: `man screen`, or you can check the *help page* of
`screen` command with `screen --help`.
