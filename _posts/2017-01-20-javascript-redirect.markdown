---
layout: post
title: 链接重定向的简单范例
date: 2017-01-20
comments: true
external-url:
categories: javascript
---


### redirect Sample code

```html
<!DOCTYPE html>
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
	<title>Welcome to our site</title>
	<script src="script08.js"></script>
</head>
<body>
  <h2>
	Hey, check out <a href="https://www.baidu.com/" id="redirect">baidu.com</a>.
  </h2>
</body>
</html>
```
### JS 脚本

```js
window.onload = initAll;

function initAll() {
  document.getElementById("redirect").onclick = initRedirect;
}

function initRedirect() {
  alert("We are not responsible for the content of pages outside our site");
  window.location = this;
  return false;
}
```