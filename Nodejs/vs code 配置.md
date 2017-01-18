运行和调试JavaScript

在VS Code中，我们可以非常方便地运行JavaScript文件。

VS Code以文件夹作为工程目录（Workspace Dir），所有的JavaScript文件都存放在该目录下。此外，VS Code在工程目录下还需要一个.vscode的配置目录，里面存放里VS Code需要的配置文件。

假设我们在C:\Work\目录下创建了一个hello目录作为工程目录，并编写了一个hello.js文件，则该工程目录的结构如下：

```js
hello/ <-- workspace dir
|
+- hello.js <-- JavaScript file
|
+- .vscode/  <-- VS Code config
   |
   +- launch.json <-- VS Code config file for JavaScript
```

可以用VS Code快速创建launch.json，然后修改如下：

```js
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Run hello.js",
            "type": "node",
            "request": "launch",
            "program": "${workspaceRoot}/hello.js",
            "stopOnEntry": false,
            "args": [],
            "cwd": "${workspaceRoot}",
            "preLaunchTask": null,
            "runtimeExecutable": null,
            "runtimeArgs": [
                "--nolazy"
            ],
            "env": {
                "NODE_ENV": "development"
            },
            "externalConsole": false,
            "sourceMaps": false,
            "outDir": null
        }
    ]
}
```

有了配置文件，即可使用VS Code调试JavaScript。





