
## Git简易流程 
 简单的一个流程操作过程示意图解

![git简易流程示意图](https://raw.githubusercontent.com/wang-shuai/staticResource/master/git_flow.png)

### 代码流转（红线部分）
1. 将代码从远程公共主仓库fork到私人远程库 
2. 从私人远程库clone代码到本地

  在本地对应文件夹内打开git客户端，通过命令

 `git clone <origin_addr` 

 `git remote -v`

  可以查看本地代码关联的远端库（此时为私人库origin）

3. 在本地git客户端内添加upstream远端库 
 `git remote add upstream <upstream_addr `

 此时通过上一步的 `git remote -v` 可查看到，本地库关联了两个远端库 
 - *upstream库是公共的代码库，别人的代码完成测试之后会合并到这里，所以本地代码需要同步upstream的代码* 
 >`git pull upstream master`
  - ***origin库是个人远端库。本地代码开发完毕，需要合并到公共主仓库，需要先推送到个人远端库*** 
 >`git push origin master`
 
 *然后从个人远端库发起一个merge request，请求合并到公共主仓库，待权限人审核代码即可合并* 

 ***tips: 要时常进行 upstream到本地的同步，可以避免很多冲突的问题***

### 一个示例(蓝色部分)
1. 从远端公共主仓库pull代码到本地master

 `git pull upstream master`

2. 新建分支（如果已有分支，则merge） 

 `git branch <newbranch `

 `git checkout <newbranch`

 或者

 `git checkout -b <newbranch`

 ##### 到这里，就可以在分支 newbranch进行开发了 

 *期间可以每天从主仓库pull代码到本地master，再合并到当前分支*  

 *开发完毕之后，需要发布测试，此时需要合并测试环境的代码* 

3. 将测试主仓库代码pull到本地dev
4. 当前分支 newbranch合并到dev，并解决冲突 

 ***一定要保证本地 newbranch代码的干净，不能掺杂其他人正在开发的代码，方便上线***

5. 合并后的dev包括别人正在测试的代码，也包括自己刚开发的代码，推送到个人远端主仓库，准备提交到测试库
6. 发起merge request，将dev的代码合并到测试主仓库
7. 测试同学从dev通过Jenkins发布到测试环境。

 *此阶段为测试阶段，需要修改bug，重复1-7操作，直到测试通过*

8. 从 newbranch分支发布上线包

 **要做到合并完远程公共主仓库的代码。发版之前，确认再做一次同步**

9. 上线完毕，合并newbranch代码到远程公共主仓库。

 先合并当前分支到本地master分支

 *此时本地master代码相当于远端 **upstream/master**和 newbranch的合并，也就是最新的代码了*

10. push本地master到origin/master
11. 发起merge request，将**origin/master**的代码合并到远程公共主仓库**upstream/master**









