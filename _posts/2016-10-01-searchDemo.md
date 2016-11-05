---
title: 搜索框
date: 2016-10-01 11:40:39
tags: [search,搜索]
categories: [搜索,search]
permalink: searchDemo
---
<h2 id="intro">前言</h2>最近要写个网站解析，需要个搜索框，同时要可以选择分类的，故搜索学习了下相关内容，[Demo](http://api.sunkejava.com/Demo/searchDemo.html)如下 ,使用css+js实现。
---
![demoimage][1]
[1]: http://ww1.sinaimg.cn/large/a24d4f55jw1f9h1r6hrtwj21gl04omxn.jpg

<!-- more -->
### html页面	

 搜索Demo html页面实现:    

	<html>
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>
		<title>taobao search demo</title>
		<script src="js/jquery-1.10.2.min.js"></script>
	</head>
	<body >
		<div class = "search-container">
			<div id = "search_tab" class = "search-list">
				<ul>
					<li id="tab_1" class = "">
						<a href="#">YY神曲</a>
					</li>
					<li id="tab_2" class = "selected">
						<a href="#">51AVI</a>
					</li>
					<li id="tab_3" class = "">
						<a href="#">音悦台</a>
					</li>
					<li id="tab_4" class = "">
						<a href="#">个人YY</a>
					</li>
				</ul>
			</div>
			<div class = "search-pannel">
					<div class = "search-tips">
						<a href = "#">
							全能<br/>解析
						</a>
					</div>
					<div class = "search-button">
						<button class = "btn-search" onclick = "parse()">搜索
						</button>
					</div>
					<div class = "search-common-pannel" >
					<input id="inputv" type = "text" x-webkit-speech="">
					<i id = "inputi" class = "iconfont" >&#xe63f;</i>
					</div>
			</div>
		</div>
		
		<div>
		</div>
	</body>
	</html>
  
﻿
### js代码
  
		<script>
		function parse(){
				
			}
			var getDOM = function(id){
				return document.getElementById(id);
			}
			var addEvent = function(id,event,fn){
				var el = getDOM(id)||document;
				if(el.addEventListener){
					el.addEventListener(event,fn,false);
				}else if(el.attachEvent){
					el.attachEvent('on'+event,fn);
				}
			}
			addEvent('inputv','focus',function(){
				if(this.value == ""){
					getDOM('inputi').display ='';
				}else{
					getDOM('inputi').display = 'none';
				}
			});
			addEvent('search_tab','mouseover',function(){
				if(this.className.indexOf('trigger-hover') < 0){
				this.className+= ' trigger-hover';
				}
			});
			
			addEvent('search_tab','mouseout',function(){
				if(this.className.indexOf('trigger-hover') > 0){
				this.className = 'search-list';
				}
			});
	
			addEvent('tab_1','click',function(){
				getDOM('search_tab').className='search-list';
				getDOM('tab_2').className='';
				getDOM('tab_3').className='';
				getDOM('tab_4').className='';
				if(this.className.indexOf('selected') < 0){
				this.className +='selected';
				}
			});
			
			addEvent('tab_2','click',function(){
				getDOM('search_tab').className='search-list';
				getDOM('tab_1').className='';
				getDOM('tab_3').className='';
				getDOM('tab_4').className='';
				if(this.className.indexOf('selected')< 0){
				this.className ='selected';
				}
				
			});
			
			addEvent('tab_3','click',function(){
				getDOM('search_tab').className='search-list';
				getDOM('tab_1').className='';
				getDOM('tab_2').className='';
				getDOM('tab_4').className='';
				if(this.className.indexOf('selected')< 0){
				this.className ='selected';
				}
			});
			
			addEvent('tab_4','click',function(){
				getDOM('search_tab').className='search-list';
				getDOM('tab_1').className='';
				getDOM('tab_2').className='';
				getDOM('tab_3').className='';
				if(this.className.indexOf('selected')< 0){
				this.className ='selected';
				}
			});
		</script>

### css代码

	<style type= "text/css">
				@font-face {
					  font-family: 'iconfont';
					  src: url('http://at.alicdn.com/t/font_1472286029_235907.eot'); /* IE9*/
					  src: url('http://at.alicdn.com/t/font_1472286029_235907.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
					  url('http://at.alicdn.com/t/font_1472286029_235907.woff') format('woff'), /* chrome、firefox */
					  url('http://at.alicdn.com/t/font_1472286029_235907.ttf') format('truetype'), /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/
					  url('http://at.alicdn.com/t/font_1472286029_235907.svg#iconfont') format('svg'); /* iOS 4.1- */
					}
				body{font:12px/1.5 tahoma,arial,sans-serif;}
				a{
					text-decoration:none;
				}
				.search-container{
					position:relative;
				}
				.search-tips{
					float:right;
					padding:3px 0 0 6px;
				}
				.search-tips a {
					color: #6c6c6c;
				}
				.search-button{
					float:right;
					
				}
				.btn-search{
					background:rgba(255, 175, 255, 0.4);
					width:100px;
					height:45px;
					border:0 none;
					cursor:pointer;
					font-size:25px;
				}
				.btn-search:hover{
					background:rgba(255, 50, 255, 0.4);
					width:100px;
					height:45px;
					border:0 none;
					cursor:pointer;
				}
				.search-common-pannel{
					height:39px;
					background-color: rgba(255, 175, 255, 0.4);
					overflow: hidden;
					padding:3px 0 3px 77px;
				}
				.search-common-pannel input{
					height:39px;
					line-height:39px;
					width:100%;
					border:0 none;
					outline: 0;
					background:rgba(255, 255, 255, 0.4);
				}
				.search-common-pannel i {
					position:absolute;
					top:14px;
					left:86px;
					z-index:2;
				}
				.iconfont {
						font-family: iconfont;
						font-size: 12px;
						font-style: normal;
						color:#ccc;
					}
				ul{
					list-style:none;
					display:block;
				}
				ul,li{
					padding:0;
					margin:0;
				}
				.search-list{
					position:absolute;
					top:3px;
					left:3px;
					width:72px;
					height:39px;
					overflow:hidden;
					background:rgba(255, 255, 125, 0.4);
					border-left:1px solid #f6f6f6;
					border-right:1px solid #e5e5e5;
				}
				.search-list li{
					display:none;
					height: 39px;
					line-height: 39px;
					overflow: hidden;
					text-align:center;
				}
				.search-list li a{
					color:#6c6c6c;
				}
				.search-list .selected{
					background:rgba(255, 255, 85, 0.4);
					display:block;
				}
				.trigger-hover{
					display:block;
					height: auto;
				}
				.out-hover{
					height: 39px;
				}
				.trigger-hover li {
					display: block;
				}
			</style>  
> 有什么留言或问题直接在文末留下评论即可。

### 欢迎访客:

<ul class="ds-recent-visitors" data-num-items="39" data-avatar-size="56"></ul>


