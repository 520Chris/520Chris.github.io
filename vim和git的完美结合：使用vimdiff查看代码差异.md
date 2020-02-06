# vim和git的完美结合：使用vimdiff查看代码差异

先配置git

```bash
git config --global diff.tool vimdiff
git config --global difftool.prompt false
git config --global alias.d difftool # 给difftool起个别名d
```

配置好了之后，在命令行中运行`git d`，即可查看代码差异。`:qa`可以查看下一个文件的代码差异。
