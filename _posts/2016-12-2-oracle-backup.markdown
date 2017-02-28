---
layout: post
title:  "oracle 备份与恢复"
date:   2016-12-2 16:32:49 +0800
category: 201612
tags: oracle
---
oracle数据库的备份与恢复  RMAN备份以及各种备份策略  Data guard

<!--break-->

数据泵expdp 导出需注意点

	可以切换用户导，使用remap_schema=原用户名:切换后的用户名
	
	如果是rac多节点导出，开启parallel并发导出后，expdp会在各节点设置的directory导出数据文件，
	此时若其他数据库节点的directory未设置，会导致导出报错，但导出不会中断，减慢整体的导出时间，
	该种情况使用cluster=n来避免
	
	
