# git学习速查

`git init`

创建仓库并初始化

`git add <file>`

将文件添加到暂存区

`git commit -m "something"`

将文件添加到版本库

`git status`

查看工作区当前状态，包括文件的修改等

`git diff <filename>`

查看文件被修改的内容

`git log`

查看修改日记，加上 `--pretty=oneline` 可以以简单方式输出。 输出的一大串数字是使用 HSA 加密算法生成的十六进制序号，表示当前版本的编号。会始终伴随这个版本。

`git log` 如果太长不退出则按 q 退出 log 参数 `--graph` 可以显示分支合并图

`git reset --hard HEAD^`

回退到上一个版本，HEAD 表示当前版本。HEAD^ 表示上一个，HEAD^^ 表示上两个。HEAD~100 表示上面100个。 用了这个之后再用 `git log`，回退之前的记录会消失。但是可以通过版本号找回来。 `git reset --hard 1094a`

`1094a` 即目标版本编号（commit id）的前几位，一般提供前几位即可。 `HEAD` 是一个指针，将指针指向当前版本。 `reset` 可以改变指针指向。 `reset` 也可以吧暂存区的修改退回到工作区。

`cat <filename>`

查看当前文件内容

`git reflog`

记录了每一次命令，可以通过这个寻找到目标版本编号。

**工作区**：当前电脑的目录

**版本库**：即隐藏文件 `.git`，其中包括暂存区 `stage`，以及分支 master，还有指向 master 的指针 `HEAD`。

文件———add————暂存区————commit————版本库

`git diff <first> -- <second>`

比较first和second的不同

其中之一可以为HEAD，代表当前版本

`git checkout -- <file>`

当工作区的文件修改之后，可以通过 `git checkout` 还原到当前版本 即还原到最近的 `git add` 或者 `git commit` 版本

`rm <file>` 移除目标文件

`git rm <file>` 从版本库移除目标文件 将本地文件推到 github 远端上（先有本地库后有远程库）： 将本地的 SSH 添加到 github 账号之后 `git remote add origin git@github.com:exampleA/exampleB.git`

后面exampleA和exampleB为库的网络地址

遇到SSH警告回复yes即可

远程库的名字就是origin，也可以用别的，但是origin为习惯性的远程库用法

第一次将本地库的所有内容推送到远程库上：

（在master分支上操作的） `git push -u origin master`

`-u` 参数将本地分支 master 和远程分支 master 相互连接起来 之后工作只需要提交 `git push origin master` 即可。

一般开发先创建远程库再从远程库克隆。

先在 github 上创建远程库

然后执行命令

`git clone git@github.com:exampleA/exampleB.git`

把地址换成远程库的网络地址。 这样可以节省掉将SSH警告之类的

而且如果在远程库中创建了 readme 会因为不同而无法上传分支：

HEAD 严格上来说，先指向 master 这个分支，master 再指向一个版本。

现在创建一个 dev 分支，HEAD 指向的是 dev，然后指向一个版本。

`git checkout -b dev`

在当前分支创建并切换到 dev 分支上

相当于两条指令的结合：

`git branch dev` 和 `git checkout dev`

`git branch`

查看当前分支，所在分支为绿色字体并在前面有分号

`git merge <branch>`

将目标 branch 整合到 master 这个分支上

git 推荐现在某个分支完成任务之后再把工作整合到 master 上。

这和在 master 上完成工作效果是一样的，并且过程更安全。

完成后可以删除分支

`git branch -d <name>`

在合并分支过程中，`git merge`如果可以会使用 Fast forward 来合并分支，但会丢掉分支的内容。

加入参数 --no-ff 可以强制禁止 fast forward 但会提交一个新的 `commit` 因此最好加入 `-m`。

比如 `git merge --no-ff -m"merge with no-ff" dev`

`git stash`

储藏当前的工作现场，之后还可以恢复。

`git stash list`

查看当前所有储藏的工作现场列表

`git stash apply`

恢复工作现场，可以加上 `@{n}` 来恢复指定数字n的工作现场

`git stash drop`

删除工作现场

`git stash pop`

弹出工作现场，即先恢复后删除

`git branch -D <name>`

强行删除一个分支
