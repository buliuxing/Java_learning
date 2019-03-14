# 第3节：Git



##Git常用命令

- ### git clone 远程代码仓库

  ```
  git init 创建本地代码仓库，创建一个.git文件夹
  git clone https://github.com/buliuxing/Java_learning.git 下载远程代码
  git clone -b branch_name  <server> 拉取分支代码到本地
  git fetch origin branch_name 拉取分支代码到本地（前提需要：建立本地仓库和远程仓库的关联） 
  git checkout -b branch_name origin/branch_nam 在本地创建分支并切换到该分支
  git pull origin branch_name 把某个分支上的内容都拉取到本地
  ```

* ### git add 提交文件到暂存区

  ```
  git add . 递归添加当前工作目录的所有文件
  ```

* ### git commit 提交已经被add的文件

  ```
  git commit -m "first commit" 提交并添加说明
  ```

* ### git remote add origin 将本地仓库与远程仓库关联起来

  ```
  git remote add origin <server>
  git remote remove origin 取消本地目录下关联的远程库
  ```

* ### git push origin master 将改动代码提交到远程仓库

  ```
  git push origin master
  ```

+ ###git checkout -b branch_name 创建分支并切换过去

  ```
  git checkout -b branch_name 
  git push origin <branch>
  ```

+ ### git pull 更新本地仓库至最新改动

  ```
  git pull
  ```

+ ### git merge 合并其他分支到你当前分支

  ```
  git merge <branch>
  ```

+ ### git diff 预览不同版本的差异

  ```
  git diff <source_branch> <target_branch>
  ```



### 参考：[Git简明指南](http://www.runoob.com/manual/git-guide/)

