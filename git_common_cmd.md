##  git 使用说明
### 一、创建仓库
+ 创建远程主仓库（一般命名upstream），可以创建分支（release，master，dev...）
+ fork主仓库到自己远程仓库（默认命名origin）
+ clone自己远程仓库（origin）到本地  
  ``` git clone git@github.com:XXXX.git ```
+ 绑定远程upstream  
  ```git remote add upstream xxx.git(主仓库地址)```
> 到这里，主仓库与个人仓库就绑定完毕了  
> 通过如下命令查看是否绑定正确  （origin：自己远程仓库，upstream：远程主仓库）  
  ```git remote -v```
### 二、本地操作流程
+ 代码clone到本地之后，就可以正常修改了
  > tips 1:此时修改的应该是个人远程仓库的dev分支  
  > tips 2:永远保持自己的dev分支不和其他dev交叉  
  > tips 3:推送到远程主仓库master的代码都只pull request提交（本地代码先dev合并到本地master，再push到个人远程仓库，在个人远程仓库提交pull request请求合并到主仓库）
+ git的代码修改与svn不一样，git常用操作：
  1. 【修改（工作区）】本地修改代码
  2. 【添加到缓冲区】```git add filepaths ``` 可以通过点号（.）代表所有文件。
  3. 【提交（本地仓库）】``` git commit -m 'msg' ```  
  4. 【拉取（从主仓库）】 ```git pull upstream master ```  upstream是主仓库名字，master是拉取的主仓库的分支名字
  5. 【推送（个人远程）】``` git push origin master```  origin是远程名字，master是推送的分支名字
  6. 【合并代码】 ```git merge branch1 ```  branch1是分支名，命令意思是将branch1分支合并到当前分支
  7. 【仓库状态】 ```git status```  查看修改状态及分支信息
  8.  【创建分支】```git branch dev1``` dev1创建的分支名
  9.  【切换分支】```git checkout dev1``` 切换到dev1分支
  10. 【创建并切换分支】 ```git checkout -b dev2``` 创建并切换到dev2分支
  11. 【撤销修改】```git checkout file``` 将file撤销到最后一次add或者commit的状态
  12. 【版本记录】```git log/reflog ```





