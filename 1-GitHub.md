# 创建新项目

## 在一个分支上工作了一段时间，需要切换到另一分支上

```shell
$ git switch master
error: Your local changes to the following files would be overwritten by checkout:
	function-def--docstring--modules.md
Please commit your changes or stash them before you switch branches.
Aborting
```

现在想要切换分支，但是还不想要提交之前的工作；所以贮藏修改。 将新的贮藏推送到栈上，运行 `git stash`：

```shell
$ git stash
Saved working directory and index state WIP on lesson6: f596ca9 initialize lesson6
```

运行 `git stash pop` 来应用贮藏然后立即从栈上扔掉它：

```shell
$ git stash pop
On branch lesson6
Your branch is up to date with 'origin/lesson6'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   function-def--docstring--modules.md

no changes added to commit (use "git add" and/or "git commit -a")
Dropped refs/stash@{0} (095f36fa8964bc1349ab95f55d6182ccc4710bac)
```

## 在本地新建工作分支并推送至 GitHub

运行 `git push <remote> <branch>`:

```shell
$ git push origin outline
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 558 bytes | 558.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'outline' on GitHub by visiting:
remote:      https://github.com/Xuzhengfu/self-management-with-git/pull/new/outline
remote: 
To https://github.com/Xuzhengfu/self-management-with-git.git
 * [new branch]      outline -> outline
```

现在，你已经将本地新建的工作分支 outline 推送至 GitHub了。打开仓库主页，你会看到 “Your recently pushed branches: outline”。Git 说得很清楚：这是你最近推送上来的分支 outline。

不仅如此，Git 还在贴心地提醒你：

> Create a pull request for 'outline' on GitHub by visiting: https://github.com/Xuzhengfu/self-management-with-git/pull/new/outline
> 通过访问 https://github.com/Xuzhengfu/self-management-with-git/pull/new/outline 在 GitHub 上为 'outline' 创建一个 pull request。

在打开浏览器中打开该链接，你会进入一个 pull request 创建页面。

## 跟踪一个刚刚拉取下来的远程分支

```
$ git branch -u origin/outline
Branch 'outline' set up to track remote branch 'outline' from 'origin'.
```

```
$ git branch -vv
  master  bac852f [origin/master] add .gitignore
* outline d782345 [origin/outline: ahead 1] the first draft
```

## 重命名文件

要在 Git 中对文件改名，可以这么做：

```shell
$ git mv file_from file_to
```

它会恰如预期般正常工作。 实际上，即便此时查看状态信息，也会明白无误地看到关于重命名操作的说明：

```shell
$ git mv README.md README
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    renamed:    README.md -> README
```

其实，运行 git mv 就相当于运行了下面三条命令：

```shell
$ mv README.md README
$ git rm README.md
$ git add README
```

如此分开操作，Git 也会意识到这是一次重命名，所以不管何种方式结果都一样。两者唯一的区别是，`mv` 是一条命令而非三条命令，直接用 `git mv` 方便得多。不过有时候用其他工具批处理重命名的话，要记得在提交前删除旧的文件名，再添加新的文件名。

## 删除完成任务的本地分支

```shell
$ git branch -d chapter-3-1 chapter-3-2 chapter-3-3 chapter-3-4 chapter-3-5 chapter-3-6
Deleted branch chapter-3-1 (was 4698337).
Deleted branch chapter-3-2 (was 7cec657).
Deleted branch chapter-3-3 (was 4bd7a90).
Deleted branch chapter-3-4 (was 924578b).
Deleted branch chapter-3-5 (was b8e4edc).
Deleted branch chapter-3-6 (was a9696e0).
```

## 删除远端跟踪分支

```shell
$ git push origin --delete chapter-3-1
```

## 远端服务器上的分支已被删除，删除本地的跟踪分支

```shell
$ git remote prune origin
Pruning origin
URL: https://github.com/Xuzhengfu/time-as-a-friend-1st.git
 * [pruned] origin/chapter-3-1
 * [pruned] origin/chapter-3-2
 * [pruned] origin/chapter-3-3
 * [pruned] origin/chapter-3-4
 * [pruned] origin/chapter-3-5
 * [pruned] origin/chapter-3-6
```
