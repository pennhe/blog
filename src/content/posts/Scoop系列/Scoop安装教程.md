---
title: Scoop 安装教程
published: 2025-02-08
description: Scoop 安装教程
tags: [Scoop, Windows]
category: Scoop
draft: false
lang: zh_CN
---

## 安装Scoop

##### 1. 在 PowerShell 中打开远程权限

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

##### 2. 设置安装路径

```powershell
# 用户安装
$env:SCOOP='D:\Scoop'
[environment]::setEnvironmentVariable('SCOOP',$env:SCOOP,'User')

#全局安装
$env:SCOOP_GLOBAL='D:\Scoop_Global'
[environment]::setEnvironmentVariable('SCOOP_GLOBAL',$env:SCOOP_GLOBAL,'Machine')
```

##### 3. 安装Scoop

```powershell
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
或
iwr -useb get.scoop.sh | iex
或
iex (new-object net.webclient).downloadstring('https://get.scoop.sh') 

#更新
scoop update
```

此时大概率会执行失败，可以更换国内源来安装 或者 修改Host文件，使网络畅通

1. 使用国内源来安装
   
   ```powershell
   iwr -useb scoop.201704.xyz | iex
   scoop update
   ```

2. 修改Host文件
   
   [GitHub地址](https://github.com/521xueweihan/GitHub520)
   
   获取host内容
   
   - 文件：`https://raw.hellogithub.com/hosts`
   
   修改host内容
   
   - Windows 系统：`C:\Windows\System32\drivers\etc\hosts`
   
   刷新DNS
   
   - Windows 系统：`ipconfig /flushdns`

###### 安装基础软件和配置

安装 7zip git aria2

```powershell
scoop install 7zip git aria2
```

开启使用aria2下载

```powershell
scoop config aria2-enabled true
# 如果使用代理，有时需要通过如下命令关闭 aria2
scoop config aria2-enabled false
```

更换镜像源

```powershell
# 查看当前镜像源
scoop config
# 设置国内镜像源
scoop config SCOOP_REPO 'https://gitee.com/glsnames/scoop-installer'
scoop config SCOOP_REPO https://gitee.com/glsnames/scoop-installer
scoop config SCOOP_REPO https://github.com/ScoopInstaller/Scoop
# 设置官方镜像源
```

配置aria2开启16线程加速下载

```powershell
scoop config aria2-retry-wait 4
scoop config aria2-split 16
scoop config aria2-max-connection-per-server 16
scoop config aria2-min-split-size 4M

# 查看配置情况
scoop config
/*
aria2-retry-wait                : 4
aria2-split                     : 16
aria2-max-connection-per-server : 16
aria2-min-split-size            : 4M
*/
```

###### 配置bucket

官方的一些源 可以放心使用的

```powershell
scoop bucket main [已经默认在bucket中了，无需手动添加]
scoop bucket extras 
scoop bucket versions
scoop bucket dorado
scoop bucket sysinternals
scoop bucket nerd-fonts
scoop bucket java
scoop bucket games
scoop bucket jetbrains
```

官方的Bucket地址在国内使用有点慢，可以用gitee上镜像地址

[scoop-bucket - Gitee.com](https://gitee.com/organizations/scoop-bucket/projects)

```powerquery
scoop bucket add extras https://gitee.com/scoop-bucket/extras
scoop bucket add main https://gitee.com/scoop-bucket/main
scoop bucket add dorado https://gitee.com/scoop-bucket/dorado
scoop bucket add java https://gitee.com/scoop-bucket/java
scoop bucket add versions https://github.com/ScoopInstaller/Versions
```

其他的一些三方Bucket

```powershell
# scoop-cn 中国用户能用的 Scoop 应用库，每日同步 Scoop 的官方库，加速应用的下载速度
scoop bucket add scoop-cn https://mirror.ghproxy.com/https://github.com/duzyn/scoop-cn

# spc 适合中国大陆用户使用的 Scoop buckets 代理镜像库
scoop bucket add spc https://mirror.ghproxy.com/github.com/lzwme/scoop-proxy-cn
```
