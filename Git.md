### 介绍

一个 Git 项目有以下三个主要部分：

- Git 目录
- 工作目录（或工作树）
- 暂存区

#### Git 目录

位于 项目路径 `/.git/` 中，是 Git 存储准确跟踪项目所需的一切的地方。这包括元数据和包含项目文件压缩版本的对象数据库。

#### 工作目录

用户对项目进行本地更改的地方。工作目录从 Git 目录的对象数据库中提取项目文件并将它们放在用户的本地机器上。

#### 暂存区

是一个文件，用于存储有关下一次提交内容的信息。



> 通过三个部分，文件可以在任何给定时间处于三种主要状态：已修改、已提交或已暂存。

### 命令

#### Git Reset

`git reset` 命令允许你将当前头部重置为指定状态。你可以重置特定文件以及整个分支的状态。

### 常用功能

#### 删除分支

```bash

// 删除本地分支
git branch -d localBranchName

// 删除远程分支
git push origin --delete remoteBranchName

```

#### 同步分支

```bash

// -p 表示精简
git fetch -p

```



#### rebase

#### reset

#### revert







git cat-file

git checkout <commit-id>

