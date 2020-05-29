# 创建新项目

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