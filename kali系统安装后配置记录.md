---
title: kali系统安装后配置记录
date: 2019-02-20 14:30:21
categries: 杂记
---

原本是在博客里的，结果昨天面试官竟然嘲笑我博客里有一个安装kali的，呃.. 感觉他的意思就是我最近才学kali？懒得解释.. 毕竟我也只是用做自己后期的备份而已，没必要放博客里，看来以后博客的内容需要整理整理，不然只会被某些水平不高又自大的面试官diss了，我还想diss他连基本的代码审计的方法都不懂呢[哼哼哼]

### 0x01 apt源更新

```bash
vi /etc/apt/sources.list 
 
#阿里云
deb http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
deb-src http://mirrors.aliyun.com/kali kali-rolling main non-free contrib
 
#官方源
deb http://http.kali.org/kali kali-rolling main non-free contrib
deb-src http://http.kali.org/kali kali-rolling main non-free contrib

apt-get update & apt-get upgrade & apt-get disk-upgrade`
```

### 0x02 open-vm-tools
```bash
apt-get install open-vm-tools*
reboot
```

### 0x03 中文输入法
```shell
apt-get install fcitx fcitx-googlepinyin
```
之后会搜索fcitx会看到小企鹅图标，然后可以对输入法切换什么的进行设置

### 0x04 shadowsocks 
**安装**  

```bash
cd ~ && wget https://github.com/shadowsocks/shadowsocks-qt5/releases/download/v3.0.1/Shadowsocks-Qt5-3.0.1-x86_64.AppImage
chmod a+x Shadowsocks-Qt5-3.0.1-x86_64.AppImage
# 设置开启自启
TODO...
暂时先用`nohup ss &`吧
```
**浏览器插件及配置**   

- proxy（SwitchyOmegaα）安装
- auto-switch 规则配置：Autoproxy : https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt

**系统设置自动代理**   

```bash
# 安装genpac https://github.com/JinnLynn/genpac/blob/master/README.md  
cd ~
pip install genpac
pip install --upgrade genpac
wget https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt
genpac --proxy="SOCKS5 127.0.0.1:1080" --gfwlist-proxy="SOCKS5 127.0.0.1:1080" -o autoproxy.pac --gfwlist-local="gfwlist.txt"
# 系统设置自动代理url为：file:///root/autoproxy.pac
```






