---
title: 简单实现vue双向绑定功能
toc: true
mathjax: true
comments: true
date: 2019-02-01 15:20:45
updated: 2019-02-01 15:20:45
photos:
tags: [vue,MVVM,双向绑定]
categories: 前端
---

# 简单实现vue双向绑定功能

```
<label>输入：</label>
<input type="text" id="demo1"><br/> 
<label>输出：</label> 
<input type="textarea" id="demo2"></input> 

<script> 
var a={}; 
var output=[]; 
Object.defineProperty(a,'b',{ 
//给a对象添加b属性 
set:function(val){ 
output['b']=val; 
}, 
get:function(){ 
return output['b']; 
} 
}) 
var demo1=document.querySelector('#demo1'); 
var demo2=document.querySelector('#demo2'); 
demo1.onkeyup=function(){ 
a.b=demo1.value;
//给a对象添加b属性时候，触发了a的set方法，此时#demo1的value值赋值给output['b']。 
demo2.value=output['b']; 
} 
</script>


```
