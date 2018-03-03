---
title: git使用
date: 2018-02-05 09:32:09
tags:
---

1. 删除远程目录上的文件夹

```
git rm -r -n --cached  */src/\*      //-n：加上这个参数，执行命令时，是不会删除任何文件，而是展示此命令要删除的文件列表预览。

git rm -r --cached  */src/\*      //最终执行命令删除文件

git commit -m "移除src目录下所有文件的版本控制"    //提交

git push origin master   //提交到远程服务器

```