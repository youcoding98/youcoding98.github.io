---
layout: post
title: 【计算机小技能】Github绑定自己的域名
gh-repo: youcoding98/youcoding98.github.io
gh-badge: [star, fork, follow]
tags: [Github]
---
本文前提是你已经搭建好了博客，已经可以通过类似：http://youcoding98.github.io/的方法访问。关于如何搭建博客，有时间会再更新一篇。


## 一、申请域名 
如果没有域名的话，可以先到[阿里云](https://wanwang.aliyun.com/)或者腾讯云去购买一个域名，个人购买不用备案，只需要上传身份证进行身份认证即可。

## 二、添加域名解析
ping你的github.io域名，如youcoding98.github.io，得到一个IP；  
[![yCm3rT.png](https://s3.ax1x.com/2021/01/28/yCm3rT.png)](https://imgchr.com/i/yCm3rT)  
在阿里云修改你的域名解析记录；  
[![yCmJZF.md.png](https://s3.ax1x.com/2021/01/28/yCmJZF.md.png)](https://imgchr.com/i/yCmJZF)  
添加两个A记录，用得到的IP，一个主机记录为：“www”，一个为“@”，这样通过**geloveli.top**和**www.geloveli.top**都能访问到博客了。  
[![yCmcIH.md.png](https://s3.ax1x.com/2021/01/28/yCmcIH.md.png)](https://imgchr.com/i/yCmcIH)  
## 三、新建CNAME文件
在GitHub pages仓库的根目录新建一个CNAME的文件  
[![yCm2id.md.png](https://s3.ax1x.com/2021/01/28/yCm2id.md.png)](https://imgchr.com/i/yCm2id)  
填写上对应解析出来的地址即可，注意不要包含Http://和www，例如如下图：  
[![yCmWRI.md.png](https://s3.ax1x.com/2021/01/28/yCmWRI.md.png)](https://imgchr.com/i/yCmWRI)  

## 四、访问地址
访问 http://geloveli.top/ 即可访问自己的GitHub个人博客  
[![yCm4QP.md.png](https://s3.ax1x.com/2021/01/28/yCm4QP.md.png)](https://imgchr.com/i/yCm4QP)      

## 参考资料
1. [如何绑定自己的域名到GitHub pages](https://www.jianshu.com/p/5b30957fc9ae)  
2. [github怎么绑定自己的域名](https://www.zhihu.com/question/31377141)




