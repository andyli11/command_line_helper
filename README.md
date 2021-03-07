## A Resource Sheet for Understanding the _Command Line Interface_ (CLI).

This guide utilizes the _Unix_ command line: a family of operating systems including _Andriod, Linux, iOS, and macOS._ 

![image](https://user-images.githubusercontent.com/65037987/110254989-94342c80-7f5f-11eb-96cb-4f3704351d4c.png)

The `echo` command takes a string argument and displays it in the _standard output_; in this case, the terminal window. 
```bash
$ echo hi
hi 
```

To leave the current line and go to a new line, hit `Ctrl-C or Command-C`. This is especially useful to get out of tough situations. A useful mneumonic is to think of 'C' as a cancel button to stop the current command. 
```bash
$ ech oops I made a typo Ctrl-C
$ 
```

The `man` command takes a command name argument and displays data about the command argument. "Man" is short for manuel. You can also run `$ man man` because man itself is a command. 
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
The up arrow `↑` gives access to the previous command entered, and the down arrow `↓` goes the other way to return the furthest command entered. 
```bash
$ echo tree
tree
$ echo tree //=> ↑ echo tree: returns previous command
```

In conclusion, here is the roadmap to solving common problems. 

![image](https://user-images.githubusercontent.com/65037987/110256744-89ca6080-7f68-11eb-8c3c-41d9e5721e56.png)

If all else fails, try these:
* [ ] Have you restarted the application?
* [ ] Have you rebooted the device?
* [ ] Have you tried uninstalling and reinstalling the app?

If you checked all these boxes and still have not derived a solution, take a break, and then 99% of the time, you'll realize what the answer is. 
