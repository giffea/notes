# C++
cov-build --dir coverity make -j 24
cov-analyze --dir coverity --all --strip-path "/proj/`whoami`/TPPA" -sf /mtkeda/CI/coverity/install_source/license.analysis.8.7.dat
cov-commit-defects --dir coverity --host mtksdaap75.mediatek.inc --user srv_TPPA --stream TPPA_${PROJECT} -sf /mtkeda/CI/coverity/install_source/license.analysis.8.7.dat --password "`cat ${TPPA_HOME}/key`"

# Python
cov-configure --config coverity-config --python
cov-build --config coverity-config --dir coverity --fs-capture-search "/proj/`whoami`/TPPA/${PROJECT}/${PROJECT}" --no-command
cov-analyze --dir coverity --all --strip-path "/proj/`whoami`/TPPA/${PROJECT}" -sf /mtkeda/CI/coverity/install_source/license.analysis.8.7.dat
cov-commit-defects --dir coverity --host mtksdaap75.mediatek.inc --user srv_TPPA --stream TPPA_${PROJECT} -sf /mtkeda/CI/coverity/install_source/license.analysis.8.7.dat --password "`cat ${TPPA_HOME}/key`"
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNTIzOTY0OTksNzMwOTk4MTE2XX0=
-->