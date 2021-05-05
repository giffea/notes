## git subtree

- split subtree from original repo 
 \> git subtree split -P src/bt -b bt ## 會產生一個branch, 只包含bt/的相關commit 
 \> git checkout bt > mkdir tmp; cd tmp #這個資料夾之後可刪除 
 \> git init 
 \> git pull ../ bt 
 \> git remote add origin http://gerrit.xxx.inc:8080/bt > git push origin master
    
-   import subtree repo to a repo 
\> git rm -r src/bt ## 先移除既有的bt/* 
\> git commit > git remote add origin-bt http://gerrit.xxx.inc:8080/bt 
\> git subtree add -P src/bt origin-bt master ## 加上--squash 會將所有subtree commit合成一個commit
    
 ```
[remote "origin-bt"]

url = http://gerrit.www.inc:8080/bt

fetch = +refs/heads/*:refs/remotes/origin-bt/*
```
‌

-   commit to subtree master > git subtree push -P src/bt origin-bt master
    
-   fetch codes of subtree > git fetch origin-bt
    
-   fetch codes of subtree and merge to current brancg > git subtree pull -P src/bt origin-bt master


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbODUxMzgwMTZdfQ==
-->