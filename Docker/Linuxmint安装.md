## linux mint 安装

与官方文档ubuntu安装说明不同，按照流程做，会报错。

最后用 `sudo apt install docker.io 直接一步安装成功。`

后续用`sudo docker ps -a` 、 `sudo docker images `、  `sudo docker run hello-world`均测试成功。

但是，虽然测试`docker --version`通过，但`docker-compose --version`提示未安装`docker-compose`

`docker-machine --version`提示命令不存在。

  



