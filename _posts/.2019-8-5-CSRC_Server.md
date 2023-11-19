---
layout: post
title: "CSRC服务器"
tagline: "大三暑假在北京计算科学研究中心..."
#categories: 
#author: ""
#meta: ""
---
这几天研究了下中心这边的服务器，这里号称**计算科学研究中心**，服务器的配置确实比我们同济物理学院的服务器好很多。

## **CSRC**

在中心局域网 `ssh` **10.0.0.125** 登录徐辛亮老师课题组的服务器，通过 `showq` 命令可以看到：

![csrc1](https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/csrc.png "CSRC Server")<br>
▲ CSRC服务器节点数

服务器共有64个节点，每个节点配置相同都是24核CPU，物理内存64G，服务器共有1536核。使用 `pbsnodes` 命令查看节点配置：

![csrc2](https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/csrc2.png "CSRC Server")
▲ CSRC服务器每个节点详细配置

## **Tongji Physics**

对比一下我们同济物理学院的服务器，同样使用 `showq` 命令：

![tongji1](https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/tongji.png "Tongji Server")<br>
▲ 同济物理学院服务器节点数

可以看到我们的服务器一共只有12个节点104核，新旧节点的CPU核数以及性能都不相同。使用 **PBS** ( *Portable Batch System* ) 任务管理系统的 `shownodes` 命令查看服务节点的运行情况：

![tongji3](https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/tongji3.png "Tongji Server")
▲ 同济物理学院服务器节点运行情况

可以看到有一些已经没用的节点（ 红背景色 ），以及10个8核CPU和2个12核CPU节点。12核CPU较新，配置较好，有24G物理内存；而8核节点比较旧，物理内存只有16G。我们学院的服务器使用的是联想公司搞的 **LJRS** 任务管理系统 ( *Lenovo Job & Resource Management System* )，类似于 **PBS** 系统， 通过 `ljrsnodes`  查看节点详细配置：

![tongji2](https://raw.githubusercontent.com/NoNo721/Pictures/master/Jekyll/tongji2.png "Tongji Server")
▲ 同济物理学院服务器12核CPU节点详细配置

## **CSRC *VS* &ensp;Tongji Physics**

简单列个表对比一下配置：

Items|CSRC|Tongji Physics
---|---|---
Processors (Total)|1536|104
Processors (Each Node)|24|8 / 12
Nodes|64|12
Physmem (GB)|64|16 / 24

可见同济物理学院的服务器完败。

&ensp;

[<b><u>Go to the Home Page</u></b>]({{ site.url }}{{ site.baseurl }})

&ensp;

<center class="half">
<font color="#26975b"><b>Sponsor the author </b></font><font color="#08a2e4"><b>if you like the contents!</b></font><br/><br/>
</center>

<center class="half">
    <img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/WechatPay.png" width="251" style="margin-right:10px;margin-left:10px"/><img src="https://nono721-1300921342.cos.ap-shanghai.myqcloud.com/AliPay.png" width="250" style="margin-right:10px;margin-left:10px"/>
</center>

&ensp;