

# Git随笔记录



## git config

查看已设配置

```shell
git config -l
```



## git 提交时的用户和邮箱

查看全局的设置中的用户和邮箱

```git
git config --global user.name 
git config --global user.email
```

查看当前的设置中的用户和邮箱

```git
git config user.name 
git config user.email
```

要是想修改的话直接在查看命令后加要修改的值如:

```
git config user.name "YourName"
```



## git stash恢复

```git
git stash pop stash@{num}
```



## git remote

`git remote`命令列出所有远程主机，使用`-v`选项，可以参看远程主机的网址

`git remote add`命令用于添加远程主机。

`git remote rm`命令用于删除远程主机。

`git remote rename`命令用于远程主机的改名。



## git 设置代理

```bash
git config --global http.proxy "localhost:1080" 
git config --global --unset http.proxy
```



## SSL证书时, Git不能工作之解决办法

```bash
export GIT_SSL_NO_VERIFY=1  #Linux
set GIT_SSL_NO_VERIFY 1 #windows
git config --global http.sslVerify false
```



## Git配置Unix换行符

使用Windows开发经常会遇上换行符不匹配的问题, 代码对比工具会告诉你‘Contents have differences only in line separators’，什么意思? 在Unix中，换行符为\n(LF)，而在Windows下，换行符为\r\n(CRLF)。通过配置Git，也可以避免换行符不匹配的问题。



**core.autocrlf** 这一配置项能够自动在commit或check out时转换两种换行符。

`check out`代码时，换行符会自动由LF转换为CRLF，而在commit时，Git也会将CRLF转换为LF，以方便在Windows上开发。

```shell
$ git config --global core.autocrlf true
```



`check out` 代码时，不会有任何的转换发生，而在commit代码时，Git仍旧会把CRLF转换为LF。这个选项推荐Mac开发者使用。

```shell
$ git config --global core.autocrlf input
```



整个自动转换就会被关闭，比较适合大家都在同一种系统上进行开发的工程。此时也可配置core.eol(ending of line)来规定本地仓库的统一规则，选项为lf/crlf/native。

```shell
$ git config --global core.autocrlf false
```



**core.safecrlf** 这一配置项能够在commit代码时检查是否混用了换行符。

Git会在提交时进行检查，并拒绝混用了换行符的文件的提交

```shell
$ git config --global core.safecrlf true
```



Git会在提交时进行检查，并提示警告

```shell
$ git config --global core.safecrlf warn
```



Git不会在提交时进行检查

```shell
$ git config --global core.safecrlf false
```



