---
layout: post
title: "My TestNG Tips"
date: 2016-08-25
comments: true
categories:
---

<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
	<style type="text/css">
	#customers
		{
		font-family:"Trebuchet MS", Arial, Helvetica, sans-serif;
		width:100%;
		text-align:left;
		font-size:0.9em;
		line-height:1.5;
		}
	ul
		{
		list-style-type: disc;
		list-style-position: inside;		
		}
	</style>
</head>

<div class="css-full-post-content js-full-post-content" id="customers">
我的TestNG学习笔记：
<li><a href="http://testng.org/doc/documentation-main.html#annotations"> TestNG官网</a></li>

<ol>
<li>Hard dependencies</li>
	<ul>
	依赖的所有方法全部都成功执行后才会执行，如果有至少一个依赖失败，当前类或方法会被在报告中标记为<b>SKIP</b>。
	</ul>
	<ul>
	alwaysRun=false
	</ul>
	<ul>
	支持dependsOnMethods和dependsOnGroups：
	
	```java  
	
	@Test(dependsOnMethods = { "serverStartedOk" })
	public void method1() {}
	@Test(dependsOnGroups = { "init.*" })
	public void method2() {}
	
	```
	
	</ul>

<li>Soft dependencies</li>
	<ul>
	依赖的所有方法全部都成功执行后才会执行，如果有至少一个依赖失败，当前类或方法会被在报告中标记为SKIP。
	</ul>
	<ul>
	@Test(dependsOnMethods = { "serverStartedOk" })
	</ul>	
</ol>



</div>	