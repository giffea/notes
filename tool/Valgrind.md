‌
valgrind -v --leak-check=full --show-leak-kinds=all --track-origins=yes --log-file=val.log
valgrind --tool=memcheck --gen-suppressions=all --track-origins=yes --vgdb=no --log-file=val.log  # from CLion
valgrind --tool=callgrind --log-file=val.log kcachegrind


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNTE4NjM1MjQsNDg1Nzk4MDQxLDM4Nz
EyNzcxN119
-->