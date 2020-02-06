# 禁用vscode硬件加速

有以下两种方法：

- 启动时加上`--disable-gpu`选项
- `ctrp+shift+p`打开命令面板，找到`Preferences: Configure Runtime Arguments`命令，然后加上`"disable-hardware-acceleration": true`即可。
