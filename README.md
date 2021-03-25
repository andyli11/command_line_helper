## A Resource Sheet for Understanding the _Command Line Interface_ (CLI).

This guide utilizes the _Unix_ command line: a family of operating systems including _Andriod, Linux, iOS, and macOS._ 

![image](https://user-images.githubusercontent.com/65037987/110254989-94342c80-7f5f-11eb-96cb-4f3704351d4c.png)

To print something onto the _standard output_, enter the command `echo` <string>. In this case, the _standard output_ is the terminal window. 
```bash
$ echo hi
hi 
```

To leave the current line and go to a new line, hit `Ctrl-C or Command-C`. This is especially useful to get out of tough situations. A useful mneumonic is to think of 'C' as a cancel button to stop the current command. 
```bash
$ ech oops I made a typo  # using Ctrl-C to leave the current line and go to the next
$ 
```

To display data about a command, enter the command `man` <command>. You can also run `$ man man` because man itself is a command. 
```bash
$ man echo    # display data about the command echo
```

To recall the previous command, enter the up arrow `↑`. To recall the furthest command, enter the down arrow `↓`.
```bash
$ echo tree
tree
$ echo tree   # using ↑ returns previous command
```

Another way to run the previous command is to enter `!!`. In software development, `!` is pronounced "bang" and `!!` is "bang bang". To enter the last command with certain characteristics, enter `!`<string>. For example, `!curl` recalls the last instance of `curl`.
```bash
$ !!
tree
$ !echo       # recalls last instance of echo
tree
$ !e          # short form works because the only command with e is echo
tree
```         

To search for a past command, hit `Ctrl-R or Command-R`. Then, type characters that match the command. This functionality is similar to searching a document with `Ctrl-F or Command-F`.
```bash
$ (reverse-i-search)`e': echo hi  # using Ctrl-R brings up the reverse search option
hi
```

To go to the front of a line, hit `Ctrl-A or Command-A`. To go to the end of the line, hit `Ctrl-E or Command-E`. These allow quick access instead of having to use `←` multiple times to go to the front of the line. To remove all contents from the line, use `Ctrl-U or Command-U` which __does not__ create a new line like `Ctrl-C or Command-C`. 
```bash
$ orange 
$ echo orange # using Ctrl-A to go to the front and add echo to fix command
$ asdfghjkl 
$             # using Ctrl-U to clear to the beginning of the line. 
```

To clear the screen of the command line interface, enter the command `clear` or hit `Ctrl-L or Command-L`. To exit the terminal window, enter the command `exit` or hit `Ctrl-D or Command-D`.
```bash
$ echo blank
blank
$            # using Ctrl-L to clear the terminal window
$ exit       # using Ctrl-D to exit the terminal window
```

To create a file and input a string, enter the redirect operator `>` <file>. If the file does not exist, it will create it. If the file exits, it will overwrite the information in the file. 
```bash
$ echo "strawberry banana smoothie" > yummy.txt
```

To print out the contents of the file, enter the command `cat` <file>.
```bash
$ cat yummy.txt
strawberry banana smoothie
```

To add another line to the text file, enter the append operator `>>` in place of the redirect operator `>`. If the file does not exist, it will create it. If the file exists, it will append the string to a new line. 
```bash
$ echo "red bean scores" >> yummy.txt
$ cat yummy.txt
strawberry banana smoothie
red bean scores 
```

To compare two files, similarly to comparing changes in _Git_, enter the command `diff` <f1> <f2>.
```bash
$ echo "strawberry banana smoothie" > drinks.txt
$ echo "chocolate milk" >> drinks.txt
$ diff yummy.txt drinks.txt
2c2
< red bean scores
---
> chocolate milk
```

To list all files and directories except _hidden_ files, enter the command `ls`. The command `ls` supports the wildcard character `*` called `star` that filters results based on the given argument. 
```bash      
$ ls *.txt    # *.txt (read "star dot t-x-t") finds any string followed by .txt
yummy.txt
drinks.txt
```

`ls` has 3 optional forms: 
* __long form__ is the flag `-l`. This shows the size of the file in bytes and latest time of update.  
* __reverse time__ of modification in long format is the flag `-rtl`. The flag can be separated from compact form to `-r -t -l` to represent reverse-order, time of modification, and the long format. The order of flags is irrelevant, hence `-t -r -l` and `-trl` is equivalent.     
* __hidden__ files and directories are identified with a `.` and are found with the flag `-a`. This can help identify git files such as .gitignore and its components.
```bash      
$ ls -rtl *txt   
-rwx------+ 1 andys andys 37 Mar 24 05:15 yummy.txt*
-rwx------+ 1 andys andys  3 Mar 24 05:16 drinks.txt*
$ echo "*.txt" > .gitignore
$ cat .gitignore
*.txt
$ ls -rtl  
.gitignore
yummy.txt
drinks.txt
```

To change directories, enter the command `cd` followed by the name of the directory. `cd` and `ls` are commonly used in cohesion to view files and directories after changing into another directory. 
```bash
$ ls
Desktop
yummy.txt
drinks.txt
$ cd Desktop/
```

To create a file, enter the command `touch` <file>. 
```bash
$ touch foo.txt 
```

To rename a file, enter the command `mv` <old> <new>. 
```bash
$ echo "foo" > bar
$ mv bar bar.txt
$ ls
bar.txt
```

To copy a file, enter the command `cp` <old> <new>. 
```bash
$ cp bar.txt baz.txt
$ diff bar.txt baz.txt
$
```

To delete a file, enter the command `rm` followed by the file name. `rm` permanently deletes the item. On a non-unix system, there is no confirmation for removals with `rm`. The reason there is confirmation on unix systems is because `rm` is an alias for `rm -i` to provide better security. However, to overrride the implicit option `-i`, enter the flag `-f` to force the deletion. This is especially common using the wildcard `*` to delete multiple files without having to confirm each one. 
```bash
$ rm bar.txt
remove bar.txt? y
$ ls bar.txt
ls: cannot access 'bar.txt': No such file or directory
```

Tab completion compeltes the word if there is a unique match in the system. If there are multiple solutions, hitting tab again would list out the solutions. This search is not case-sensative. 
```bash
$ cat y⇥     # using tab completetion yields yummy.txt 
starwberry banana smoothie
red bean scores
```

To check if a command exists on the system, enter the command `which` <command>. If the command exits, the location of the command will be displayed. Otherwise, it may be beneficial to download said command.
```bash
$ which echo
/usr/bin/echo
```

To download a file from an URL, enter the commmand `curl` <url>.
```bash
$ curl -OL cdn.learnenough.com/sonnets.txt
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 95635  100 95635    0     0  95635      0  0:00:01 --:--:--  0:00:01  667k
```

To get data on the file, enter the command `wc` <file>.
```bash
$ wc sonnets.txt
2620 17670 95635 sonnets.txt  # lines, words, size in bytes, name 
```

To view the first 10 lines of a file, enter the command `head` <file> and for the last 10 lines, enter the command `tail` <file>. We can also combine these commands with the redirect operator `>`.
```bash
$ head sonnets.txt  # display first 10 lines  
$ tail sonnets.txt > sonnets_tail.txt
$ wc sonnets_tail.txt
 10  77  425  sonnets_tail.txt
```

To avoid making a new file like above, there is the _pipes_ techique `|`. 
```bash
$ tail sonnets.txt | wc
     10      77     425  # lines, words, size in bytes
```

To select a specific number of lines, enter the flag `-n`, with n representing the number of lines. Tip: this can be discovered using `$ man head`.
```bash
$ head -18 sonnets.txt | tail -1  # retrives the last line of the first sonnet 
To eat the world's due, by the grave and thee.
```

To look at a file in more depth, enter the command `less` that can be used to navigate through the file in serveral ways. To move up and down 1 line at a time, hit the arrow keys or the spacebar. To move up and down 1 page at a time, hit `Ctrl-F or Command-F` and `Ctrl-B and Command-B`. To quit `less`, hit `q`. To search for a specific substring, enter `/` <string>. If the string occurs, the first occurance will be highlighted. If there are multiple instances, then hit `n` to navigate to the next match, or `N` to navigate to the previous match. To move to the end of the file, hit `G`, and to move to the beginning, hit `1G`. `man` uses `less` so the following inputs will also work. 
```bash
$ less sonnets.txt
```

To search for a substring directly without using `less`, enter the command `grep` <string> <file>. `grep` is case-sensitive by default. To find the option to ignore case-sensitivity, enter `$ man grep`, then `/case`, and the result is the flag `-i`. Fun fact: `grep` stands for _globally search a regular expression and print_ and comes from a pattern-matching system called _regular expressions_ or _regexes_. 
```bash
$ grep rose sonnets.txt  # display all lines with the occurance of rose
$ grep rose sonnets.txt | wc 
     10      82     419  # 10 lines contain rose
```

Example: find lines that contain words that start with "ro", have letters inbetween, and end with "s".
```bash
$ grep ' ro[a-z]*s ' sonnets.txt  # [a-z] is a regular expression for any letter
To that sweet thief which sourly robs from me.
Die to themselves. Sweet roses do not so;
When rocks impregnable are not so stout,
He robs thee of, and pays it thee again.
The roses fearfully on thorns did stand,
I have seen roses damask'd, red and white,
But no such roses see I in her cheeks;
```

In conclusion, here is the roadmap to solving common problems. 

![image](https://user-images.githubusercontent.com/65037987/110256744-89ca6080-7f68-11eb-8c3c-41d9e5721e56.png)

If all else fails, try these:
- [ ] Have you restarted the application?
- [ ] Have you rebooted the device?
- [ ] Have you tried uninstalling and reinstalling the app?

If you checked all these boxes and still have not derived a solution, take a break, and then 99% of the time, you'll realize what the answer is. 
