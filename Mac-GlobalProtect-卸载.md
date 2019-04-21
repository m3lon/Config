---
title: Mac GlobalProtect 卸载
date: 2019-02-27 15:34:32
categories: 杂记
---

global protect是访问公司网络用的，比较流氓，杀掉进程会自动重新启动（终端 kill id）。只要删除Info.plist，就不会自动启动了  
1. 删除文件Info.plist（mac启动该程序时使用）
```shell
  sudo rm  /Applications/GlobalProtect.app/Contents/Info.plist
```
2. 活动监视器杀掉global protect进程
3. 应用程序中把global protect移到废纸篓
