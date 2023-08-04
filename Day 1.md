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
alias -view all aliases
sort                                                           -sort content according to ascii table position
  -n                                                           -numerically
  -u                                                           -uniquely
  -nr                                                          -reverse numerically
  -t'+'                                                        -specify field separator '+'
uniq                                                           -report/omit repeat lines/values
  -c                                                           -select content (has to be sorted) and return number of instances it appears
  -u                                                           -shows only unique lines (no repeats)
  -d                                                           -shows only lines with duplicates
awk                                                            -pattern scanning/language processing
    awk [options] 'selection _criteria {action}' input-file > output-file
  -F: '{print $1}'                                             -displays first fireld based on delimiter
sed                                                            -stream editor, filters/changes text
  - 's/abc/123/'                                               -replaces 1st occurrence of abc in every line with 123
  - 's/abc/123/g'                                              -replaces every occurrence of abc in every line with 123
  - '/sus/d'                                                   -delete the sus lines. Output everything else
  - '-i '<expression>' file.txt                                -"sed inplace" makes changes permanent in file.txt
  -  '/G'                                                      -adds a newline character



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

#Conditionals
  -e                                                                      -file exists? (T/F)
  -f                                                                      -file exists and is a regular file
  -d                                                                      -file exists and is a directory
  ==                                                                      -strings, is equal to strings
  -eq                                                                     -numbers, is equal to
  -!=                                                                     -strings, is NOT equal to

#IF STATEMENTS
  if [[condition]]; then commands
  elif [[condition]]; then commands
  else commands
  fi
    if comparing letters use symbols                                            -'== or !='
    else use letters                                                            -'-eq or -ne'

#Command Substitution
  -used to substitute the output of a command to a variable or another command
    -VAR=$(command)                                                              -substitutes output of command as value of VAR
    -command $(command)
    -VAR=`command'
  -""                                                                             -expands variable (run command, substitute value, etc.)
  -''                                                                             -prints literal


#Parameters
  Store values and can be:
    name (variable)
    number (positional)
    special char (special parameter)
      $#                                                                          -Number of args passed to script
      $0                                                                          -Script Name
      $i                                                                          -Represents the ith arg passed to shell script
      $*                                                                          -Represents all args passed to the shell separated by spaces
      $!                                                                          -PID of last background process
      $?                                                                          -Exit status of last executed command
      $_                                                                          -Last arg to last executed command
      $$                                                                          -PID of current shell
      $@                                                                          -All args of script treated as an array
      $-                                                                          -Current flags set in your script


#Functions
  Series of commands executed as if a single command
  Declare the function, then call it
    Ways to format a function block:"
        function MyFunction {
           echo "this is MyFunction"
        }
         myfunct() {
           echo "myfunct"
       }
       function AFunc() {
         echo "Another Function"
      }
  Call the function with  
    Example:
      folder() {
        if [ ! -s $1 ];  then
          mkdir $1
        else
          echo "whoa stop!
          return 1
        fi
        }
        folder $1
      Run with ./folder "filename"


Example:
function getuserchoice() {
echo "Make a choice [1,2,3]:"
read userchoice
case $userchoice in
(1) echo one ;;
(2) echo two ;;
(3) echo three ;;
(*) echo other ;;
esac
}
getuserchoice


#Variable Substitution
  Example:
    A=$1
    echo The story of Robert the $A
    echo The $A was at the "$A" store so we could buy $A clothes!

  sub1() {
    #Simple Variable Substitution
    name="john"
    echo $name
  }
  sub2() {
    #Variable sub in quotes
    name="John"
    echo "My name is $name"
  }
  sub3() {
    #Variable sub in single quotes
    name="John"
    echo 'My name is $name'
  }
  sub4() {
    #Using curly brackets with variable sub
    name="Hohoh"
    echo "My name is $nameho"
    echo "My name is ${name}ho"
  }
  sub5() {
    #Extra curly brackets
    name="Johnny!"
    echo ${name:2:4}
  }


#Bash Loops
  ##For Loop
    for item in [list]                                    -List can be strings separated by spaces, range of numbers, output of command, array, etc.
    do
    [commands]
    done
    
  ##Break/Continue
    if [[condition]];then
    break                                                 -Terminates loop after a condition is met
    fi
    if [[condition]];then
    continue                                              -Continues with next iteration of loop
    fi

  ##While/Until Loop
    counter=1
    while [[ $counter -le 10 ]]
    do
      echo $counter
      ((counter++))
    done
    echo "All done!"

  counter=1
  until [[ $counter -gt 10 ]]
  do
    echo $counter
    ((counter++))
  done
  echo "All done!"


#EXAMPLES
  ##Loops
    T1(){
    for x in {a,b,1,2}
    do
      echo $x
    done
    }
    T2(){
    x=0
    while [[ $x -le 10 ]]; do echo $x; x = $(($x+1))
    if [[ $x -eq 8 ]]; then break; fi; done
    }
    T3(){
    echo "From T3 count"
    for ((x=0;x<=5;x++))
    do
    if [[$x == 4]];then 
      continue
    fi
      echo "\$x is equal to $x"
      done
      }
    T1
    T2
    T3
