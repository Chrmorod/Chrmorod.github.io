---
layout: post
title:  "Mark Up Language Unit 3"
date:   2018-02-02
excerpt: "Unit 2 XML and XSL"
image: "/images/xml3.png"
---

## UNIT 3 EXERCISE 1
### My first XSL - Stylize CDs XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet version="1.0" type= "text/xsl" href="ej1_xsl.xsl"?>
<cds>
	<cd>
		<titulo>babilonia</titulo>
		<interprete>revolver</interprete>
		<anyo>2015</anyo>
		<estilo>pop-rock</estilo>
		<precio>23</precio>
	</cd>
	<cd>
		<titulo>Comes</titulo>
		<interprete>The Liberty</interprete>
		<anyo>2015</anyo>
		<estilo>pop</estilo>
		<precio>13.00</precio>
	</cd>
	<cd>
		<titulo>Wallflower</titulo>
		<interprete>Diana Krall</interprete>
		<anyo>2014</anyo>
		<estilo>pop</estilo>
		<precio>12.00</precio>
	</cd>
</cds>
```
### My first XSL - XSL associated to CDs XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
<xsl:template match="/">
<html>
	<body>
		<h1>CD's</h1>
			<table>
				<tr bgcolor="#887788">
					<th>Título</th>
					<th>Intérprete</th>
				</tr>
				<xsl:for-each select="cds/cd">
				<tr>
					<td bgcolor="#cec6ce"><xsl:value-of select="titulo"/></td>
					<td bgcolor="#cec6ce"><xsl:value-of select="interprete"/></td>
				</tr>
				</xsl:for-each>
			</table>
	</body>
</html>
</xsl:template>
</xsl:stylesheet>
```
## UNIT 3 EXERCISE 2
### Continuity of exercise 1 - CDTECA XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet version="1.0" type= "text/xsl" href="ej1_xsl.xsl"?>
<cds>
	<cd>
		<titulo>babilonia</titulo>
		<interprete>revolver</interprete>
		<anyo>2015</anyo>
		<estilo>pop-rock</estilo>
		<precio>23</precio>
		<duracion>20:00</duracion>
	</cd>
	<cd>
		<titulo>Comes</titulo>
		<interprete>The Liberty</interprete>
		<anyo>2015</anyo>
		<estilo>pop</estilo>
		<precio>13.00</precio>
		<duracion>36:00</duracion>
	</cd>
	<cd>
		<titulo>Wallflower</titulo>
		<interprete>Diana Krall</interprete>
		<anyo>2014</anyo>
		<estilo>pop</estilo>
		<precio>12.00</precio>
		<duracion>40:00</duracion>
	</cd>
		<cd>
		<titulo>50 palos</titulo>
		<interprete>Jarabe de Palo</interprete>
		<anyo>2017</anyo>
		<estilo>pop</estilo>
		<precio>7.30</precio>
		<duracion>37:00</duracion>
	</cd>
		<cd>
		<titulo>Blues Parade</titulo>
		<interprete>Mojo Blues Band</interprete>
		<anyo>2000</anyo>
		<estilo>blues</estilo>
		<precio>5.00</precio>
		<duracion>50:00</duracion>
	</cd>
  <cd>
		<titulo>Chuck</titulo>
		<interprete>Sum41</interprete>
		<anyo>2004</anyo>
		<estilo>rock</estilo>
		<precio>6.00</precio>
		<duracion>39:00</duracion>
	</cd>
	  <cd>
		<titulo>Highly Evolved</titulo>
		<interprete>The Vines</interprete>
		<anyo>2002</anyo>
		<estilo>rock</estilo>
		<precio>15.00</precio>
		<duracion>30:00</duracion>
	</cd>
</cds>
```
### Continuity of exercise 1 - CDTECA XSL
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
<xsl:template match="/">
<html>
	<body>
		<h1>CDTECA</h1>
			<table>
				<tr bgcolor="#887788">
				  <th>Estilo Musical</th>
					<th>Título</th>
					<th>Intérprete</th>
					<th>Duración (min)</th>
					<th>Precio €</th>
				</tr>
				<xsl:for-each select="cds/cd">
				<tr>
				  <td bgcolor="#d67584"><xsl:value-of select="estilo"/></td>
					<td bgcolor="#cec6ce"><xsl:value-of select="titulo"/></td>
					<td bgcolor="#cec6ce"><xsl:value-of select="interprete"/></td>
					<td bgcolor="#aec2c4"><xsl:value-of select="duracion"/></td>
					<td bgcolor="#ede5c4"><xsl:value-of select="precio"/></td>
				</tr>
				</xsl:for-each>
			</table>
	</body>
</html>
</xsl:template>
</xsl:stylesheet>
```
