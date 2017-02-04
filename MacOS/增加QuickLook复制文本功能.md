1. 终端输入命令：

   `defaults write com.apple.finder QLEnableTextSelection -bool TRUE`

2. 再输入：

   `Killall Finder`

   该指令会重启finder，之后就生效了。

3. 如果要取消，将第一条指令的 `TRUE` 修改成 `FALSE ` 即可。