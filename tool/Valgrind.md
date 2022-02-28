‌
valgrind -v --leak-check=full --show-leak-kinds=all --track-origins=yes --log-file=val.log
valgrind --tool=callgrind --log-file=val.log kcachegrind


<!--stackedit_data:
eyJoaXN0b3J5IjpbNDg1Nzk4MDQxLDM4NzEyNzcxN119
-->