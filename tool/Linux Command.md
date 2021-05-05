
| Command | Desciption |
|--|--|
| nm -demangle main.o | show symbol table |
| objdump -CS libxx.so | dump assembly codes |

du -h --max-depth=1
find . -name "PATTERN" -type f -mtime +7 --exec rm -rf {} \; # delete files which older than 7 days
find . -name "*.cpp" -not -path "./gui/*" -o -name "*.h" -not -path "./gui/*" | xargs wc -l # count code lines
gstack ip addr show eth0 # show ip address
libreoffice --calc
netstat -a | grep tcp # when you need to see what's going on with port
rsync -a --delete --no-group --no-owner --no-perms -O SOURCE DESTINATION COMMAND >& | tee LOG

rsync -arvOJ --delete --exclude .git --no-group --no-owner --no-perms * /path/
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNzkwOTQxMzksMTA4MTU2ODkyOSwtND
A3MzEwNjUwLDE2MDUzMzc4MzNdfQ==
-->