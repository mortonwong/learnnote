https://www.liaoxuefeng.com/wiki/896043488029600/897271968352576

初始配置，global可选

```bash
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

初始化repository

```bash
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/
```

添加文件到git

```bash
$ git add readme.txt
```

提交文件到git

```bash
$ git commit -m "wrote a readme file"
```

查看有无文件没被提交

```bash
$ git status
```

查看文件修改历史

```bash
$ git diff readme.txt 
```

显示从最近到最远的提交日志，

```bash
$ git log
```

版本回退

- `HEAD`指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`。
- 穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。
- 要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。