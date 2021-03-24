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
$ man echo
ECHO(1)                                                      
                                                             
NAME                                                         
       echo - display a line of text                         
                                                             
SYNOPSIS                                                     
       echo [SHORT-OPTION]... [STRING]...                    
       echo LONG-OPTION                                      
                                                             
DESCRIPTION                                                  
       Echo the STRING(s) to standard output.                
                                                             
       -n     do not output the trailing newline             
                                                             
       -e     enable interpretation of backslash escapes     
                                                             
       -E     disable interpretation of backslash escapes (de
                                                             
       --help display this help and exit                     
                                                             
       --version                                             
              output version information and exit            
                                                             
       If -e is in effect, the following sequences are recogn
                                                             
       \\     backslash                                      
                                                             
       \a     alert (BEL)                                    
                                                             
       \b     backspace                                      
                                                             
       \c     produce no further output                      
                                                             
       \e     escape                                         
                                                             
       \f     form feed                                      
                                                             
       \n     new line                                       
                                                             
       \r     carriage return                                
                                                             
       \t     horizontal tab                                 
                                                             
       \v     vertical tab                                   
                                                             
       \0NNN  byte with octal value NNN (1 to 3 digits)      
                                                             
 Manual page echo(1) line 1 (press h for help or q to quit)  
```
To recall the previous command, enter the up arrow `↑`. To recall the furthest command, enter the down arrow `↓`.
```bash
$ echo tree
tree
$ echo tree   # using ↑ returns previous command
```

Another way to run the previous command is to enter `!!`. In software development, `!` is pronounced "bang" and `!!` is "bang bang". To enter the last command with certain characteristics, enter `!`<string>. For example, `!curl` recalls the last instance of `curl`.
```bash
$ echo hi
hi
$ !!
hi
$ !echo       # recalls last instance of echo
hi
$ !e          # short form works because the only command with e is echo
hi
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
$ echo before 
$ before 
$ echo after
$ after
$            # using Ctrl-L to clear the terminal window
```
```bash
$ exit       # using Ctrl-D to exit the terminal window
```

To create a file and input a string, enter the redirect operator `>` <file>. If the file does not exist, it will create it. If the file exits, it will overwrite the information in the file. 
```bash
$ echo "strawberry banana smoothie" > yummy.txt
```

To print out the contents of the file, enter the command `cat` <file>.
```bash
$ cat yummy.txt
$ strawberry banana smoothie
```

To add another line to the text file, enter the append operator `>>` in place of the redirect operator `>`. If the file does not exist, it will create it. If the file exists, it will append the string to a new line. 
```bash
$ echo "red bean scores" >> yummy.txt
$ strawberry banana smoothie
$ red bean scores 
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
Downloads
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
$ cat y⇥     # using tab completetion yields yummy.txt because it is the only file or directory that starts with a `y` or `Y`
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
$ head sonnets.txt  
Shake-speare's Sonnets

I

From fairest creatures we desire increase,
That thereby beauty's Rose might never die,
But as the riper should by time decease,
His tender heir might bear his memory:
But thou contracted to thine own bright eyes,
Feed'st thy light's flame with self-substantial fuel,  # line 10
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
$ head -18 sonnets.txt | tails -5  # retrives the last 5 lines of the first sonnet; -18 can also be rewritten as -n 18
And only herald to the gaudy spring,
Within thine own bud buriest thy content,
And tender churl mak'st waste in niggarding:
Pity the world, or else this glutton be,
To eat the world's due, by the grave and thee.
```

In conclusion, here is the roadmap to solving common problems. 

![image](https://user-images.githubusercontent.com/65037987/110256744-89ca6080-7f68-11eb-8c3c-41d9e5721e56.png)

If all else fails, try these:
- [ ] Have you restarted the application?
- [ ] Have you rebooted the device?
- [ ] Have you tried uninstalling and reinstalling the app?

If you checked all these boxes and still have not derived a solution, take a break, and then 99% of the time, you'll realize what the answer is. 
