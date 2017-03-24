# Message: 'chromedriver' executable needs to be in PATH

路径错误，修复方法：

下载chromedriver安装包：[https://sites.google.com/a/chromium.org/chromedriver/downloads](https://sites.google.com/a/chromium.org/chromedriver/downloads)

然后解压移动到目录 `/usr/local/bin`

命令如下：

```
$unzip chromedriver_mac64.zip 

$mv chromedriver /usr/local/bin

$cd /usr/local/bin

$chmod a+x chromedriver
```

