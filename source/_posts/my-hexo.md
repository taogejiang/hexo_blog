title: Hexo博客搭建全过程
categories: 知识体系
tags:
  - hexo
  - cloud studio
  - yilia
date: 2019-02-06 17:14:04
---
### Hexo博客搭建操作整理
项目 | 简介 | 链接
:--- | :--- | :---
驱动引擎 | Hexo官网 | [Hexo](https://hexo.io/)
服务器 | Cloud Studio 腾讯云 | [基于 Cloud Studio + Hexo 创建个人博客](https://dev.tencent.com/s/87dd23ee-b405-4ceb-848e-ad1b0c8f609b)
博客主题 | 博客的样式风格 | [Yilia](https://github.com/litten/hexo-theme-yilia)
Yilia定制 | Yilia源码目录结构及构建须知 | [Yilia源码目录结构及构建须知](https://github.com/litten/hexo-theme-yilia/wiki/Yilia%E6%BA%90%E7%A0%81%E7%9B%AE%E5%BD%95%E7%BB%93%E6%9E%84%E5%8F%8A%E6%9E%84%E5%BB%BA%E9%A1%BB%E7%9F%A5)
Yilia定制 | 提升效率 | [Yilia删除上报](https://github.com/litten/hexo-theme-yilia/pull/786)
Yilia定制 | 源主题代码中微信分享生成二维链接已失效，需优化 | [Yilia修改微信分享二维码生成方式](https://github.com/litten/hexo-theme-yilia/pull/779)
Yilia定制 | 文章时间如果为今天则显示“今天” | [文章时间如果为今天则显示“今天”](https://github.com/litten/hexo-theme-yilia/pull/462)
博客插件 | IP计数统计 | [“不蒜子”计数器](http://ibruce.info/2015/04/04/busuanzi/)
博客插件 | 文章字数+阅读时长统计(_个人感觉意义不大_) | [Hexo-WordCount](https://github.com/willin/hexo-wordcount)
博客插件 | Hexo文章加密码 | 
博客插件 | 文章置顶插件 | 
博客插件 | Valine评论 | 
博客插件 | Valine评论提醒 | 
博客插件 | Hexo管理插件 | [Hexo Admin Plugin](https://github.com/jaredly/hexo-admin)

### Hexo博客搭建踩过的坑
##### 坑：版本重置或文件名称更新时，文章部分连接失效404
1.清理浏览器缓存后可解决

2.文件名称修改为全英文且不带空格

##### 坑：hexo deploy 部署时总是提示输入用户名和密码 
调整deploy的设置，可参考如下:
```
# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  message: hexo deploy to git for master 
  repo:
    #github: <repository url>,[branch]
    #coding: https://git.dev.tencent.com/taogejiang_study/blog.git,master ### 此种设置部署时需要提供用户名和密码
    coding: git@git.dev.tencent.com:taogejiang_study/blog.git,master ###此种设置可免密
```
##### 坑：hexo admin 部署时报ENOENT错误 
调整deploy的_config.yml的设置，可参考如下:
```
# hexo-admin authentification
admin:
 deployCommand: ./shell/hexo_deploy.sh ##需要加可执行权限
```
```
cat ./shell/hexo_deploy.sh
#!/usr/bin/env sh
cd ~/blog.hexo/shell
hexo clean && hexo deploy
```