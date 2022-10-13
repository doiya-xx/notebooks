# git

## install

### windows

```shell
git version
# 配置
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
# 生成rsa密钥
ssh-keygen -t rsa -C "904455569@qq.com"
# 将生成的公钥添加到github账号中
# github不信任ssh，需要进行账号授权
```

## command

配置

```shell
git config --global -l # 查看全局配置
git config --global -e # 编辑全局配置
git config --global [<variable>] # 查看全局变量值
git config --global [<variable> <value>] # 设置全局变量值

```

将目录变成让git管理的目录。在目录下生成`.git`目录。

```shell
git init
```

提交修改，添加要放进仓库管理的文件

```shell
git add README.md
```

提交文件到仓库中，并且添加描述。

```shell
# 添加的文件可以多个，然后只需要提交一次
git commit -m "commit description"
```

查看当前仓库状态

```shell
git status
```

查看文件的修改

```shell
git diff <file>
git diff README.md
```

查看提交的版本历史

```shell
git log
git log --pretty=oneline
git log --graph # 使用图显示
git log --graph --pretty=oneline --abbrev-commit
```

版本回滚

`HEAD`表示当前版本，`HEAD^`表示上一个版本，`HEAD^^`表示上上一个版本，`HEAD~100`表示上100个版本。

回滚版本后，之前版本状态之后创建的文件不见了

在当前命令行进程没有结束前，还可以撤销回滚，找到要回滚的版本头。

```shell
git reset --hard <commit_id>
git reset --hard HDEA^
git log
git reset --hard a964
```

查看commit_id

```shell
git reflog
```

让文件回到最近一次`git add`或`git commit`状态

```shell
git checkout -- <file>
```

将提交到`stage`的修改撤销：`unstage`，将文件放回工作区

```shell
git reset HEAD <file>
```

删除文件

```shell
# 删除工作区文件，并且将这次删除放入暂存区。
git rm <file>
# 删除工作区和暂存区文件，并且将这次删除放入暂存区。
git rm -f <file>
# 删除暂存区文件，但保留工作区的文件，并且将这次删除放入暂存区。
git rm --cached <file>
# 恢复
git checkout -- <file>
```

链接远程仓库

在`~/.shh/`目录下，生成rsa非对称密钥进行签名，将生成的公钥添加到github的账号中

```shell
ssh-keygen -t rsa -C "youremail@example.com"
```

```shell
# 链接远程仓库
git remote add origin https://github.com/doiya-xx/rust_source_codes.git
git remote add origin git@github.com:doiya-xx/rust_source_codes.git # 使用SSH
# 推送
git push -u origin master # 第一次推送需要使用 -u
git push origin master
```

```shell
git remote -v # 查看链接的远程库
git remote rm origin # 删除链接远程库
```

分支管理

```shell
# 查看所有分支，以及当前HEAD指向哪个分支
git branch
# 创建新分支
git branch dev 
# 创建新分支并切换到新分支
git checkout -b dev 
==>
git branch dev
git checkout dev # 切换分支
# 删除分支
git branch -d <branch>
git branch -d dev
# 创建新分支并切换到新分支
git switch -c dev
git switch main # 切换到目标分支
```

在当前分支下，合并其他分支

```shell
git merge <branch>
git merge dev
# 禁止使用fast forward，添加描述，将会在当前分支下commit新版本
git merge --no-ff -m "merge with no-ff" dev 
```

