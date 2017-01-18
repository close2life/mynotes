# 在Linux上安装Git

可以试着输入git，看看系统有没有安装Git：

```js
$ git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git
```

`sudo apt-get install git`就可以直接完成Git的安装

---
# 在mac上安装Git
安装homebrew，然后通过homebrew安装Git，具体方法请参考homebrew的文档：[http://brew.sh/](http://brew.sh/)

---
安装完成后，还需要最后一步设置，在命令行输入：

$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

因为Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址。
注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。

