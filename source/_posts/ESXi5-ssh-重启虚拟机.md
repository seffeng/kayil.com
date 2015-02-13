title: ESXi5 ssh 重启虚拟机
date: 2014-11-21 15:14:17
tags: 虚拟化
categories: 虚拟化
---

1、使用自带的命令获得某个虚拟机的 ID 号
    # vim-cmd vmsvc/getallvms
    Vmid   Name                File                 Guest OS      Version   Annotation
    1      test1   [datastore1] test1/test1.vmx   winXPProGuest   vmx-08
    例如：我们要开虚拟机名字叫 test1 ，看到他的 Vmid=1

2、停止虚拟机
    # vim-cmd vmsvc/power.off 1
    例如：我们要停止虚拟机名字叫 test1 ，他的 Vmid=1，运行命令：vim-cmd vmsvc/power.off 1

3、启动虚拟机
    # vim-cmd vmsvc/power.on 1
    例如：我们要停止虚拟机名字叫 test1 ，他的 Vmid=1，运行命令：vim-cmd vmsvc/power.on 1

