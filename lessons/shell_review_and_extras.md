# Review and some extras on Linux Shell

>**Tip** - Remember since this is a new day, make sure you have downloaded the latest lesson.
```bash
$ cd ~/biocoding_2015
$ git pull
```



The shell that we have been using in Linux is known as the ['Bash shell'](https://en.wikipedia.org/wiki/Bash_%28Unix_shell%29). Let's review yesterday's introduction to the shell with some short challenges, and then take a quick look at a few extras. 

##Working from a distance

Do the following without using the ``cd`` command:

1.  Create the following
    * [x] A directory called ``test_directory`` on the Desktop
    * [ ] A  directory called ``sub_directory`` in the Desktop ``test_directory``
    * [ ] A file called ``file.temp`` in the above mentioned ``sub_directory``
2. Use ``ls`` with the recursive option to view the contents of the Desktop directories and files created. 
3. Create 20 empty files (1..20) using the ``touch`` command. End each file with the extension ``.txt``. 
    * [x] Use ``mv`` along with the wildcard ``*`` to move all the ``.txt`` files into your Desktop ``test_directory``
    * [ ] Use the ``cp`` command to copy all ``.txt`` files from ``test_directory`` to ``test_directory/sub_directory``

##History, grep, and piping

We have time for just a few more shell commands. As you learned yesterday, you can go back to previously used commands by pressing the *up* arrow button. There is another command that can let us see a more complete list, ``history``. Using this command, we get an output like this:

```bash
$ history
  512  mkdir test_directory
  513  mkdir test_directory/sub_directory
  514  touch test_directory/sub_directory/file.tmp
  515  history
```
Each of our commands is numbered. We can rerun any command by entering an ``!`` followed by the number of that command in the history list:

```bash
$ !515
  512  mkdir test_directory
  513  mkdir test_directory/sub_directory
  514  touch test_directory/sub_directory/file.tmp
  515  history
  516  history
  ```
Question, how many times in your history have you used the ``cd`` command? 

Perhaps you can count, but there is another way to find what were are looking for ``grep``. ``grep`` allows us to search a file for a word, character, number, pattern. Etc. 

To search a file use the ``grep`` command, followed by the search term (e.g. 'biology'), followed by the name of the file you wish to check. Try this command:
```bash
$ grep 'biology' ~/biocoding_2015/watson.txt
```
``grep`` returns each line in the file that matches your search. Play with the grep command by changing your search terms. 

You can combine programs at the shell using the ``|`` character. Try this command and explain what you think is going on...

```bash
$ grep 'biology' ~/biocoding_2015/watson.txt | wc
```
What's happening with the ``|`` and what does ``wc`` do?

###how many times in your history have you used the ``cd`` command?

Use grep to and ``|`` to try and answer this question. 

