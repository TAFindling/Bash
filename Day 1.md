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


#EXAMPLES
1.
Brace expansion is a mechanism by which arbitrary strings may be generated, for commands that will take multiple arguements. For the below examples, the first example is equivalent to the second command.

$ mkdir /var/log/{auth,syslog,dmesg}_log

Results in

$ mkdir /var/log/auth_log /var/log/syslog_log /var/log/dmesg_log

Activity: Using Brace-Expansion, create the following directories within the $HOME directory:

1123
1134
1145
1156

  mkdir 11{23,34,45,56} 
2.
As we learned, the following example would create five files with one command.

touch file1.txt file2.txt file3.txt passwd.txt shadow.txt

But, with Brace Expansion it can be shortened to the following.

touch file{1..3}.txt passwd.txt shadow.txt

Activity:

Use Brace-Expansion to create the following files within the $HOME/1123 directory. You may need to create the $HOME/1123 directory. Make the following files, but utilze Brace Expansion to make all nine files with one touch command.

Files to create:

1.txt
2.txt
3.txt
4.txt
5.txt
6~.txt
7~.txt
8~.txt
9~.txt
touch 1123/{1..5}.txt 1123/{6..9}~.txt

3.
Using ONLY the find command, find all files on the system with inode 4026532575 and print only the filename to the screen, not the absolute path to the file, separating each filename with a newline. Ensure unneeded output is not visible.

Tip: The above inode is specific to this CTFd question and might not be in use on your Linux Opstation. Instead, you can test your command on your Linux OpStation against inode 999.
find // -inum 4026532575 -printf "%f\n" 2>/dev/null

6.
Activity:

Write a basic bash script that greps ONLY the IP addresses in the text file provided (named StoryHiddenIPs in the current directory); sort them uniquely by number of times they appear.

It is not important to have a regular expression that only catches fully valid IP addresses. It is more important that you become familiar with creating and using regular expressions. Below, there are some useful websites that you can use to visually see what your regular expression pattern is matching on.

www.regexr.com
www.regex101.com
E.g., [1-4]{0,5}

Bracket Expression: [1-4] = 1 or 2 or 3 or 4

Repetitions: {0,5} = above numbers (1,2,3,4) appear from 0 to 5 times, meaning our number can be between 1 and 44444

