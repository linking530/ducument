git merge最简洁用法

一、开发分支（dev）上的代码达到上线的标准后，要合并到 master 分支
git checkout dev
git pull
git checkout master
git merge dev
git push -u origin master
二、当master代码改动了，需要更新开发分支（dev）上的代码
git checkout master 
git pull 
git checkout dev
git merge master 
git push -u origin dev