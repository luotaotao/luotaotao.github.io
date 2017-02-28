---
layout: post
title:  "oracle 存储过程 函数"
date:   2017-01-19 9:51:49 +0800
category: 201701
tags: oracle
---
存储过程 函数 oracle开发相关

<!--break-->

查看存储过程编译状态，是否编译成功

	SQL> select status from user_objects where object_name= '存储过程名称 ';  
	STATUS  
	-------  
	INVALID
	创建的时候会给出提示,"好像是带有编译错误的提示"
	第三方工具查看存储过程,会发现有XX之类的提示
	
	sql适合处理批量数据，而程序开发更偏向流程性
	
where子句和having子句对比

	在查询过程中聚合语句(sum,min,max,avg,count)要比having子句优先执行，简单的理解为只有有了统计结果后我才能执行筛选啊。
	where子句在查询过程中执行优先级别优先于聚合语句(sum,min,max,avg,count)，因为它是一句一句筛选的。
	HAVING子句可以让我们筛选成组后的对各组数据筛选，而WHERE子句在聚合前先筛选记录。现查询部门号不等于10的部门并且工资总和大于8000的部门编号。
	分析为通过where子句筛选出部门编号不为10的部门，然后在对部门工资进行统计，然后再使用having子句对统计结果进行筛选。
	select deptno,sum(sal) from emp where deptno!='10' group by deptno having sum(sal) > 8000;	
		
oracle函数
	
	nvl
	NVL(eExpression1, eExpression2)
	如果表达式1为非null，则返回表达式一的值，为null则返回表达式2的值
	在不支持 null 值或 null 值无关紧要的情况下，可以使用 NVL( ) 来移去计算或操作中的 null 值。
	
	decode
	DECODE()函数，它将输入数值与函数中的参数列表相比较，根据输入值返回一个对应值。
	函数的参数列表是由若干数值及其对应结果值组成的若干序偶形式。当然，如果未能与任何一个实参序偶匹配成功，则函数也有默认的返回值。
	比较表达式和搜索字，如果匹配，返回结果；如果不匹配，返回default值；如果未定义default值，则返回空值
	
	常用聚合函数
	聚合语句(sum,min,max,avg,count)
	
	分析函数
	分析函数用于计算基于组的某种聚合值，它和聚合函数的不同之处是
	对于每个组返回多行，而聚合函数对于每个组只返回一行。 
	
	
	
	