# Basic built-in terminal commands


-Navigate your computer's file system along with base-level tasks such as create, copy, rename, and delete: <br>
    *Move around your directory (folder) structure: `cd` <br>
    *Create directories: `mkdir` <br>
    *Create files (and modify their metadata): `touch` <br>
    *Copy files or directories: `cp` <br>
    *Move files or directories: `mv` <br>
    *Delete files or directories: `rm` <br>

-Download files found at specific URLs: `curl`

-Search for fragments of text inside larger bodies of text: `grep`

-View a file's contents page by page: less, `cat`

Manipulate and transform streams of text (for example changing all the instances of `<div>s` in an HTML file to `<article>`): awk, tr, sed
<br>
<hr>

## Listing directory contents

### ls

    is for list the content of your directory
    shows you all folders and files that you have in the directory where you are on

<hr>

## Introducing command options

### ls -l

    In the case of ls, the -l (dash ell) option gives you a listing with one file or directory on each line, and a lot more information shown. Directories can be identified by looking for a letter "d" on the very left-hand side of the lines. Those are the ones we can cd into.<hr>
    Basically, the -l gives to you more detail about the files and folders that you have into a specific directory.

<hr>

### open terminal in vscode

    you need to press Ctrl + J
    and you can show or hide the terminal

<hr>

### Creating, copying, moving, removing

    There are a number of other basic utility commands that you'll probably end up using quite a lot as you work with the terminal. They are pretty simple, so we won't explain them all in quite as much detail as the previous couple.

    Have a play with them in a test directory you've created somewhere so that you don't accidentally delete anything important, using the example commands below for guidance:

`mkdir` — this creates a new directory inside the current directory you are in, with the name you provide after the command name. For example, mkdir my-awesome-website will make a new directory called my-awesome-website.

`rmdir` — removes the named directory, but only if it's empty. For example, rmdir my-awesome-website will remove the directory we created above. If you want to remove a directory that is not empty (and also remove everything it contains), then you can use rm -r instead (see below), but this is dangerous. Make sure there is nothing you might need inside the directory later on, as it will be gone forever.

`touch` — creates a new empty file, inside the current directory. For example, touch mdn-example.md creates a new empty file called mdn-example.md.

`mv` — moves a file from the first specified file location to the second specified file location, for example mv mdn-example.md mdn-example.txt (the locations are written as file paths). This command moves a file called mdn-example.md in the current directory to a file called mdn-example.txt in the current directory. Technically the file is being moved, but from a practical perspective, this command is actually renaming the file.

`cp` — similar in usage to mv, cp creates a copy of the file in the first location specified, in the second location specified. For example, cp mdn-example.txt mdn-example.txt.bak creates a copy of mdn-example.txt called mdn-example.txt.bak (you can of course call it something else if you wish).

`rm` — removes the specified file. For example, rm mdn-example.txt deletes a single file called mdn-example.txt. Note that this delete is permanent and can't be undone via the recycle bin that you might have on your desktop user interface.

<hr>
<br>

# Connecting commands together with pipes
The terminal really comes into its own when you start to chain commands together using the | (pipe) symbol. Let's look at a very quick example of what this means.

What if we wanted to quickly count the number of files and directories inside the current directory? ls can't do that on its own.

There is another Unix tool available called `wc`. This counts the number of words, lines, characters, or bytes of whatever is inputted into it. This can be a text file — the below example outputs the number of lines in myfile.txt:<br>
`wc -l myfile.txt`
<br>

But it can also count the number of lines of whatever output is piped into it. For example, the below command counts the number of lines outputted by the ls command (what it would normally print to the terminal if run on its own) and outputs that count to the terminal instead:<br>
`ls | wc -l`
<br>

Since ls prints each file or directory on its own line, that effectively gives us a directory and file count.

So what is going on here? A general philosophy of (unix) command line tools is that they print text to the terminal (also referred to "printing to standard output" or STDOUT). A good deal of commands can also read content from streamed input (known as "standard input" or STDIN).

The pipe operator can connect these inputs and outputs together, allowing us to build up increasingly more complex operations to suit our needs — the output from one command can become the input to the next command. In this case, ls would normally print its output to STDOUT, but instead ls's output is being piped into wc, which takes that output as an input, counting the number of lines it contains, and prints that count to STDOUT instead.

# A slightly more complex example
curl https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch -L -I | grep location | awk '{ print "https://developer.mozilla.org" $2 }'

<hr>

# Adding powerups
I already have Node js and prettier, so I don't need this.