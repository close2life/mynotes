# 建立项目

1. 创建项目

   ```shell
   (django) xdeMacBook-Pro:python x$ django-admin.py startproject HelloWorld .
   ```

   > 末尾的`.`让新项目使用适合的目录结构，有助于开发完成后部署到服务器。

   创建完之后的目录说明：

   * HelloWorld：项目容器。
   * manage.py：命令行工具，可以以各种方式与该项目交互。
   * HelloWorld/\_\_init\_\_.py：一个空文件，告诉python该目录是一个python包。
   * HelloWorld/settings.py：该项目的设置／配置。
   * HelloWorld/urls.py：该项目的URL声明；一份由Django驱动的网站“目录”
   * HelloWorld/wsgi.py：一个WSGI兼容的Web服务器的入口

2. 启动服务器：

   ```shell
   (django) xdeMacBook-Pro:django x$ python3 manage.py runserver
   ```

   ⚠️**注意**：如果出现错误“That port is already in use“，可以更换另外的端口

   ```shell
   (django) xdeMacBook-Pro:django x$ python3 manage.py runserver 8001
   ```



# 视图和URL配置

`url()函数` 可以接收四个参数，分别是两个必选参数：regex、view 和两个可选参数：kwargs、name

* regex：正则表达式，与之匹配的 URL 会执行对应的第二个参数 view。
* view：用于执行与正则表达式匹配的 URL 请求。
* kwargs：视图使用的字典类型的参数。
* name：用来反向获取 URL。

1. 添加视图文件：`HelloWorld/view.py`

   ```python
   from django.http import HttpResponse
    
   def default(request):
   	return HttpResponse('This is a default page ! ')

   def hello(request):
   	return HttpResponse('Hello world ! ')
   ```

2. 绑定 URL 与视图函数：`HelloWorld/urls.py`

   ```python
   from django.conf.urls import url
    
   from . import view
    
   urlpatterns = [
       url(r'^$', view.default), url(r'^hello$', view.hello),
   ]
   ```

   ​

# 模版`template`

1. 新增模版文件：`templates/hello.html`

   ```html
   <h1>{{ hello }}</h1>
   <h1>{{ world }}</h1>
   ```

   > 模板中变量使用了双括号

2. 向Django说明模版文件的路径：`HelloWorld/settings.py`

   ```django
   TEMPLATES = [
       {
           'BACKEND': 'django.template.backends.django.DjangoTemplates',
           'DIRS': [BASE_DIR+"/HelloWorld/templates",],       # 修改位置
   ```

3. 向模版提交数据：`view.py`

   ```python
   from django.shortcuts import render

   def hello(request):
       context = {}
       context['hello'] = 'View show Hello World!'
       context['world'] = 'The world of Django!'
       return render(request, 'hello.html', context)
   ```

   > 使用 render 来替代之前使用的 HttpResponse。
   >
   > render 还使用了一个字典 context 作为参数。
   >
   > context 字典中元素的键值 "hello" 对应了模板中的变量 "{{ hello }}"。

   ​

## 模版标签`templatetag`

### if/else

基本语法：

```django
{% if condition1 %}
   ... display 1
{% elif condiiton2 %}
   ... display 2
{% else %}
   ... display 3
{% endif %}
```

{% if %} 标签接受 and ， or 或者 not 关键字来对多个变量做判断 ，或者对变量取反（ not )，例如：

```django
{% if athlete_list and coach_list %}
     athletes 和 coaches 变量都是可用的。
{% endif %}
```

### ifequal/ifnotequal

比较模板变量 section 和字符串 :

```django
{% ifequal section 'sitenews' %}
    <h1>Site News</h1>
{% else %}
    <h1>No News Here</h1>
{% endifequal %}
```

### for

```django
{% for athlete in athlete_list %}
    <li>{{ athlete.name }}</li>
{% endfor %}
```

反向迭代

```django
{% for athlete in athlete_list reversed %}
...
{% endfor %}
```

### 过滤器`filter`

模板过滤器可以在变量被显示前修改它，过滤器使用管道字符，如下所示：

```django
{{ name|lower }}
```

{{ name }} 变量被过滤器 lower 处理后，文档大写转换文本为小写。

过滤管道可以被* 套接* ，既是说，一个过滤器管道的输出又可以作为下一个管道的输入：

```django
{{ my_list|first|upper }}
```

将第一个元素并将其转化为大写。

有些过滤器有参数。 过滤器的参数跟随冒号之后并且总是以双引号包含。 例如：

```django
{{ bio|truncatewords:"30" }}
```

这个将显示变量 bio 的前30个词。

其他过滤器：

* addslashes : 添加反斜杠到任何反斜杠、单引号或者双引号前面。

* date : 按指定的格式字符串参数格式化 date 或者 datetime 对象，实例：

  ```django
  {{ pub_date|date:"F j, Y" }}
  ```

* length : 返回变量的长度。

### include

允许在模板中包含其它的模板的内容。

```django
{% include "nav.html" %}
```

### 注释

```django
{# 这是一个注释 #}
```

## 模版继承

`base.html`：

```django
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
		<h1>Hello World!</h1>
		<p> Django 测试。</p>
		{% block mainbody %}
		   <p>original</p>
		{% endblock %}
	</body>
</html>
```

名为 mainbody 的 block 标签是可以被继承者们替换掉的部分。

所有的 {% block %} 标签告诉模板引擎，子模板可以重载这些部分。

hello.html 中继承 base.html，并替换特定 block

`hello.html`：

```django
{% extends "base.html" %}
 
{% block mainbody %}<p>继承了 base.html 文件</p>
{% endblock %}
```











1. 创建数据库

   ```shell
   (django) xdeMacBook-Pro:django x$ python3 manage.py migrate
   ```

2. 查看项目，主要校验是否正确创建

   ```shell

   ```

   ​

   ```

   ```



# 创建应用程序

Django项目由一系列应用程序组成。

1. 创建应用程序所需的基础设施。

   ```
   (django) xdeMacBook-Pro:django x$ python3 manage.py startapp learning_logs
   ```







# 管理网站

1. 创建超级用户

   ```
   (django) xdeMacBook-Pro:django x$ python3 manage.py createsuperuser
   ```

   ​