Interpreted BASH Chars: . | $ ` \ ! must be escaped with \ in a regex. I.E. to match on a backslash, you must use \\ in your pattern.
egrep -E -o "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" StoryHiddenIPs | sort -nr | uniq -c | sort -nr

7.
Activity:

Find all dmesg kernel messages that contain CPU or BIOS (uppercase) in the string, but not usable or reserved (case-insensitive)
Print only the msg itself, omitting the bracketed numerical expressions ie: [1.132775]
Note: For security reasons, the dmesg command is being emulated on the CTFd backend. You can still use it as normal on your Linux OpStation, but to get a similar output, do not use any dmesg switches. The intent of this activity is to take raw dmesg output and combine it with grep and either awk or cut to manipulate the output into a desired end state.

Tip: As you may have noticed, when using grep you can simulate a logical AND by piping the output of one grep command to the next. This will filter down your output to only what contains all your patterns. But, for this activity, you will need to use a logical OR to match on a wide range of strings. If you do not recall how to utilize that option in grep, go research it from the resources available to you.
dmesg | egrep -E "CPU|BIOS" | egrep -iv "usable|reserved" | cut -d] -f2-

8.
Activity:

Write a Bash script using "Command Substitution" to replace all passwords, using openssl, from the file $HOME/PASS/shadow.txt with the MD5 encrypted password: Password1234, with salt: bad4u
Output of this command should go to the screen/standard output.
You are not limited to a particular command, however you must use openssl. Type man openssl passwd for more information.
TIP: While not required, using awk is possibly the most straightforward method of accomplishing this activity. Keep in mind that awk is its own programming language. It can not use Bash variables unless you import them in. Below is a break down of applicable parts of an awk command, with descriptions of each part. See if you can use this example as a jumping off point to accomplish the end state of the activity.

#!/bin/bash 

a=”New name to place in field one” 
awk -F: -v "awk_var=$a" 'BEGIN {OFS=":"} {$1=awk_var} {print $1,$NF}' /etc/passwd

# '-F' is used to change the default field seperator of " ".  In this example, it	\
# now designates ':'

# '-v' designates or imports a variable into AWK.  In the above example, 'awk_var' is 	\
# declared with the Bash variable of '$a'.

# The 'BEGIN' pattern(s) tells AWK to execute action parts of the pattern before any of	\
# the input is read.  In this case, the 'OFS', or 'Output Field Seperator' will place	\
# colons between the firelds being printed in the output.  As well, it will replace the	\
# first field (i.e. '$1') with whatever data is contained in the AWK variable declared	\
# previously.

# The '{print}' statement designates whatever the desired fields are to print.  '$0' is	\
# the variable for the entire line.  The first field is '$1', the second field is '$2',	\
# and so on.  AWK has a builtin variable, '$NF' which evaluates to the number of fields	\
# on a line.  Use this as a shortcut if you need to print the last field on the line.

#!/bin/bash

a=$(openssl passwd -1 -salt bad4u Password1234)
awk -F: -v "awk_var=$a" 'BEGIN {OFS=":"} {$2=awk_var} {print $0}' $HOME/PASS/shadow.txt

9.
Using ONLY sed, write all lines from $HOME/passwd into $HOME/PASS/passwd.txt that do not end with either /bin/sh or /bin/false.
sed '\/bin\/sh/d;\/bin\/false/d' $HOME/passwd > $HOME/PASS/passwd.txt

10.
Activity:

Using find, find all files under the $HOME directory with a .bin extension ONLY.
Once the file(s) and their path(s) have been found, remove the file name from the absolute path output.
Ensure there is no trailing / at the end of the directory path when outputting to standard output.
You may need to sort the output depending on the command(s) you use. Have each path displayed only once.
Tip: For stripping the filename out of the output, there are different ways that this can be accomplished based on what you have learned so far.

Utilizing -printf options on find.
Utilizing awk to manipulate the fields. This may leave the trailing / if you don't take that into account.
Utilizing the rev and cut commands creatively.
find -name "*.bin" -printf "%h\n" | sort -u

11.
Activity:

Write a script that will do the following.

Write a script which will copy the last entry/line in the passwd-like file specified by the $1 positional parameter
Modify the copied line to change:
User name to the value specified by $2 positional parameter
Used id and group id to the value specified by $3 positional parameter
Home directory to a directory matching the user name specified by $2 positional parameter under the /home directory (i.e. if the $2 was 'Chris', the new line would have /home/Chris as its home directory)
The default shell to `/bin/bash'
Append the modified line to the end of the file
Example INPUT file's last line.

games:x:5:60::/usr/games:/usr/sbin/nologin
If positional parameter 2 was passed "devildog" and positional paramter 3 was passed "9001", after modifications the appended line would look like this.

devildog:x:9001:9001::/home/devildog:/bin/bash
Tip: awk provides the simplest method for completing this activity. Refer back to your notes on "09 - BASH Activity" if you are in need of starting point on this activity.

Note: The contents of the passwd-like file will be randomly generated on each submission. It is intended to read the last line once and store it in a variable.

To read more on Positional Parameters, go to the following resource:

https://www.gnu.org/software/bash/manual/bash.html#Positional-Parameters
To read more on the Passwd file format, go to the following resource:

man passwd.5
tail -1 $1 | awk -F: -v "name=$2" -v "guid=$3" -v "directory=/home/$2" 'BEGIN {OFS=":"} {$1=name;$3=guid;$4=guid;$6=directory;$7="/bin/bash"} {print $0}' >> $1

13.
Activity:

Find all executable files under the following four directories:
/bin
/sbin
/usr/bin
/usr/sbin
Sort the filenames with absolute path, and get the md5sum of the 10th file from the top of the list.
Tip: In the below example, you can see the different uses of md5sum. While not wrong, the first command is hashing the string output of the the find command. In the second, md5sum is hashing the file contents of the given file, which is what is intended for this activity. You can also tell the second method hashed the file as the file name is listed in the hash output; the first only lists a hyphen indicating a string was hashed. For this activity, to provide md5sum with the 10th file of the sorted output, it is recommended to use Command Subtitution.

[chris@localhost ~]$ find /etc -maxdepth 1 -name passwd | md5sum
9231fb35b4431d59eae53a8c0d673231  -
[chris@localhost ~]$ md5sum /etc/passwd
62f5fa5100adcee3305cf979b5734a3e  /etc/passwd
#!/bin/bash

