t 常用命令

## 获得版本库

* git init 

* git clone

  ​

## 查看信息

* git help

* Git log

  ​	查看提交日志

* git diff

  ​	比较文件在不同状态中的文件区别

## 版本管理

* Git add

  ​	加入到版本暂存区中

  ​	. 表示当前文件夹都纳入到暂存区

* git commit

  ​       将暂存区的文件提交到git版本库中

* git rm

  ​      git rm 版本库中的文件



## 远程协作

* git pull

  ​	将远程版本库中的文件拉取到本地

* git push

  ​	将本地版本库中的文件推送到远程库

## Git配置

#### git 查看版本

* git —version

#### 首次使用前的配置

对于user.name与user.email来说，有3个地方可以设置

* 1，/etc/gitconfig (几乎不用) 对于操作系统的 git config —system

* 2，~/.gitconfig (很常用) 对于所有的git项目 git config —global

* 3，针对于特定的项目的 .git/config文件中 对于特定的项目 git config —local

  ```
   git config --local user.name 'lihao'
   git config --local user.email 'test@qq.com'
   git config user.name
   git config user.email
   
   //重置
    git config --local user.name 'lisan'
    
    //删除
    git config --local --unset user.name
    
    
  ```

  ​	

## git的提交更新

提交更新，每次准备提交前，先用 git status 看下，是不是都已暂存起来了，然后在运行提交命令。

* Git commit
* git commit -m 'init'
* Git commit —amend -m 'init' 修改最后一次提交的message
* git commit -am 'init'  添加到索引库并提交 不用写add了



## git 删除文件

* 删除文件
* Git rm readme

#### 以上两者区别

Git rm :

* 删除了一个文件
* 将被删除的文件纳入到暂存区（stage,index）

如果恢复文件

 git reset HEAD index.php  由暂存区恢复到工作区

 git checkout — index.php  丢弃工作区删除文件的内容



rm:

​	将文件删除了，这时，被删除的文件并未纳入缓存区当中.

如果恢复文件：

 	git checkout — index.php



## git 重命名

git mv from_file to_file



## Git 查看提交历史

* git log
* -p 展开显示每次提交的内容差异
* -n 仅显示最近的n次更新
* —stat 仅显示简要的增改行数统计
* —pretty==oneline
* —pretty=format:'%h - %an,%ar:%s'
* —graph 图形化的方式查看log

## 忽略文件 .gitignore

* 新建 .gitignore 文件
* *.a   忽略所有 .a结尾的文件
* !lib.a    但 lib.a除外
* /todo   仅仅忽略项目根目录下的todo文件不包括subdir/todo
* Build/  忽略build/目录下的所有文件
* doc/*.txt   会忽略doc/notes.txt 但不包括 doc/server/arch.txt
* **   表示所有的目录



## 分支

#### 列出当前所有分支

* git branch

#### 创建分支

* git branch branch_name

#### 切换分支

* git checkout branch_name

#### 删除分支

* git branch -d branch_name

#### 创建并转向所创建的分支

* git checkout -b branch_name

#### 修改分支的名称

* git branch -m branch_name new_branch_name

#### fast-forward

* 如果可能，合并分支时git 会使用fast-forward 模式
* 在这种模式下，删除分支时会丢掉分支信息。
* 合并时加上 —no-ff 参数会禁用fast-forword, 这样会多出一条commit id
* git merge —no-ff dev

## 合并分支

* Git merge branch_name





## git 回退版本

* 回退到上一个版本

  ```
  git reset -- hard HEAD^  //回退到上一个版本
  git reset -- hard HEAD^^ //回退到上两个版本
  git reset -- hard HEAD~2 //回退到指定第几个版本
  git reset -- hard commit_id //回退到指定的版本
  ```

  ​

* 查看操作日志

  ```
  git reflog 
  ```





## checkout

* Git checkout — test.txt

   作用是：丢弃掉相对于暂存区中最后一次添加的文件内容所做的变更

* Git reset HEAD test.txt

  作用是：将之前添加到暂存区（stage,index）的内容从暂存区移除到工作区。



## 保存工作现场

#### 保存现场

* git stash
* git stash sava 'init'
* git stash list
* git stash —help

#### 恢复现场

* Git stash apply （stash 内容并不删除，需要通过git stash drop stash@{0} 手动删除）
* git stash pop （恢复的同时也将stash 内容删除）
* Git stash apply stash@{0}





## git 标签

* 新建标签，标签有两种：轻量级标签（lightweight）与带有附注标签（annotated）

* 创建一个轻量级标签

  ```
  git tag v1.0.1
  ```

* 创建一个带有附注的标签

  ```
  git tag -a v1.0.2 -m 'release verion'
  ```

  ​

* 删除标签

  ```
  git tag -d tag_name
  ```

* 搜索标签

  ```
  git tag -l 'v*'
  ```

  ​

  ​	

## 查看一个文件都是谁提交的

```
git blame  index.php
```



##  git diff 比较

* git diff ： 比较的是暂存区与工作区文件之间的差别，暂存区表示是原始文件。
* git diff HEAD:  比较的是最新的提交与工作区之间的差别。
* git diff —cached： 比较的是版本库与暂存区之间的差别。


