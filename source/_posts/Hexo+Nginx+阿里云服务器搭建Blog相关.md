---
title: Hexo搭建博客
date: 2020-11-2 9:23:46
categories: 
    - 网站
tags: 
    - Web
    - Hexo
    - 阿里云
mp3: 
cover: img/hexo.jpeg
---


## Hexo相关

 1. npm hexo node安装
 2. hexo init blog(此处建议更换国内源,提高初始化速度,github乌龟速度)
 3. hexo g 生成静态页面,hexo s启动本地服务器, hexo d部署到github或者服务器
 

## 服务器相关
 1. nginx,git安装
 2. nginx配置
a.nginx.conf
```bash
server {
  # 侦听80端口
  listen 80;
  # 域名
  server_name www.catnipball.xyz;
  #默认请求
  location / {
    # 网站根目录，此处为你的Hexo部署位置
    root /home/hexo;
    index index.html index.htm;
  }
}
```
b.hooks:post-receive

```bash
#!/bin/sh
git --work-tree=/home/hexo --git-dir=/home/git/blog.git checkout -f
```
c.local hexo项目

```bash
# Deployment
# Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git                                       
  repo: git@你的服务器ip:/home/git/blog.git		
  branch: master  
```
## 问题

 - Nginx 403报错:将conf直接写在nginx.conf文件中;开放80端口
 - 图片无法加载(网页图片链接在github):取消本地hexo配置中github相关

