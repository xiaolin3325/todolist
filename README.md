1、记录GIT使用方法：
git add ***


git status -s 所有状态
git status 查看已被暂存的修改或未被暂存的修改。

git diff 比较差异 ，git diff 本身只显示尚未暂存的改动，而不是自上次提交以来所做的所有改动

.gitignore  维护不需要更新的文件（排除）

若要查看已暂存的将要添加到下次提交里的内容，可以用 git diff --staged 命令。 这条命令将比对已暂存
文件与最后一次提交的文件差异 

git diff --cached 查看已经暂存起来的变化（ --staged 和 --cached 是同义词）