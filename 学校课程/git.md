# 初始配置

`git config --global user.email "942422490@qq.com"`

`git config --global user.name "mortonlim"`

生成ssh公钥

`ssh-keygen -t rsa -C 942422490@qq.com`

`cat id_rsa.pub`

# 版本库

创建版本库,将目录转换为repository

`git unit`

添加文件到本地repository

`git add 文件名`

提交**所有已添加**的文件到repository

`git commit -m "message"`

每次commit都会保存一个快照,可以版本回退。

# 远程库

将一个本地库与远程库关联

`git remote add origin git@gitee.com:mortonwong/hello.git`

 把本地库的内容推送到远程库(比如多个commit)

`git push -u origin master`

使用克隆来从远程库新建一个本地库