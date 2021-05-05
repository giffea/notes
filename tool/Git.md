# git bisect

# git lfs
(https://wiki.mediatek.inc/pages/viewpage.action?pageId=598639040)
git lfs install
git lfs trace *.bin
git lfs pull

# git subrepo
Tutorial: [https://github.com/ingydotnet/git-subrepo  
](https://github.com/ingydotnet/git-subrepo)
[subrepo vs submodule vs subtree](https://github.com/ingydotnet/git-subrepo/blob/master/doc/intro-to-subrepo.swim)

-   Turn an existing subdirectory into a subrepo.  
    git subrepo init <subdir> -r <remote>  
    ex. git subrepo init src/bt -r [https://gerrit.mediatek.inc/TPPA/bt](https://gerrit.mediatek.inc/TPPA/bt)
-   Update the subrepo subdir with the latest upstream changes.  
    git subrepo pull <subdir>
-   Push a properly merged subrepo branch back upstream.  
    git subrepo push <subdir>  
    
-   Add a repository as a subrepo in a subdir of your repository.  
    git subrepo clone <repository> <subdir>  
    

# git submodule

[https://services.github.com/on-demand/downloads/submodule-vs-subtree-cheat-sheet/](https://services.github.com/on-demand/downloads/submodule-vs-subtree-cheat-sheet/)

git submodule add [https://gerrit.inc:/stateBased](https://gerrit.mediatek.inc/TPPA/stateBased) # add a submodule to current repo  
git clone --recursive  [https://gerrit.inc/kernel](https://gerrit.mediatek.inc/TPPA/kernel) # clone whole TPPA/kernel repo  
git submodule update --init # clone submodule if TPPA/kernel is already existed  
git submodule update --remote # pull submodule updates

# git subtree

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
eyJoaXN0b3J5IjpbLTE3Nzc5NjIyMjcsODUxMzgwMTZdfQ==
-->