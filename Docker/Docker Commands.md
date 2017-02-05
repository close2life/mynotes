1. `docker ps`

   查看正在运行中的container

   `docker ps -a`

   查看所有的container

2. `docker run -d -p 80:80 --name webserver nginx`

   在一个container中启动nginx

3. `docker start webserver`  `docker stop webserver`

   启动某个container中的服务

4. `docker rm -f webserver`

   删除某个container，但不是nginx image

5. `docker images`

   查看现存的images

6. `docker rmi nginx`

   删除nginx image

7. `docker exec -ti a4d8c1ae7878 /bin/bash`

   进入容器内部，并启动一个bash

8. ​