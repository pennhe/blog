---
title: Scoop 常用命令
published: 2025-02-08
description: Scoop常用命令
tags: [Scoop, Windows]
category: Scoop
draft: false
lang: zh_CN
---

### 清除缓存
``` shell
scoop cache rm *
```


### 清除历史版本
``` shell
scoop cleanup * -g -k
```

- `-g` 指的是全局地Cleanup
- `-c` 指的是包括删除过期地下载缓存