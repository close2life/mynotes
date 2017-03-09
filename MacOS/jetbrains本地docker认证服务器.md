认证jetbrains系列ide时点选license, 并填写http://127.0.0.1:20701

如果要提供服务给团队使用，记得把127.0.0.1 替换为 相应的外网ip。

## 临时认证搭建

```
docker run -it --rm -p 20701:20701 woailuoli993/jblse:0.2.0
```

## version 0.2.0

增加了自定义认证用户名参数。

## usage

```
docker pull woailuoli993/jblse:0.2.0
```

- 使用默认认证用户名

  ```
  docker run -d --name="jblse" -p 20701:20701 woailuoli993/jblse:0.2.0
  ```

- 使用自定义用户名

  ```
  docker run -d --name="jblse" -p 20701:20701 woailuoli993/jblse:0.2.0 -u coldplay
  ```

- 以上命令建立了一个认证用户名为coldplay的认证服务。

如果不想用这个端口， -p 后面的 第一个20701 也可以修改成别的。