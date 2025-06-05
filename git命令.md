### Git的常用命令

***

|                             命令                             |                             意思                             | 备注                                                         |
| :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------- |
|                        git --version                         |                        查看Git版本号                         |                                                              |
| 尽量先folk，不然后期修改很烦<br />git --clone url(ps:github文件地址) |                             克隆                             |                                                              |
| cd "\\目录\\"（Ps:第一步进入克隆所在文件夹命令） <br/>git status |                         查看文件状态                         |                                                              |
|     git add <文件名>（Ps:想要放到暂存区的文件名.格式 ）      |                把变动的文件放到git远端暂存区                 |                                                              |
|                git commit -m"commit message"                 |               提交文件<br />编写commit message               | 先在IDE里进行代码修改保存，<br />然后git status查看状态<br />提交git commit -m"commit message"文件 |
|         git commit -am"update 文件1.格式 文件2.格式"         |             更新修改过的全部文件。不能提交新文件             |                                                              |
|                           git push                           |                           push文件                           |                                                              |
| git restore --staged <文件名>（Ps:想要取出暂存区的文件名.格式 ) |                       把文件取出暂存区                       |                                                              |
|                      git pull --rebase                       |                         拉取远端信息                         |                                                              |
|                 git config pull.rebase true                  |          修改默认的git pull命令为git pull --rebase           |                                                              |
|                 git config pull.rebase false                 |               修改默认的git pull命令为git pull               |                                                              |
|                    git rm  <文件名.格式>                     |                  在git远端仓库删除一个文件                   |                                                              |
|                git mv <文件名.格式 ><文件夹>                 |         文件名.格式 移动到文件夹。记得commit命令提交         |                                                              |
|               git mv <文件1.格式>< 文件2.格式>               |         重命名文件1重命名为文件2。记得commit命令提交         |                                                              |
|                           git log                            |               查看日志，点击q建就可以退出状态                |                                                              |
|                      git log --oneline                       |                        以简洁方式更改                        |                                                              |
|                git reset --mixed 哈希值（B）                 |                        将指针会退回B                         |                                                              |
|                     git show 哈希值（B）                     |                  B的修改完整信息，按Q退出。                  |                                                              |
|                    git revert 哈希值（B）                    | 反向操作，抵消信息<br />输入完成，点击Esc键退出<br />输入:wq!(输入四个字符)<br />git push命令推送远程 |                                                              |
|                      git commit --amend                      |                      修改上一次的commit                      | 只能修改最后一次                                             |
|                 it commit --amend --no-edit                  |                      修改上一次的commit                      | --no-edit：表示直接使用上次提交的说明，不打开编辑器修改。    |

git后悔药

| git操作 | git命令                                                      | 使用场景                                  | 注意事项                                                     |
| ------- | ------------------------------------------------------------ | ----------------------------------------- | ------------------------------------------------------------ |
| discard | git restore<文件名>（单个文件）<br />git reset --hard(所有文件) | 工作区的修改还么commit                    | 舍弃掉工作区的修改文件                                       |
| reset   | git reset <commit ID>                                        | 还原到某个commit的状态，舍弃之后的commmit | 如果resert已经推送到远端的commit，会造成强制推送，集成分支禁止强推 |
| revert  | git revert <commit ID>                                       | 使用一个新的提交抵消某次commit的修改      |                                                              |
| amend   | git amend <commit ID>                                        | 只能修改最新一次的commmit                 | 如果amend 已经推送到远端commit,会造成强制推送。集成分支禁止强推 |

git 分支命令

| 命令                                  | 意思                                            | 备注                                                         |
| ------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------ |
| git branch                            | 查看本地分支                                    |                                                              |
| git branch -a                         | 查看本地和远端分支                              | 显示绿色的是本地分支，红色显示远端分支                       |
| git  checkout -b 分支名               | 在本地分支上创建分支                            |                                                              |
| git push --set-upstream origin 分支名 | 把远端的和本地的分支关联起来                    |                                                              |
| git switch 分支名                     | 切换分支                                        |                                                              |
| git branch -d 分支名                  | 删除分支                                        | 但是不能删除本分支，需要进行切换<br />分支没有合并使用小写d是不能删除的，需要强制删除命令 |
| git branch -D 分支名                  | 强制删除分支                                    |                                                              |
| git pusah origin --delete  分支名     | 删除远端的分支                                  |                                                              |
| git fetch                             | 同步远端分支                                    | 当远端创建分支之后，本地不会显示，需要同步远端分支           |
| git  checkout  远端分支名             | 关联远端分支在本地端                            |                                                              |
| git merge 分支A                       | 合并本地分支                                    | 第一步：git switch 分支B,切换分支B.<br />第二步：git merge 分支A<br />把分支A合进分支B |
| git merge origin/分支A                |                                                 |                                                              |
| git merge --no-ff 分支名              | 非快速前进合并                                  |                                                              |
| git rebase 分支A                      |                                                 | 第一步：git checkout  分支B<br />git rebase 分支A  <br />将 分支B 变基到 分支A。（分支B移动分支A的后面） |
| git log 分支A ..分支B                 | 比较分支A跟分支B之间**提交**的改动              | 显示的是分支B上有的分支A上没有的改动                         |
| git log 分支A ...分支B                | 比较分支A跟分支B之间**提交**的改动              | 所有差异的都显示，和上面的命令的区别一个..一个...            |
| git diff 分支A ..分支B                | 比较分支A跟分支B之间**文件**的改动              | 显示的是分支B上有的分支A上没有的改动                         |
| git diff 分支A ...分支B               | 把分支B和他们共同的祖先分支进行比较             |                                                              |
| git diff                              | 进行比较，显示的是工作目录和暂存区的差异        |                                                              |
| git diff --staged                     | 进行比较，显示的是暂存区和本地分支的差异        |                                                              |
| git diff HEAD                         | 进行比较，显示的是工作目录和本地分支的差异      |                                                              |
| git diff commit ID1 commit ID12       | 进行比较，显示的是两个commitID的差异            |                                                              |
| git merge --squash 分支A              | 把所有的分支压缩到一个分支合进分支B             | 第一步：git switch 分支B<br />第二步：git merge --squash分支A<br />第三步：git commit -m"squash three into one"<br />第四步:git push<br /> |
| git cherry-pick 哈希值1 哈希值2       | 挑选commmit进行合并                             |                                                              |
| git stash                             | 把工作暂存stash栈中                             |                                                              |
| git stash list                        | 查看当前仓库中所有 **stash（暂存）记录** 的命令 |                                                              |
| git stash -a                          | 保存所有的文件在stash栈                         |                                                              |
| git stash apply "stash@{0}"           | **恢复** stash 内容，**不删除** stash           | "stash@{0}"为系统生成的stash记录名称                         |
| git stash drop "stash@{0}"            | **删除** stash，**不恢复**内容                  |                                                              |
| git stash pop "stash@{0}"             | **恢复** stash 内容并**删除** stash             |                                                              |
| git tag v1.1.0                        | 打标签                                          |                                                              |
| git tag v1.1.0 commit ID              | 给指定的commit打上tag                           |                                                              |
| git  push --tag                       | tag push远端                                    |                                                              |
| git tag -d v1.1.0                     | 删除本地tag                                     |                                                              |
| git push origin --delete v1.1.0       | 删除远端tag                                     |                                                              |
| git diff v1.0.0..v1.0.2               | 对比两个版本                                    |                                                              |
| git rebase -i                         | 可以修改提交历史，交互式变基                    |                                                              |

