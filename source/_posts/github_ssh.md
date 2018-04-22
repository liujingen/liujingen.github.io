---
title:  完整的 SSH 与 github 绑定
date: 2018-04-22 22:00:00
categories: 编辑器
tags: [sublime]
comments: false
---

> 我们已经对 GitHub 有了一定的了解，包括创建仓库、拉分支，或者通过Clone or download克隆或者下载代码；我们也下载并安装了 Git，也了解了其常用的命令。But，无论是 GitHub，还是 Git，我们都是单独或者说是独立操作的，并没有将两者绑定啊！也就是说，我们现在只能通过 GitHub 下载代码，并不能通过 Git 向 GitHub 提交代码。
因此，在本篇博文中，我们就一起完成 Git 和 GitHub 的绑定，体验通过 Git 向 GitHub 提交代码的能力。不过在这之前，我们需要先了解 SSh（安全外壳协议），因为在 GitHub 上，一般都是通过 SSH 来授权的，而且大多数 Git 服务器也会选择使用 SSH 公钥来进行授权，所以想要向 GitHub 提交代码，首先就得在 GitHub 上添加 SSH key配置。

### 第 1 步：生成 SSH key

我们首先在 `git Bash` 里边输入 `ssh` 来查看本机是否安装了SSH
```
$ ssh
usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file]
           [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           [user@]hostname [command]
```

<!-- more -->

如上图所示，此结果表示我们已经安装 SSH 啦！接下来，输入ssh-keygen -t rsa命令表示我们指定 RSA 算法生成密钥，然后敲三次回车键，期间不需要输入密码，之后就就会生成两个文件，分别为id_rsa和id_rsa.pub，即密钥id_rsa和公钥id_rsa.pub

密钥和公钥生成之后，我们要做的事情就是把公钥id_rsa.pub的内容添加到 GitHub，这样我们本地的密钥id_rsa和 GitHub 上的公钥id_rsa.pub才可以进行匹配，授权成功后，就可以向 GitHub 提交代码啦！

### 第 2 步：添加 SSH key

![Alt text](../images/1.png)

如上图所示，进入我们的 GitHub 主页，先点击右上角所示的倒三角▽图标，然后再点击`Settins`，进行设置页面；点击我们的头像亦可直接进入设置页面：

![Alt text](https://img-blog.csdn.net/20170404134608330)

如上图所示，进入`Settings`页面后，再点击`SSH and GPG Keys`进入此子界面，然后点击New SSH key按钮：

![Alt text](https://img-blog.csdn.net/20170404135835070)

如上图所示，我们只需要将公钥`id_rsa.pub`的内容粘贴到Key处的位置（Titles的内容不填写也没事），然后点击`Add SSH key` 即可。



