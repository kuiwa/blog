---
layout: post
title: "My TestNG Tips"
date: 2016-08-25
comments: true
categories:
---

<head>
	<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
	
	 <link rel="stylesheet" href="testng.css" type="text/css" />
        <link type="text/css" rel="stylesheet" href="http://beust.com/beust.css"  />
        <script type="text/javascript" src="banner.js"></script>

      <script type="text/javascript" src="http://beust.com/scripts/shCore.js"></script>
      <script type="text/javascript" src="http://beust.com/scripts/shBrushJava.js"></script>
      <script type="text/javascript" src="http://beust.com/scripts/shBrushXml.js"></script>
      <script type="text/javascript" src="http://beust.com/scripts/shBrushBash.js"></script>
      <script type="text/javascript" src="http://beust.com/scripts/shBrushPlain.js"></script>
      <link type="text/css" rel="stylesheet" href="http://beust.com/styles/shCore.css"/>
      <link type="text/css" rel="stylesheet" href="http://beust.com/styles/shThemeCedric.css"/>
      <script type="text/javascript">
        SyntaxHighlighter.config.clipboardSwf = 'scripts/clipboard.swf';
        SyntaxHighlighter.defaults['gutter'] = false;
        SyntaxHighlighter.all();
      </script>
      <script type="text/javascript" src="http://beust.com/toc.js"></script>
	  
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
	支持dependsOnMethods和dependsOnGroups, 如下例：
	
	<pre class="brush: java">
	@Test
	public void serverStartedOk() {}

	@Test(dependsOnMethods = { "serverStartedOk" })
	public void method1() {}
	</pre>
	
	</ul>
<li>Soft dependencies</li>
	<ul>
	依赖的所有方法全部都成功执行后才会执行，如果有至少一个依赖失败，当前类或方法会被在报告中标记为SKIP。
	</ul>
	<ul>
	@Test(dependsOnMethods = { "serverStartedOk" })
	</ul>	
</pre>
</ol>
</div>	