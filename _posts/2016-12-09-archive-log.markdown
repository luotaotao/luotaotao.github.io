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
	
	释放dg备库，取消归档
	alter system set log_archive_config='dg_config=(dlltcxff,dlltcxff_st1)' scope=both sid='*';
	alter system set LOG_ARCHIVE_DEST_2=''scope=both sid='*'; 
	alter system set FAL_SERVER=dlltcxff_st1 scope=both sid='*'; 
	注：实例名修改为自己单位的。
	
	统计每日产生的归档量
	  方法一：
	  select 
	  trunc(completion_time) as "Date"
	 ,count(*) as "Count"
	 ,sum(blocks * block_size) /1024 /1024 as "MB"
	 from v$archived_log
	 group by trunc(completion_time);
	 方法二：
	 切换到grid用户，asmcmd进入到asm命令行：lsdg（查看asm盘使用情况），常规操作命令du可统计文件大小
	 
	
