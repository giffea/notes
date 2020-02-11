# C++
cov-build --dir coverity make -j 24
cov-analyze --dir coverity --all --strip-path "/path/proj" -sf /path/coverity/install_source/license.analysis.8.7.dat
cov-commit-defects --dir coverity --host coverity.com --user giffea --stream ${PROJECT} -sf
/path/coverity/install_source/license.analysis.8.7.dat --password "`cat /path/key`"

# Python
cov-configure --config coverity-config --python
cov-build --config coverity-config --dir coverity --fs-capture-search "/path/proj" --no-command
cov-analyze --dir coverity --all --strip-path "/path/proj" -sf /path/coverity/install_source/license.analysis.8.7.dat
cov-commit-defects --dir coverity --host coverity.com --user giffea --stream ${PROJECT} -sf /path/coverity/install_source/license.analysis.8.7.dat --password "`cat /path/key`"
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjc4ODMzNDQ3LDczMDk5ODExNl19
-->