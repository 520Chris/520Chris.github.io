# node和npm命令报错：Segmentation fault

重新安装`node`和`npm`即可，但是要保证之前的都**删除干净**。

删除操作：

1. `sudo apt remove nodejs nodejs-legacy npm`

2. 再用`n`命令找到系统里已经安装的所有`nodejs`版本，然后**全部删除**。

3. 保证系统里没有`node`, `nodejs`, `npm`, `n`这四个可执行命令, 如果还有就用`rm`删除。

然后重新安装`node`即可：

```bash
sudo apt install -y nodejs nodejs-legacy npm
sudo npm config set registry https://registry.npm.taobao.org
sudo npm install -g n
sudo n stable
```
