title: "ipsec-IP安全策略"
date: 2015-01-08 11:50:27
tags: windows
category: windows
---

控制面板\所有控制面板项\管理工具 >> 本地安全策略 >> IP 安全策略,在本地计算机

1、删除所有策略
``` bash
    netsh ipsec static delete all
```
2、创建IP安全策略（名称=ipsec）
``` bash
    netsh ipsec static add policy name=ipsec
```
3、是否指派该 IPSec 策略（只能指派一个 IPSec 策略）
``` bash
    netsh ipsec static set policy name=ipsec assign=yes|no
```
4、添加IP筛选列表
``` bash
    netsh ipsec static add filterlist name="acp_tcp"
```
5、添加筛选器操作
``` bash
    netsh ipsec static add filteraction name="acc_tcp" action="permit"（允许）
    netsh ipsec static add filteraction name="drop_tcp" action="block"（阻止）
```
6、将筛选器添加到指定的筛选器列表
``` bash
    netsh ipsec static add filter filterlist="acc_tcp" srcaddr=me dstaddr=42.120.184.4 protocol=TCP dstport=80 dstmask=24 description="user.taobao.com"
```
7、用指定的筛选器列表和筛选器操作创建一个规则
``` bash
    netsh ipsec static add rule name="yunxu" policy=ipsec filterlist=acp_tcp filteraction=acp_tcp
    netsh ipsec static add rule name="zuzhi" policy=ipsec filterlist=drop_tcp filteraction=drop_tcp
```