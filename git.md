# git常用命令
## 安装
sudo apt-get install git

## 创建版本库
git init

## 从远程库克隆
git clone git@github.com:close2life/myaides.git

## 提交文件
git add readme.md

git commit -m "wrote a readme"

> 如果提交时提示需要输入用户名和邮箱，需要添加全局变量
git config --global user.name "close2life"
git config --global user.email "1qaz@WSX"
