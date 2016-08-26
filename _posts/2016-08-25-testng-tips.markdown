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
	不管依赖的方法是否都成功执行，始终会执行当前类或方法。
	</ul>
	<ul>
	alwaysRun=true

<li>Dependencies in XML</li>
	<ul>
	注：Groups中一共包括define/run/dependencies三个子菜单，亲身体验是define和dependencies放在一起的时候，dependencies不生效，也就是两个最好不要同时用。而且define或dependencies最好和run一起使用，参照下例:
	</ul>
	<ul>
	alwaysRun=true
	</ul>
	<ul>
	<pre class="brush: xml">
	  &lt;test name="My suite"&gt;
	&lt;!DOCTYPE suite SYSTEM "http://testng.org/testng-1.0.dtd" &gt;
	&lt;suite name="testNgSuite" &gt;
		&lt;test name="Test dependencies" &gt;
			&lt;groups&gt;
				&lt;run&gt;
					&lt;include name="group7" /&gt;
				&lt;/run&gt;
				&lt;dependencies&gt;
					&lt;group name="group5" depends-on="group2 group4" /&gt;
					&lt;group name="group7" depends-on="group5 group6" /&gt;
				&lt;/dependencies&gt;
			&lt;/groups&gt;
			
			&lt;classes&gt;
				&lt;class name="testng.groups.MyTestB"&gt;
				&lt;/class&gt;
			&lt;/classes&gt;
		&lt;/test&gt;
	&lt;/suite&gt;
	</pre>
	</ul>
</ol>
</div>	