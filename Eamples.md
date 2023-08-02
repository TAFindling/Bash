#Examples

awk -F: -v a=$test -v b=100 'BEGIN {OFS=" "} {$3=a, $4=b} {print $0}' passwd

