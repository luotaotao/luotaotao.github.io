---
layout: post
title:  "archive log 相关"
date:   2016-12-09 10:54:49 +0800
category: 201612
tags: [oracle] 
---
oracle数据库归档日志的相关知识

<!--break-->

	查看是否为归档模式，归档目标位置，归档日志列表信息
	archive log list;
	select * from v$archived_log order by sequence#;
	
	查看归档位置参数
	show parameter log_archive_dest
	
	修改归档位置
	ALTER SYSTEM SET log_archive_dest_1='localtion=/oracle/backup_m' SCOPE=spfile   重启后才生效
	ALTER SYSTEM SET log_archive_dest_1='localtion=/oracle/backup_m' SCOPE=both  不用重启立即生效
