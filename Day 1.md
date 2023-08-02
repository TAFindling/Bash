CTFd site: http://10.50.43.161

#Commands
!!                                                             -run the last command
!#                                                             -run the command indicated by the number
ctrl + a                                                       -jump to beginning of line
ctrl + e                                                       -jump to end of line
ctrl + u                                                       -clear everything to the left of the cursor
ctrl + l/r arrow                                               -jumps to next word on line
ctrl + l                                                       -clears screen
'#'                                                            -used to note comments
ctrl + r                                                       -used to search through history for commands
man                                                            -opens help pages
  G/g                                                          -jumps to end of current man page
  //?/&/n/q                                                    -used to search forward/backward for line//jumps to next pattern match/quit man
  []                                                           -denotes optional triggers
curl "website"                                                 -used to view web pages within a command shell
 ">"                                                             -used to redirect output of a command ( curl cht.sh/grep > file.txt)
alias                                                          -used to associated words/letters with a given command
function                                                       -used to associate an entry with a given function
type -a                                                        -used to find out what a command is (function/alias/etc)
cd/home/~/$HOME                                                -used to navigate to the current user's home directory
touch -t                                                       -used to change file timestamps/create files if they do not already exist
cat                                                            -used to concatenate files (combine)
more                                                           -displays content of a file one page(screen) at a time starting from the top of the file
less                                                           -displays content of a file starting from bottom of the file
head/tail                                                      -shows first/last 10 lines of a file (trail with number to show specified number of lines)
locate                                                         -looks through multiple directories (assuming file in cache) and displays locations of files
whereis                                                        -used to find executable files and returns installation location
which                                                          -used to see if something is present on machine (commands for example)
find                                                           -used to search for files
  -name                                                        -specifies the specific file that is being looked for
  -iname                                                       -denotes a search with case insensitivity
  /"directory"                                                 -begins search in the specified directory
  -type                                                        -specifies file type to be searched for
  ! -type                                                      -finds everything except for the specified file type
  -maxdepth                                                    -specifies how many layers from root to search
  2> /dev/null                                                 -used to redirect STDERR to /dev/null
grep                                                           -searches for lines/files that match a specified file
  -Example:  ls -lisa | grep root                              -used to run an ls and only return files that contain root
  -Example:  grep day ./poems.txt                              -searches for any lines that contain the word 'day' within poems.txt
  -v                                                           -used to invert the search (not/!)
  -n                                                           -displays the line number of the line containing the search result
  -c                                                           -displays the number of times a specified search shows up within a file without displaying the containing lines
  grep -e/egrep                                                -allows for the use of Regex with grep
    -Example: egrep ":[0-9]{3}" passwd                         -searches for any number appearing 3 times in a row
    -Example: egrep 'root' passwd                              -searches for root in passwd and returns the line it appears on
  -o                                                           -displays just the found search expression and none of the rest of the line
    -Example: egrep "student|root" ./passwd                    -finds/prints any lines that contain either student or root within the passwd file
    -Example: egrep -A/B/C# "student|root" ./passwd            -same as above, but prints # of lines above/below/both the found pattern
cut                                                            -used to remove data from files based on specified arguments
    -Example: tail -1 passwd | cut -d: -f3                     -cuts field 3 from the passwd file starting/ending at the colons surrounding it
  --output-delimiter+''                                        -changes the delimiter used when printing to the screen
  

  
#Order of Operations
  1. Redirection
  2. Alias
  3. Parameter Expansion/Commands/Arithmetic/Quote Removal
  4. Shell Function
  5. Built-In Commands
  6. Hash Tables
  7. Path Variable
  8. Error Handling (command not found)

#Brace Expansion
  -used to more efficiently run multiple commands at a time
  -ex: mkdir test{1..5}  -runs iterations of mkdir up to 5 creating the files test1, test2, etc.

#Recommendations
  - .bashrc                                                       -file allowing for the changing of native setup for logged in user
  -

