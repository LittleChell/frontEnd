#IE 兼容

#####	1.	[Date constructor returns NaN in IE, but works in Firefox and Chrome _date_ _stackoverflow_](https://stackoverflow.com/questions/2182246/date-constructor-returns-nan-in-ie-but-works-in-firefox-and-chrome)
IE中对日期的解析为NAN。

IE支持以下格式：<br>
new Date(Y,M-1,D,H,M,S);

#####	2.	兼容ie8 rgba()用法
	filter:progid:DXImageTransform.Microsoft.gradient(startColorstr=#19ffffff,endColorstr=#19ffffff);
	rgba透明值	IE filter值

<table style="width:100%;text-align: center;">
<tr style="width:100%;">
<td style="width: 50%;">
rgba透明值
</td>
<td>
IE filter值
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.1
</td>
<td>
19
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.2
</td>
<td>
33
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.3
</td>
<td>
4c
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.4
</td>
<td>
66
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.5
</td>
<td>
7f
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.6
</td>
<td>
99
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.7
</td>
<td>
b2
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.8
</td>
<td>
c8
</td>
</tr>
<tr style="width:100%;">
<td style="width: 50%;">
0.9
</td>
<td>
e5
</td>
</tr>
</table>




	