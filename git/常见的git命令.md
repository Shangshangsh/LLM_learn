# git命令
本文记录了工作中git的学习，不按照功能划分，而是按照时间线划分，即一开始就会的到不断掌握的

## 经典三件套 保存-记录更改-上传
最简单的三件套，首先是保存。当你在git clone下来一个项目后，自己修改完，想要上传回仓库，此时应该

1：首先是保存
```
git add .
```

2：然后是记录

```
git commit -m "这里写这次修改了什么"

3:最后是上传

```
git push
```

## 进阶——链接远程
当已经git下载项目，你在本地修改了代码，但是没填，像上传时，但是项目名称变了。此时你想:1:链接远程（不是clone），2：将改的代码提交

情况一：本地没有配置

首先需要先进入你的目录
```
cd /path/to/your/local/project
```

然后init

```
git init
```
然后连接到仓库，
```
git remote add origin cd git@github.com:ShiangHou/LLM_learn.git
```
剩下的就是三件套了

情况二：之前已经链接过了，但是远程改了（比如改名字了）

```
git remote add origin git@github.com:ShiangHou/LLM_learn.git
```
即修改现有的仓库命令就行

