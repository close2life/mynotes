1. Automator 新建一个 Application

2. 添加一个动作 "Run AppleScript"

3. 代码如下：

   ```
   on run {input, parameters}

   	tell application "Finder"

   	set selection to make new file at (get insertion location)

   	end tell

   	return input

   end run
   ```

4. 保存到 "应用程序"文件夹, 名字姑且叫 "NewFile.app" 吧.

5. Finder 工具栏右键, 自定义, 然后把 New File.app 拖上去, 大功告成