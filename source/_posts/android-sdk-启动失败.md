title: "android-sdk 启动失败 "
date: 2015-01-08 12:02:42
tags: android
category: android
---

错误表现：
1，不能分配SD卡大小
2，启动时提示：Failed to start emulator: Cannot run program "/tools/emulator": error=2, No such file or directory

错误处理：
1，在用的架构:
```bash
~# dpkg --print-architecture
```
输出当前的使用的架构，比如amd64 

2，添加架构
```bash
~# dpkg --add-architecture i386
```
3，刷新下源列表
```bash
~# apt-get update
```
4，安装ia32-libs
```bash
~# apt-get install ia32-libs
```