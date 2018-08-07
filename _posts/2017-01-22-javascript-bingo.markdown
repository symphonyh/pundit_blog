---
layout: post
title: Bingo
date: 2017-01-22
comments: true
external-url:
categories: Javascript
---

### Bingo source code

```html
<!DOCTYPE html>
<html>
<head>
	<title>Make Your Own Bingo Card</title>
	<link rel="stylesheet" href="script01.css">
	<script src="script11.js"></script>
	<meta name="viewport" content="height=800, width=560" />
</head>
<body>
<h1>Web 2.0 Bingo</h1>
<table>
	<tr>
		<th>B</th>
		<th>I</th>
		<th>N</th>
		<th>G</th>
		<th>O</th>
	</tr>
	<tr>
		<td id="square0">&nbsp;</td>
		<td id="square5">&nbsp;</td>
		<td id="square10">&nbsp;</td>
		<td id="square14">&nbsp;</td>
		<td id="square19">&nbsp;</td>
	</tr>
	<tr>
		<td id="square1">&nbsp;</td>
		<td id="square6">&nbsp;</td>
		<td id="square11">&nbsp;</td>
		<td id="square15">&nbsp;</td>
		<td id="square20">&nbsp;</td>
	</tr>
	<tr>
		<td id="square2">&nbsp;</td>
		<td id="square7">&nbsp;</td>
		<td id="free">Free</td>
		<td id="square16">&nbsp;</td>
		<td id="square21">&nbsp;</td>
	</tr>
	<tr>
		<td id="square3">&nbsp;</td>
		<td id="square8">&nbsp;</td>
		<td id="square12">&nbsp;</td>
		<td id="square17">&nbsp;</td>
		<td id="square22">&nbsp;</td>
	</tr>
	<tr>
		<td id="square4">&nbsp;</td>
		<td id="square9">&nbsp;</td>
		<td id="square13">&nbsp;</td>
		<td id="square18">&nbsp;</td>
		<td id="square23">&nbsp;</td>
	</tr>
</table>
<p><a href="script11.html" id="reload">Click here</a> to create a new card</p>
</body>
</html>

```
### JS 脚本

```javascript
var buzzwords = new Array ("Aggregate",	
	"Ajax",
	"API",
	"Bandwidth",
	"Beta",
	"Bleeding edge",
	"Convergence",
	"Design pattern",
	"Disruptive",
	"DRM",
	"Enterprise",
	"Facilitate",
	"Folksonomy",
	"Framework",
	"Impact",
	"Innovate",
	"Long tail",
	"Mashup",
	"Microformats",
	"Mobile",
	"Monetize",
	"Open social",
	"Paradigm",
	"Podcast",
	"Proactive",
	"Rails",
	"Scalable",
	"Social bookmarks",
	"Social graph",
	"Social software",
	"Spam",
	"Synergy",
	"Tagging",
	"Tipping point",
	"Truthiness",
	"User-generated",
	"Vlog",
	"Webinar",
	"Wiki",
	"Workflow"
);

var usedWords = new Array(buzzwords.length);
window.onload = initAll;

function initAll() {
	if (document.getElementById) {
		document.getElementById("reload").onclick = anotherCard;
		newCard();
	}
	else {
		alert("Sorry, your browser doesn't support this script");
	}
}

function newCard() {
	for (var i=0; i<24; i++) {
		setSquare(i);
	}
}

function setSquare(thisSquare) {
	do {
		var randomWord = Math.floor(Math.random() * buzzwords.length);
	}
	while (usedWords[randomWord]);

	usedWords[randomWord] = true;
	var currSquare = "square" + thisSquare;
	document.getElementById(currSquare).innerHTML = buzzwords[randomWord];
	document.getElementById(currSquare).className = "";
	document.getElementById(currSquare).onmousedown = toggleColor;
}

function anotherCard() {
	for (var i=0; i<buzzwords.length; i++) {
		usedWords[i] = false;
	}

	newCard();
	return false;
}

function toggleColor(evt) {
	if (evt) {
		var thisSquare = evt.target;
	}
	else {
		var thisSquare = window.event.srcElement;
	}
	if (thisSquare.className == "") {
		thisSquare.className = "pickedBG";
	}
	else {
		thisSquare.className = "";
	}
	checkWin();
}

function checkWin() {
	var winningOption = -1;
	var setSquares = 0;
	var winners = new Array(31,992,15360,507904,541729,557328,1083458,2162820,4329736,8519745,8659472,16252928);

	for (var i=0; i<24; i++) {
		var currSquare = "square" + i;
		if (document.getElementById(currSquare).className != "") {
			document.getElementById(currSquare).className = "pickedBG";
			setSquares = setSquares | Math.pow(2,i);
		}
	}

	for (var i=0; i<winners.length; i++) {
		if ((winners[i] & setSquares) == winners[i]) {
			winningOption = i;
		}
	}
	
	if (winningOption > -1) {
		for (var i=0; i<24; i++) {
			if (winners[winningOption] & Math.pow(2,i)) {
				currSquare = "square" + i;
				document.getElementById(currSquare).className = "winningBG";
			}
		}
	}
}
```
### CSS file

```css
body {
	background-color: white;
	color: black;
	font-size: 20px;
	font-family: "Lucida Grande", Verdana, Arial, Helvetica, sans-serif;
}

h1, th {
	font-family: Georgia, "Times New Roman", Times, serif;
}

h1 {
	font-size: 28px;
}

table {
	border-collapse: collapse;
}

th, td {
	padding: 10px;
	border: 2px #666 solid;
	text-align: center;
	width: 20%;
}

#free, .pickedBG {
	background-color: #f66;
}

.winningBG {
	background-image: url(images/redFlash.gif);
}
```