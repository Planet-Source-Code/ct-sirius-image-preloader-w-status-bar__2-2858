<div align="center">

## Image Preloader w/ Status Bar


</div>

### Description

This code acts as a splash page and preloads images that the main site would need to provide lower loading time. It has a status bar indicator of the percent and number of images that it loaded. It also has a loading bar and option to skip the loading process. Its great code and you need to check it out!
 
### More Info
 
None, there are clearly denoted sections of what the end user should edit and what they should not. Explaination of most variables are also included to allow for easy config.

Javascripts errors may happen, just adjust a variable to correct. It is one of the instructions.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[CT Sirius](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/ct-sirius.md)
**Level**          |Advanced
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |
**Category**       |[Graphics](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics__2-75.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/ct-sirius-image-preloader-w-status-bar__2-2858/archive/master.zip)





### Source Code

```
<html>
<head>
<meta name="GENERATOR" content="Microsoft FrontPage 5.0" />
<meta name="ProgId" content="FrontPage.Editor.Document" />
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252" />
<title>Preloading Images</title>
<script language="JavaScript1.2">
<!-- begin hiding
//Image Preloader Script By Ct_Sirius@Hotmail.com!
//
//Sys_Reactor@Neowin.net
//
//Copyright 2001
//
//Please do not remove this message.
//
//!Read Instructions If Confused, Else Leave at Default Value!
//
//#Begin No-Modify Section
BeginColor = new Array()
EndColor = new Array()
//#End No-Modify Section!
//#Begin Modify Settings Section!
//#The Images You Want To Preload!
//#Place Them In the Array by ("img name","img name",...)!
var yourImages = new Array("")
//#The target page that you to redirect to after the images successfully preload!
//#Default = index2.html
var PreloadTarget = "index2.html"
//#The length of the preload status bar! Note it MUST BE larger than the number of images loaded!
//#Default = 500
var preloadbarWidth = 500
//#The height of the preload status bar!
//#Default = 20
var preloadbarHeight = 20
//#Default Color of the Preload Status Bar!
//#Default = White (#FFFFFF)!
var backgroundOfGradient = "#ffffff"
//#Enter the first letter or number of each set of HEX color codes!
//#Example {35,16,24}, Then BeginColor[0]=3, BeginColor[1]=1, BeginColor[2]=2, Etc!
//#You will NOT notice a color difference!
//#Default = {BC,BF,C0}
BeginColor[0] = "B"
BeginColor[1] = "B"
BeginColor[2] = "C"
//#Enter the first letter or number of each set of HEX color codes!
//#Example {35,16,24}, Then EndColor[0]=3, EndColor[1]=1, EndColor[2]=2, Etc!
//#You will NOT notice a color difference!
//#Default = {BC,BF,C0}
EndColor[0] = "B"
EndColor[1] = "B"
EndColor[2] = "C"
//#If you get a javascript error, adjust this value, otherwise please do not modify!
//#Note that the MINUNUM VALUE is 2!
//#Default = 5!
var gap = 5
//#End Modify Settings Section!
//#Begin No-Modify Section!
if (!document.all) location.replace(PreloadTarget)
var a = 10, b = 11, c = 12, d = 13, e = 14, f=15, i, j, decimal = new Array(), hex = new Array(), diff = new Array();
var convert = new Array("0","1","2","3","4","5","6","7","8","9","a","b","c","d","e","f"), imgLen = yourImages.length;
var loaded = new Array(), preImages = new Array(), currCount = 0, pEndColor = 0, h = 0, hilite = new Array(), cover = new Array();
var num = Math.floor(preloadbarWidth/gap);
for (i = 0; i < 3; i++) {
	BeginColor[i] = BeginColor[i].toLowerCase();
	EndColor[i] = EndColor[i].toLowerCase();
	BeginColor[i] = eval(BeginColor[i]);
	EndColor[i] = eval(EndColor[i]);
	diff[i] = (EndColor[i]-BeginColor[i])/num;
	decimal[i] = Math.floor(diff[i]);
	hex[i] = Math.round((diff[i] - decimal[i])*15);
}
EndColor[0] = 0;
EndColor[1] = 2;
EndColor[2] = 1;
i = 0, j = 0;
while (i <= num) {
	hilite[i] = "#";
	while (j < 3) {
		hilite[i] += convert[BeginColor[j]];
		hilite[i] += convert[EndColor[j]];
		BeginColor[j] += decimal[j];
		EndColor[j] += hex[j];
		if (EndColor[j] > 15) {
			EndColor[j] -= 15;
			BeginColor[j]++;
		}
		j++;
	}
	j = 0;
	i++;
}
function loadImages() {
	for (i = 0; i < imgLen; i++) {
		preImages[i] = new Image();
		preImages[i].src = yourImages[i];
		loaded[i] = 0;
		cover[i] = Math.floor(num/imgLen)*(i+1)
	}
	cover[cover.length-1] += num%imgLen
	checkLoad();
}
function checkLoad() {
	if (pEndColor) { changeto(); return }
	if (currCount == imgLen) { location.replace(PreloadTarget); return }
	for (i = 0; i < imgLen; i++) {
		if (!loaded[i] && preImages[i].complete) {
			loaded[i] = 1; pEndColor++; currCount++;
			checkLoad();
			return;
		}
	}
	setTimeout("checkLoad()",10);
}
function changeto() {
	if (h+1 > cover[currCount-1]) {
		var percent = Math.round(100/imgLen)*currCount;
		if (percent > 100) while (percent != 100) percent--;
		if (currCount == imgLen && percent < 100) percent = 100;
		defaultStatus = "Loaded " + currCount + " out of " + imgLen + " Images [" + percent + "%].";
		pEndColor--;
		checkLoad();
		return;
	}
	eval("document.all.cell" + (h+1) + ".style.backgroundColor = hilite[h]");;
	h++;
	setTimeout("changeto()",1);
}
defaultStatus = "Loaded 0 out of " + imgLen + " images [0%]."
// end hiding -->
</script>
</head>
<body>
<div align="center">
 <center>
 <p>&#160;</p>
 </center>
 <p>&#160;</p>
 <p>&#160;</p>
 <p>&#160;</p>
 <table width="75%" border="0" cellspacing="0" cellpadding="0" height="200" style="border-collapse: collapse" bordercolor="#111111">
  <tbody>
  <tr>
   <td height="159">
   <p align="center">&#160;</p>
   <p align="center">&#160;</p>
   <p align="center">
   <font face="Arial" style="font-size: 7pt" color="#FF0000">Preloading Images</font></p>
   <div align="center">
    <font face="Verdana, Arial, Helvetica, sans-serif" size="2" color="#CCCCCC">
    <script language="JavaScript1.2">
<!-- beging hiding
document.write('<table border="1" cellpadding="0" cellspacing="0" width="' + preloadbarWidth + '"><tr height="' + preloadbarHeight + '" bgcolor="' + backgroundOfGradient + '">');
for (i = 0; i < num; i++) {
	document.write('<td width="' + gap + '" id="cell' + (i+1) + '"></td>');
}
document.write('</tr></table>');
document.write('<p><small><a href="javascript:location.replace(PreloadTarget)">Skip Loading (Not Recommended)</a></small></p></font>')
loadImages();
// end hiding -->
     </script>
    </font>
   </div>
   </td>
  </tr>
 </tbody>
 </table>
 <p>&#160;</p>
</div>
<p align="center"><b><font face="Arial" size="6" color="#FF0000">Loading...</font></b></p>
<p align="center"><b><font face="Arial" size="6" color="#FF0000">Please Wait...</font></b></p>
</body>
</html>
```

