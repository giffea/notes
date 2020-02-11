# C++
cov-build --dir coverity make -j 24
cov-analyze --dir coverity --all --strip-path "/path/proj" -sf /path/coverity/install_source/license.analysis.8.7.dat
cov-commit-defects --dir coverity --host coverity.com --user giffea --stream ${PROJECT} -sf /path/coverity/install_source/license.analysis.8.7.dat --password "`cat /path/key`"

# Python
cov-configure --config coverity-config --python
cov-build --config coverity-config --dir coverity --fs-capture-search "/path/proj" --no-command
cov-analyze --dir coverity --all --strip-path "/path/proj" -sf /mtkeda/CI/coverity/install_source/license.analysis.8.7.dat
cov-commit-defects --dir coverity --host mtksdaap75.mediatek.inc --user srv_TPPA --stream TPPA_${PROJECT} -sf /mtkeda/CI/coverity/install_source/license.analysis.8.7.dat --password "`cat ${TPPA_HOME}/key`"
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1MDc0NjM5MzAsNzMwOTk4MTE2XX0=
-->