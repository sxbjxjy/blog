---
layout: post
title: 无法导出文件错误
date: 2022-11-01
category: Other
---

开发环境构筑后，无法从D365的Table Browser或者SSRS report导出Excel文件。

错误信息：No connection could be made because the target machine actively refused it 127.0.0.1:10002

原因：Azure Storage Emulator没有启动。

解决方法：Windows搜索栏输入`Azure Storage Emulator`，启动。