hasher() {
a=$(find /bin /sbin /usr/bin /usr/sbin -executable -type f | sed '/\/bin\/sbin\/usr\/bin\/usr\/sbin/d' | sort -d | head -n 10 | tail -1)
md5sum $a | cut -d ' ' -f1
}

hasher


14.
Activity:

Using any BASH command complete the following:

Sort the /etc/passwd file numerically by the GID field.
For the 10th entry in the sorted passwd file, get an md5 hash of that entry’s home directory.
Output ONLY the MD5 hash of the directory's name to standard output.
Note: Since we are dealing with a directory, which is both a string and an absolute path, it matters how we get the md5sum of our intended output.

[chris@localhost ~]$ md5sum /home/chris
md5sum: /home/chris: Is a directory
In the above example, an error is returned because we are applying the directory /home/chris as the first argument of the above command. Since /home/chris is a directory, likely with additional files within it, we cannot assign this as an argument. However, we have the string /home/chris as STDIN for a command, as seen in the below example.

[chris@localhost ~]$ echo "/home/chris" | md5sum
fd1a05901ce7150f82abd7f7d76f2827  -
sort -t: -k4 -n /etc/passwd | head -n 10 | tail -1 | cut -d: -f6 | md5sum | cut -d ' ' -f1


15.
Activity:

Write a script which will find and hash the contents 3 levels deep from each of these directories: /bin /etc /var
Your script should:
Exclude file type named pipes. These can break your script.
Redirect STDOUT and STDERR to separate files.
Determine the count of files hashed in the file with hashes.
Determine the count of unsuccessfully hashed directories.
Have both counts output to the screen with an appropriate title for each count.
Example Output:

Successfully Hashed Files: 105
Unsuccessfully Hashed Directories: 23
#!/bin/bash


finder(){
find /bin /etc /var -maxdepth 3 ! -type p -exec md5sum {} \; 2>>error 1>>out
s=$(cat out | wc -l)
e=$(grep -c directory error)
echo "Successfully Hashed Files: $s"
echo "Unsuccessfully Hashed Directories: $e"
}

finder

16.
Activity:

Design a script that detects the existence of directory: $HOME/.ssh

Upon successful detection, copies any and all files from within the directory $HOME/.ssh to directory $HOME/SSH and produce no output. You will need to create $HOME/SSH.
Upon un-successful detection, displays the error message "Run ssh-keygen" to the user.
NOTE: If the $HOME/.ssh directory does not exist, one may run the ssh-keygen command. Accept all defaults for the purposes of this exercise. This is not necessary for passing the activity but can be used for testing on your local machine.

#!/bin/bash

