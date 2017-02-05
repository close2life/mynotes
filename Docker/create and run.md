## 创建自己的lamp

1. 创建新的工作目录：

   ```
   $ mkdir lamp
   $ cd lamp
   $ touch Dockerfile
   ```

2. 创建Dockerfile文件，内容为：

   ```
   FROM tutum/lamp:latest
   RUN rm -fr /app && git clone https://github.com/username/customapp.git /app
   #这里将https://github.com/username/customapp.git 地址替换为你自己的项目地址
   EXPOSE 80 3306
   CMD ["/run.sh"]
   ```

3. 创建镜像，命名为 close2life/mylamp

   ```
   $ docker build -t close2life/mylamp .
   ```



## 运行自己的lamp

指定-d参数，让容器后台运行

-P是允许外部访问容器需要暴露的端口

-v标记也可以指定挂载一个本地的已有目录到容器中去作为数据卷

```
sudo docker run -d --name php -v /home/x/Codes/CodePractice/php:/app -p 8080:80 -p 3306:3306 close2life/mylamp
```

检查是否启动成功

```
$ curl http://127.0.0.1:8080/
```

