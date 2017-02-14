1. 拉取官方的Ubuntu镜像。

   `sudo docker pull ubuntu`

2. 创建容器并进入容器，运行一个bash。

   `sudo docker run -ti ubuntu /bin/bash`

   如果已经有了一个容器，可以直接运行，并进入

   ```
   sudo docker start 6a75afw7w8e
   sudo docker exec -ti 6a75afw7w8e /bin/bash
   ```

3. 安装apache2，mysql

   ```
   apt-get update
   apt-get install apache2
   apt-get install mysql-server
   ```

4. 启动

   ```
   service apache2 start
   service mysql start
   ```

5. 验证

   ```
   curl 127.0.0.1
   netstat -tap | grep mysql
   ```

6. 修改apache文档路径

   在` /etc/apache2/sites-available` 中修改 `000-default.conf `中的`DocumentRoot /var/www/` 修改为想要的目录。比如：`DocumentRoot /var/www/html/mainpage`

7. 运行容器，并映射文件路径及端口

   `sudo docker run -d --name php -v /home/x/Codes/CodePractice/php:/app -p 8080:80 -p 3306:3306 ubuntu`