copier(){
mkdir $HOME/SSH
if [ -d "/$HOME/.ssh" ]
then
cp -r $HOME/.ssh/* $HOME/SSH 2>/dev/null
else
echo "Run ssh-keygen"
fi


}

copier

17.
Activity:

Write a script that determines your default gateway ip address. Assign that address to a variable using command substitution.
NOTE: Networking on the CTFd is limited for security reasons. ip route and route are emulated. Use either of those with no arguments/switches.
Have your script determine the absolute path of the ping application. Assign the absolute path to a variable using command substitution. HINT: man which
Have your script send six ping packets to your default gateway, utilizing the path discovered in the previous step, and assign the response to a variable using command substitution.
Evaluate the response as being either successful or failure, and print an appropriate message to the screen.
Pseudo Example:

A=$(command_1)
B=$(command_2)
C=$($A command_3 $B)
if [[ "$" <condition> "$" ]]; then
   echo "successful";Activity:

Write a bash script that will find all the files in the /etc directory, and obtains the octal permission of those files. The stat command will be useful for this task.
Depending how you go about your script, you may find writing to the local directory useful. What you must seperate out from the initial results are the octal permissions of 0-640 and those equal to and greater than 642, ie 0-640 goes to low.txt, while 642 is sent to high.txt.
Have your script uniquely sort the contents of the two files by count, numerically-reversed, and output the results, with applicable titles, to the screen. An example of the desired output is shown below.
NOTE: There is a blank line being printed between the two sections of the output below.
EXAMPLE OUTPUT:

Files w/ OCTAL Perm Values 642+:
    424 777
    365 644
     15 755
  
Files w/ OCTAL Perm Values 0-640:
      4 640
      3 440
      2 600
      1 444
#!/bin/bash

find /etc -type f -exec stat -c '%a' {} \; > ~/test.del 2>/dev/null


for x in $(cat ~/test.del); do
    if [[ $x -le 640 ]]; then
        echo "$x" >> ~/less.del
    elif [[ $x -ge 642 ]]; then
        echo "$x" >> ~/more.del
    fi
done

echo "Files w/ OCTAL Perm Values 642+:"
sort ~/more.del | uniq -c | sort -nr
echo 
echo "Files w/ OCTAL Perm Values 0-640:"
sort ~/less.del | uniq -c | sort -nr

rm ~/*.del

else
   echo "failure";
fi 
#!/bin/bash

gateway(){
A=$(which ping)
B=$(route | grep 'UG[ \t]' | awk '{print $2}')
$A -c 6 $B > pingresult.txt
C=$(cat pingresult.txt | grep received | cut -d ' ' -f4)
if [[ $C == 6 ]]; then
    echo "successful";
else
    echo "failure";
fi
}

gateway

18.
ctivity:

Create the following files in a new directory you create $HOME/ZIP:
file1 will contain the md5sum of the text 12345
file2 will contain the md5sum of the text 6789
file3 will contain the md5sum of the text abcdef
Create a zip file containing the three files above, without being stored inside a directory in the zip file. Name the zip file $HOME/ZIP/file.zip
HINT: "Junk" the paths
Utilize tar on $HOME/ZIP/file.zip to archive it into a file called $HOME/ZIP/file.tar.gz which should not include directories. Use the gzip option in tar, DO NOT use a seperate gzip binary.
HINT: You might need an option to change directories first.
mkdir $HOME/ZIP
cd $HOME/ZIP
md5sum <<<"12345" | cut -d ' ' -f1 > file1
md5sum <<<"6789" | cut -d ' ' -f1 > file2
md5sum <<<"abcdef" | cut -d ' ' -f1 > file3
zip file.zip file1 file2 file3
tar -czvf file.tar.gz file.zip

19.
Activity:

Utilize Bash looping to iteratively create each user account and their directories.

Design a basic FOR Loop that iteratively alters the file system and user entries in a passwd-like file for new users: LARRY, CURLY, and MOE.
Each user should have an entry in the $HOME/passwd file
The userid and groupid will be the same and can be found as the sole contents of a file with the user's name in the $HOME directory (i.e. $HOME/LARRY.txt might contain 123)
The home directory will be a directory with the user's name located under the $HOME directory (i.e. $HOME/LARRY)
NOTE: Do NOT use shell expansion when specifying this in the $HOME/passwd file.
The default shell will be /bin/bash
The other fields in the new entries should match root's entry
Users should be created in the order specified
baseline=$(head -1 $HOME/passwd)
for x in {LARRY,CURLY,MOE}; do
    echo $baseline | awk -F: -v un=$x -v ui=$(cat $HOME/$x.txt) '{OFS=":"} {$1=un;$3=$4=ui;$6="$HOME/"un} {print $0}' >> $HOME/passwd
mkdir $HOME/$x
done

20
Activity:

Write a bash script that will find all the files in the /etc directory, and obtains the octal permission of those files. The stat command will be useful for this task.
Depending how you go about your script, you may find writing to the local directory useful. What you must seperate out from the initial results are the octal permissions of 0-640 and those equal to and greater than 642, ie 0-640 goes to low.txt, while 642 is sent to high.txt.
Have your script uniquely sort the contents of the two files by count, numerically-reversed, and output the results, with applicable titles, to the screen. An example of the desired output is shown below.
NOTE: There is a blank line being printed between the two sections of the output below.
EXAMPLE OUTPUT:

Files w/ OCTAL Perm Values 642+:
    424 777
    365 644
     15 755
  
Files w/ OCTAL Perm Values 0-640:
      4 640
      3 440
      2 600
      1 444
#!/bin/bash

find /etc -type f -exec stat -c '%a' {} \; > ~/test.del 2>/dev/null


for x in $(cat ~/test.del); do
    if [[ $x -le 640 ]]; then
        echo "$x" >> ~/less.del
    elif [[ $x -ge 642 ]]; then
        echo "$x" >> ~/more.del
    fi
done

echo "Files w/ OCTAL Perm Values 642+:"
sort ~/more.del | uniq -c | sort -nr
echo 
echo "Files w/ OCTAL Perm Values 0-640:"
sort ~/less.del | uniq -c | sort -nr

rm ~/*.del
