# GIT将本地的代码提交到新建的远程仓库

我在本地有一个工程，一直没有进行代码托管，打算在git上新建一个仓库进行代码管理，以前我都是建好远程仓库以后clone到本地，然后把本地代码复制粘贴过去，然后在提交。但是最近开始使用cocoapods创建工程，感觉这种复制粘贴不太好，所以有了这篇文章。

终端cd到工程目录

终端输入

```ruby
git init
```

然后

```ruby
git add .
```

.代表add所有文件,继续输入

```ruby
git commit -m 'a commit'
```

引号里是commit的描述

复制好远程git仓库的地址，终端输入

```ruby
git remote add origin https://git.xxxx.com:8443/xxxx/xxxx.git
```

最后

```ruby
git push -u origin master
```

注：

最后这一步如果远程仓库不是空的，比如有README.md文件，就会出错，需要先把远程仓库的文件pull下来(相当于把远程仓库文件clone下来与本地文件合并)

```ruby
git pull --rebase origin master
```

在重新执行

```ruby
git push -u origin master
```

大功告成

---

关键词：git push origin remote fetch cocoapods pod 

