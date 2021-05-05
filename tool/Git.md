git bisect find error commit

# git subrepo 
Tutorial: [https://github.com/ingydotnet/git-subrepo](https://github.com/ingydotnet/git-subrepo)

# subrepo vs submodule vs subtree
 [https://github.com/ingydotnet/git-subrepo/blob/master/doc/intro-to-subrepo.swim](https://github.com/ingydotnet/git-subrepo/blob/master/doc/intro-to-subrepo.swim) Turn an existing subdirectory into a subrepo. git subrepo init -r ex. git subrepo init src/bt -r [http://gerrit.inc:8080/TPPA/bt](http://gerrit.inc:8080/TPPA/bt) Update the subrepo subdir with the latest upstream changes. git subrepo pull Push a properly merged subrepo branch back upstream. git subrepo push Add a repository as a subrepo in a subdir of your repository. git subrepo clone git submodule [https://services.github.com/on-demand/downloads/submodule-vs-subtree-cheat-sheet/](https://services.github.com/on-demand/downloads/submodule-vs-subtree-cheat-sheet/) git submodule add [http://gerrit.inc:8080/TPPA/stateBased](http://gerrit.inc:8080/TPPA/stateBased) # add a submodule to current repo git clone --recursive [http://gerrit.inc:8080/TPPA/kernel](http://gerrit.inc:8080/TPPA/kernel) # clone whole TPPA/kernel repo git submodule update --init # clone submodule if TPPA/kernel is already existed git submodule update --remote # pull submodule updates

## git subtree

- split subtree from original repo 
git subtree split -P src/bt -b bt ## 會產生一個branch, 只包含bt/的相關commit 
git checkout bt > mkdir tmp; cd tmp #這個資料夾之後可刪除 
git init 
git pull ../ bt 
git remote add origin http://gerrit.xxx.inc:8080/bt
git push origin master
    
-   import subtree repo to a repo 
git rm -r src/bt ## 先移除既有的bt/* 
git commit > git remote add origin-bt http://gerrit.xxx.inc:8080/bt 
git subtree add -P src/bt origin-bt master ## 加上--squash 會將所有subtree commit合成一個commit
    
 ```
[remote "origin-bt"]
url = http://gerrit.www.inc:8080/bt
fetch = +refs/heads/*:refs/remotes/origin-bt/*
```
‌
-   commit to subtree master 
git subtree push -P src/bt origin-bt master
-   fetch codes of subtree 
git fetch origin-bt   
-   fetch codes of subtree and merge to current brancg 
git subtree pull -P src/bt origin-bt master


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc5MzYzMDY3Nyw4NTEzODAxNl19
-->