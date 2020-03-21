1、记录GIT使用方法：
git add ***


git status -s 所有状态
git status 查看已被暂存的修改或未被暂存的修改。

git diff 比较差异 ，git diff 本身只显示尚未暂存的改动，而不是自上次提交以来所做的所有改动

.gitignore  维护不需要更新的文件（排除）

若要查看已暂存的将要添加到下次提交里的内容，可以用 git diff --staged 命令。 这条命令将比对已暂存
文件与最后一次提交的文件差异 

git diff --cached 查看已经暂存起来的变化（ --staged 和 --cached 是同义词


git commit --amend
有时候我们提交完了才发现漏掉了几个文件没有添加，或者提交信息写错了。 此时，可以运行带有 --amend 选
项的提交命令来重新提交：
这个命令会将暂存区中的文件提交。 如果自上次提交以来你还未做任何修改（例如，在上次提交后马上执行了
此命令）， 那么快照会保持不变，而你所修改的只是提交信息（最终你只会有一个提交——第二次提交将代替第一次提交的结果。）

取消暂存的文件
你已经修改了两个文件并且想要将它们作为两次独立的修改提交， 但是却意外地输入
git add * 暂存了它们两个。如何只取消暂存两个中的一个呢？ git status 命令提示了你：
git reset HEAD CONTRIBUTING.md
***  git reset 确实是个危险的命令，如果加上了 --hard 选项则更是如此。 然而在上述场景
中，工作目录中的文件尚未修改，因此相对安全一些。***

撤消对文件的修改    git checkout -- Edit.md 
(请务必记得 git checkout -- <file> 是一个危险的命令。 你对那个文件在本地的任何修
改都会消失——Git 会用最近提交的版本覆盖掉它。 除非你确实清楚不想要对那个文件的本地
修改了，否则请不要使用这个命令。)

git remote  -v  查看远程仓库

运行 git remote add <shortname> <url> 添加一个新的远程 Git 仓库，同时指定一个方便
使用的简写(shortname),指定别名
eg: git remote add pb https://github.com/***/***.git
git fetch pb  (使用别名)

从远程仓库中抓取与拉取
 git fetch <remote> 这个命令会访问远程仓库，从中拉取所有你还没有的数据，执行完成后，你将会拥有那个远程仓库中所有分支
的引用，可以随时合并或查看。

如果你使用 clone 命令克隆了一个仓库，命令会自动将其添加为远程仓库并默认以 “origin” 为简写。 所
以，git fetch origin 会抓取克隆（或上一次抓取）后新推送的所有工作。 必须注意 git fetch 命令只会
将数据下载到你的本地仓库——它并不会自动合并或修改你当前的工作。 当准备好时你必须手动将其合并入你的
工作。

推送到远程仓库
当你想分享你的项目时，必须将其推送到上游。 这个命令很简单：git push <remote> <branch>。 当你
想要将 master 分支推送到 origin 服务器时（再次说明，克隆时通常会自动帮你设置好那两个名字）， 那么
运行这个命令就可以将你所做的备份到服务器：
git push origin master
只有当你有所克隆服务器的写入权限，并且之前没有人推送过时，这条命令才能生效。 当你和其他人在同一时
间克隆，他们先推送到上游然后你再推送到上游，你的推送就会毫无疑问地被拒绝。 你必须先抓取他们的工作
并将其合并进你的工作后才能推送。

查看某个远程仓库
如果想要查看某一个远程仓库的更多信息，可以使用 git remote show <remote> 命令。 如果想以一个特
定的缩写名运行这个命令，例如 origin，会得到像下面类似的信息：git remote show origin

这个命令列出了当你在特定的分支上执行 git push 会自动地推送到哪一个远程分支。 它也同样地列出了哪些
远程分支不在你的本地，哪些远程分支已经从服务器上移除了， 还有当你执行 git pull 时哪些本地分支可以
与它跟踪的远程分支自动合并。


远程仓库的重命名与移除
你可以运行 git remote rename 来修改一个远程仓库的简写名。 例如，想要将 pb 重命名为 paul，可以用
git remote rename 这样做   git remote rename pb paul

如果因为一些原因想要移除一个远程仓库——你已经从服务器上搬走了或不再想使用某一个特定的镜像了， 又或
者某一个贡献者不再贡献了——可以使用 git remote remove 或 git remote rm ：  git remote remove origin


打标签
列出标签
在 Git 中列出已有的标签非常简单，只需要输入 git tag 
创建标签
Git 支持两种标签：轻量标签（lightweight）与附注标签（annotated）
轻量标签很像一个不会改变的分支——它只是某个特定提交的引用
轻量标签很像一个不会改变的分支——它只是某个特定提交的引用。
而附注标签是存储在 Git 数据库中的一个完整对象， 它们是可以被校验的，其中包含打标签者的名字、电子邮件
地址、日期时间， 此外还有一个标签信息，并且可以使用 GNU Privacy Guard （GPG）签名并验证。 通常会建
议创建附注标签，这样你可以拥有以上所有信息。但是如果你只是想用一个临时的标签， 或者因为某些原因不
想要保存这些信息，那么也可以用轻量标签。

 git log --pretty=oneline  ,假设在 v1.0 时你忘记给项目打标签   git tag -a v1.0 9fceb02 (校验和或部分校验和)
 
 共享标签
 默认情况下，git push 命令并不会传送标签到远程仓库服务器上。 在创建完标签后你必须显式地推送标签到
共享服务器上。 这个过程就像共享远程分支一样——你可以运行 git push origin <tagname>。
git push origin --tags   这将会把所有不在远程仓库服务器上的标签全部传送到那里


删除标签
要删除掉你本地仓库上的标签，可以使用命令 git tag -d <tagname>。 例如，可以使用以下命令删除一个
轻量标签：
$ git tag -d v1.0
注意上述命令并不会从任何远程仓库中移除这个标签，你必须用 git push <remote>
:refs/tags/<tagname> 来更新你的远程仓库：
第一种变体是 git push <remote> :refs/tags/<tagname> ：
 第二种更直观的删除远程标签的方式是:git push origin --delete <tagname>
 
 
 检出标签
 如果你想查看某个标签所指向的文件版本，可以使用 git checkout 命令， 虽然这会使你的仓库处于“分离头
指针（detacthed HEAD）”的状态
在“分离头指针”状态下，如果你做了某些更改然后提交它们，标签不会发生变化， 但你的新提交将不属于任
何分支，并且将无法访问，除非通过确切的提交哈希才能访问。 因此，如果你需要进行更改，比如你要修复旧
版本中的错误，那么通常需要创建一个新分支
git checkout -b version2 v2.0.0  如果在这之后又进行了一次提交，version2 分支就会因为这个改动向前移动， 此时它就会和 v2.0.0 标签稍微有些不同，这时就要当心了。

Git 别名

git checkout branch 分支切换
