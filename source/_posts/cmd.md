---
title: 常用命令集
date: 2019-02-07 23:01:46
categories: 收藏
tags:
  - Linux
---

## Linux 常用命令集
- 查看磁盘空间 `df -ha`
- 查看端口占用情况 `netstat -tlnp | grep 4000`，其中p参数会显示进程id，可以直接`kill -9 ${pid}`即可释放端口资源