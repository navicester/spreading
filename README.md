[Markdown语言详解](http://www.kuqin.com/shuoit/20141125/343459.html)  
[http://mahua.jser.me/](http://mahua.jser.me/)  
[http://maxiang.info/](http://maxiang.info/)  

-------------------

[TOC]  


## New repository

## Install client msysgit

## Congiure git
以[spreading](https://github.com/navicester/spreading)为例

### Create ssh key
```
ssh-keygen -t rsa -C your_email@youremail.com
```
```
$ ssh-keygen -t rsa -C navicester@qq.com
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/bhe001/.ssh/id_rsa):
/c/Users/bhe001/.ssh/id_rsa already exists.
Overwrite (y/n)? y
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/bhe001/.ssh/id_rsa.
Your public key has been saved in /c/Users/bhe001/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:+iKp4YC2DXNqjcluAz2EBIaOirvaozd9wpwMvZsFFVk navicester@qq.com
The key's randomart image is:
+---[RSA 2048]----+
|+.    .oE        |
|o.    ..         |
|+.    .          |
|o..  .           |
|oo ..   S        |
|= + .. .         |
|===O +o          |
|o@@o@oo.         |
|OB==o= ..        |
+----[SHA256]-----+
```
后面的 your_email@youremail.com 改为自己的邮箱，之后会要求确认路径和输入密码，这里使用默认的一路回车就行。成功的话会在 ~/ 下生成 .ssh 文件夹，打开 id_rsa.pub，复制里面的 key，回到 github，进入 settings，左边选择 SSH keys，Add SSH Key，title 随便填，粘贴 key。

### Verify ssh key
```
ssh -T git@github.com
ssh -T -v git@github.com 可以打印debug信息
```
``` markdown
$ ssh -T git@github.com
Hi navicester! You've successfully authenticated, but GitHub does not provide shell access.
```
如果是第一次的会提示是否 continue，输入 yes 就会看到：You've successfully authenticated, but GitHub does not provide shell access，这就表示已成功连上 github。

常见问题1:[关于ssh连接主机，git连接github失败的问题](http://blog.csdn.net/sunnypotter/article/details/18948053)

### Clone your project
接下来我们要做的就是把 github 上面建立的仓库克隆到本地，在此之前还需要设置 username 和 email，因为 github 每次 commit 都会记录他们。

``` python
git config --global user.name your name
git config --global user.email your_email@youremail.com

git config --global user.name navicester
git config --global user.email navicester@qq.com
```
克隆到本地 (spreading)
```
git clone git@github.com:navicester/spreading.git
```

```markdown
$ git clone git@github.com:navicester/spreading.git
Cloning into 'spreading'...
remote: Counting objects: 86, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 86 (delta 1), reused 0 (delta 0), pack-reused 84
Receiving objects: 100% (86/86), 14.18 KiB | 0 bytes/s, done.
Resolving deltas: 100% (20/20), done.
Checking connectivity... done.
```
需要注意的是：github 提供了 3 种 url 路径（HTTPS，SSH，Subversion），一般如果账号处于登录状态，那么我们可以用 SSH，就像上面的代码，如果没有登录的话，只能用 HTTPS 的 url 了，如图所示：
克隆成功，如下所示：

## Pull

## Modify, Commit, Push
我们可以修改克隆到本地的项目，修改完成后先要 add 修改的文件（. 表示全部），然后填写 commit，最后在 push 到 github。
```
git add .
git commit -m 'update'
git push
```
## gitignore
比如我要忽略sumlime项目文件
lwc.sublime-project
lwc.sublime-workspace
```
touch  .gitignore     #创建gitignore隱藏文件  
vim    .gitignore     #编辑文件，加入指定文件 
#下面是我的gitignore文件的内容  
#忽略gitignore文件  
.gitignore  
#忽略后缀缀名为.o和.a的文件  
*.[oa]  
#或有sublime项目文件  
lwc.sublime-project
lwc.sublime-workspace
```

## git status

