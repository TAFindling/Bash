#Examples

awk -F: -v a=$test -v b=100 'BEGIN {OFS=" "} {$3=a, $4=b} {print $0}' passwd                  -

cat passwd                                                                                    -prints passwd to the screen
egrep student passwd                                                                          -pulls the student line out of passwd
egrep student passwd | sed 's/student/student1/'                                              -changes student username to student1 in passwd
egrep student passwd | sed 's/student/student1/g' >> passwd                                   -changes student in passwd and changes student home directory to student1
egrep student passwd | sed 's#/home/student#/home/notstudent#'
egrep student passwd | sed 's/\/home\/notstudent/\/home\/student#/'
