# Intro to Linux Shell

[Linux](https://en.wikipedia.org/wiki/Linux) is the world's most popular operating system - if you are thinking about [supercomputing](https://en.wikipedia.org/wiki/Supercomputer), science, and most of the world's internet servers. Most people are familiar with Windows - the Microsoft [Operating System](https://en.wikipedia.org/wiki/Operating_system), or MAC OS for Apple. However, according to the [Linux Foundation](http://www.linuxfoundation.org/about/about-linux):
> "98% of the world’s super computers, most of the servers powering the Internet, the majority of financial trades worldwide and tens of millions of Android mobile phones and consumer devices. In short, Linux is everywhere."

In this course, we will not have to go very deep into how to use Linux. However, we will learn a decent amount about how to work with Linux at the [command line](https://en.wikipedia.org/wiki/Command-line_interface). Fortunately, many of the Python skills we will most study in the course are very relevant or have parallels in Linux. In order to use Python we will also need to get started with our Linux machines. 

##Opening the terminal

To get started, we will open the terminal on the [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29) operating systems we will be working with. Ubuntu is the most popular version of Linux (or Linux 'Distro') for people using Linux personal computing applications. 

###Open the terminal

1. On the Desktop (Dashboard), the topmost icon will allow you to search. Search for 'terminal' and select the terminal icon

   >alternatively you can also use the shortcut Ctrl +Alt + T
   
The first thing you will see at the terminal is the 'prompt' this '$' icon and cursor indicate that the computer is ready to accept your command:

```bash
biocoder@biocoder:~$
```
Usually the prompt the prompt will indicate three important pieces of information:

* The name of the user (you/ your account name)
* The name of the computer
* The location (working directory) you are located at


In this case the prompt is telling you the following:

* **User Name:** biocoder
* **Computer Name:** @ biocoder 
* **Location:** (Working directory):~ ('~' is symbol for 'home')

As you will learn, Linux is full of abbreviations. During the early days of computing, memory was very expensive. In 1957 1MB of memory - enough to store 15-20 emails (no attachments), or 3-4 Facebook posts with pics[*](http://bmobile.co.tt/faqs/what-can-i-do-with-1-megabyte-of-data/) cost approximately $411,041,792; in 2015 1MB costs about $0.0056. [*](http://www.jcmit.com/memoryprice.htm). So as a rule in Linux, and command line competing **less typing is best.**

We can verify the above statements by trying out our first commands. 

####Exercise I - Get details about your computer

Type the following commands and see what your output is

```bash
$ whoami
```
```bash
$ pwd
```
```bash
$ hostname
```
> **Tip:** When entering commands from the documentation/tutorial never enter the '$' prompt symbol. Just enter what comes after it. 

What do you think these commands do? First, let's check that you got the following outputs:

```bash
biocoder@biocoder:~$ whoami
biocoder
biocoder@biocoder:~$ pwd
/home/biocoder
biocoder@biocoder:~$ hostname
biocoder
```

Let's talk about what each of these commands are doing:

* ``whoami`` - This command outputs the username
* ``pwd`` - This command (print working directory) outputs the current working directory. When you work in Linux, it is assumed that any commands (or any inputs) are **located in** the working directory, unless otherwise specified
* ``hostname`` - This command outputs the full name of the computer you are working on. 

Sadly, this is probably the last time you will be using these commands (outside of taking or teaching another Linux course). However, as simple as these commands are, they are still useful. Let me try to show you this after teaching you two new commands. 

>**FYI:** What happens when you type ``whoami``\*- when we type `whoami` the shell (terminal):
>1.  finds a program called `whoami`,
2.  runs that program,
3.  displays that program's output, then
4.  displays a new prompt to tell us that it's ready for more commands.
\*from [https://github.com/swcarpentry/shell-novice](https://github.com/swcarpentry/shell-novice)

####Exercise II - Exploring the neighborhood 
Try the following command 

```bash
$ cd ~/Desktop
```
The ``cd`` command allows you to change directories. In this case the command has three important components

* **``cd``:** This is the name of the command (change directory)
* **``  ``:** Space - this is very important, if you are missing a space, your command will not work!
* **~/Desktop:** The is the destination, or the directory you want to change into. This already could be broken down further:
    * ~ - as encountered before, this symbol means 'home'
    * / - this symbol here mean one level beyond the location to the left
    * ``Desktop`` - this is simply the directory called 'Desktop' on your computer

try ``pwd`` again and this is what you should find:

```bash
biocoder@biocoder:~$ cd ~/Desktop
biocoder@biocoder:~/Desktop$
```
Notice two important things that have happened here:

1. Linux did not give you any special output message like 'Now moving to the Desktop' or 'Successfully changed directory' - in Linux **No news is good news** - in most cases as long as you get some prompt ending in '$' you have been successful and the computer is ready for the next command
2. Notice that the command prompt has changed. You now can see that you really have changed directories because the prompt now shows where you are located **relative** to the home ('~') directory. 

```bash
biocoder@biocoder:~/Desktop$
```

#### Understanding Paths

The word **relative** was bolded above, because another important point in Linux is understanding 'where' you are. Think about some of the following ways you might use to describe your location:

* "I'm at home"
* "I'm at school"
* "I'm at the store"
* "I am at 1600 Pennsylvania Ave"
* "I'm at 40.6900037,-74.0448958"

Each of these are increasingly specific, but all involve a certain amount of relativity. To your family and friends your home is probably very well defined. 'The store' is probably very ambiguous assuming you aren't living in a town in the middle of nowhere. "40.6900037,-74.0448958" is probably about as specific a location as you can get, but still assumes we are talking about coordinates on the planet Earth.

Linux, is actually much simpler than the examples I have just given. You have two choices, and like all command line computing - both leave little room for ambiguity

**Absolute Paths**

These paths (or locations) always start with '/' (called 'root') which is the all-encompassing Linux directory (every other directory must trace its way back to '/'). To see your absolute path, just enter ``pwd``. We'll use two commands to 1) change our working directory back to home so we get the same output and the 2)``pwd`` so we can see our absolute path:

```bash
biocoder@biocoder:~/Desktop$ cd ~
biocoder@biocoder:~$ pwd
/home/biocoder
biocoder@biocoder:$
```
First, hopefully you understood what ``cd ~`` means, if not, please talk to the people next to you! Secondly, you see the absolute path for the home directory of the bicolored user is ``/home/biocoder``

**Relative Paths**

Relative paths are easy - you have already seen how they are displayed on your screen. For example ``~/Desktop`` is equivalent to ``/home/biocoder/Desktop``. So why the need for relative paths? Well, as stated above **less typing is best**, or as we will say from now on **less best.** Rather than showing a prompt like this:

```bash
biocoder@biocoder:/home/biocoder/Desktop$
```
Linux simply omits the unnecessary info - of course you are home! Where else would you be?!

There is one more important abbreviation when it comes to paths, that is ``.``. ``.`` means 'here' or 'whatever directory you are now in.' for example, what happens when you try following command?

```bash
biocoder@biocoder:~/$ cd .
```
Well, the next prompt you get back should show that you have changed into the directory you were already in. As silly as this is, its also quite useful. For example if I did this:

```bash
biocoder@biocoder:~/very/very/very_long_path$ cd ~/very/very/very_long_path
```
I could just omit all that typing any use ``cd .``; they are equivalent. 

``.`` is a lot more useful than this. In most cases, we will use the ``.`` to mean 'relative to here' where 'here' is always the directory I am currently in. We may use this more later, but let's learn just a few more commands first. 


#### Creating directories

To create a directory we use the ``mkdir`` command. Try the following, and note first that we want to change into our home directory:

```bash
biocoder@biocoder:~$ cd ~
biocoder@biocoder:~$ mkdir temp_dir
```
We have just created a new directory called ``temp_dir``

How do we know that. Use the ``ls`` command to list, all the directories that your current working directory contain:

```bash
biocoder@biocoder:~$ ls
Desktop      Music    temp_dir
Documents    Pictures
Downloads    Public
```
Depending on your setup, there may be less or fewer directories, but among them will be your new 'temp_dir' directory. 

####Exercise III - Setting up your project

To prepare us for the week, lets setup a few directories that we can use to organize our work. Use the ``mkdir`` command to create the following directories:

/home/biocoder/camp_projects<br>
/home/biocoder/camp_projects/data<br>
/home/biocoder/camp_projects/docs<br>
/home/biocoder/camp_projects/results<br>

**Note:** Before creating these directories, take 3-5 minutes to discuss with your neigbhor/partner how you will create these directories. Is there any way to do this using the **less best** principle?

####Exercise IV - Options

So far, most of the commands we have been using so far have had the following structure:

```bash
$ <command name> <input>
```

For example in ``$cd ~/Desktop`` ``cd`` is the command and ``~/Desktop`` was the input. It was not emphasized, but as you know, the space between those two items is also necessary. However, many programs also have some options (or parameters) that can alter their behavior. For example try this:

```bash
biocoder@biocoder:~$ mkdir /home/biocoder/camp_projects/data/tmp1/tmp2
mkdir: cannot create directory '/home/biocoder/camp_projects/data/tmp1/tmp2
' : No such file or directory
```
``mkdir`` if ``/home/biocoder/camp_projects/data/tmp1/`` existed, ``mkdir`` would go ahead and make ``tmp2``. However, since one of the directories along the path to making ``tmp2`` does not exist, ``mkdir`` gives up. Using the ``-p`` option, I can force ``mkdir`` to make the desired directory, as well as any needed directories. Try:

```bash
biocoder@biocoder:~$ mkdir -p /home/biocoder/camp_projects/data/tmp1/tmp2
```
``mkdir`` makes this with no problem! how can you check? Let's combine a bit of what we learned before. Use the ``ls`` command to verify that ``tmp2`` has been created. 

####Exercise V - Instructions

How do we figure out what are the options/parameters a program has? There is a program for that: ``man``

**Questions:** 
* What are some of the options for the ``ls`` command?
* How can you use ``ls`` to tell the difference between a file and a directory?

**Tip:** When you are reading a manual you can use the 'q' key to quit the manual. You can also use the arrow or space key to move through the manual. 

Recall earlier how we mentioned that commands have a defined structure:

```bash
$ <command name> <input>
```
The brackets in this structure are meaningful. In general '[ ]' indicates that item is optional. Often , you will see the '< >' brackets to indicated an item is required. Look at the manual for the ``cd`` command. Focusing on the synopsis, what do you think will happen with the following command:

```bash
$ cd 
```
What about? 

```bash
$ ls
```
what about? 

```bash
$ cp
```
Looking at the manual 

```bash
NAME
     cp -- copy files

SYNOPSIS
     cp [-R [-H | -L | -P]] [-fi | -n] [-apvX] source_file target_file
```
In this case most of the parameters are optional (in [brackets]), but the source file (what you want to copy) and the target file (where you want to copy to). For more details, see this [Beginners guide to man pages](http://www.tfug.org/helpdesk/general/man.html). 

####Exercise VI - Final file manipulations

There are hundreds of Linux programs. Probably 15-20 of them make up what most users need on a day-to-day basis. Here are just a few more commands, figure out what they do using the man pages and try them out. 

> **Tip:** Use the ``touch`` command - with ``touch`` you can create a file, just give touch the name of the file you would like to create (e.g. ``touch temp_file.txt``)

**Try the following commands**

* cp
* mv
* rm

##Wrap up

There are many more Linux tips and tricks. We will pick some up through the course as needed. Linux and the command line shell are really powerful for doing repetitive tasks quickly. For example, in just about the same number of characters you can create one directory 

```bash
$ mkdir one_directory
```
you can also create 100 directories

```bash
$ mkdir {1..100}_directory
```
You can create 100 files

```bash
$ touch temp_file_{1..100}.txt
```
and make a backup copy of those files

```bash
for file in *
> do
> cp $file {$file}_backup.txt
> done

```
This last command (a [for loop](https://en.wikipedia.org/wiki/For_loop)) may seem complex right now, but hopefully by the end of the course you will see how easy it is!


