---
layout: post
title:  "It Systems"
date:   2018-04-08
excerpt: "Unit 6.2 Shell Scripts"
image: "/images/scrip2.png"
---

## UNIT 6 EXERCISE 2
### First Script - Create a subdirectories number for different directories of people.
```python
#!/bin/bash
clear
dir=$1
maxlin=`cat nombres.txt | wc -l`
linea=1
while [ $linea -lt $maxlin ]; do
   user=`cat nombres.txt | head -${linea} | tail -1`
   mkdir $user
   cd $user
   for i in `seq 1 $dir`; do
       mkdir personal$i
   done
   cd ../
   linea=`expr $linea + 1`
done
```
### Second Script - Average of rainfall from file
```python
#!/bin/bash
clear
linea=1
prom=0
precip=`cat precipitaciones.txt | wc -l`
while [ $linea -le $precip ]; do
    preplin=`cat precipitaciones.txt | head -${linea} | tail -1 | awk '{print $2}'`
    prom=`expr $prom + $preplin`
    linea=`expr $linea + 1`
done
media=$(echo "scale=2; $prom / $precip"|bc)
echo "La media de las $precip precipitaciones es $media"
```
### Third Script - Indicate rainy days from file
```python
#!/bin/bash
clear
linea=1
precip=`cat precipitaciones.txt | wc -l`
while [ $linea -le $precip ]; do
    preplin=`cat precipitaciones.txt | head -${linea} | tail -1 | awk '{print $2}'`
    dialin=`cat precipitaciones.txt | head -${linea} | tail -1 | awk '{print $1}'`
    if [ $preplin -eq 0 ]; then
	for i in `seq 1 7 30`; do
	 if [ $dialin -eq $i ]; then
	     echo "El Lunes dia $dialin no llovió."
	 fi
	done
	for i in `seq 2 7 30`; do
	 if [ $dialin -eq $i ]; then
	     echo "El Martes dia $dialin no llovió."
	 fi
	done
	for i in `seq 3 7 30`; do
	 if [ $dialin -eq $i ]; then
	     echo "El Miercoles dia $dialin no llovió."
	 fi
	done
	for i in `seq 4 7 30`; do
	 if [ $dialin -eq $i ]; then
	     echo "El Jueves dia $dialin no llovió."
	 fi
	done
	for i in `seq 5 7 30`; do
	 if [ $dialin -eq $i ]; then
	     echo "El Viernes dia $dialin no llovió."
	 fi
	done
	for i in `seq 6 7 30`; do
	 if [ $dialin -eq $i ]; then
	     echo "El Sabado dia $dialin no llovió."
	 fi
	done
	for i in `seq 7 7 30`; do
	 if [ $dialin -eq $i ]; then
	     echo "EL Domingo dia $dialin no llovió."
	 fi
	done
    fi
linea=`expr $linea + 1`
done
```
### Fourth Script - print odd numbers and even numbers from file
```python
#!/bin/bash
clear
linea=1
maxlin=`cat numeros.txt | wc -l`
while [ $linea -le $maxlin ]; do
	num=`cat numeros.txt | head -${linea} | tail -1`
	if [ `expr $num % 2` -eq 0 ]; then
	echo "$num" >> par.txt
	else
	echo "$num" >> impar.txt
	fi
	linea=`expr $linea + 1`
done
echo "-------Numeros Pares-------"
cat par.txt
echo "-------Numeros Impares-----"
cat impar.txt
```
### Fifth Script - Count Windows or Linux Computers and their process
```python
#!/bin/bash
clear
linea=1; countLinux=0; countWindows=0; countproLi=0; countproWi=0;
list=`cat listado.txt | wc -l`
while [ $linea -le $list ]; do
    si=`cat listado.txt | head -${linea} | tail -1 | awk '{print $2}'`
    proces=`cat listado.txt | head -${linea} | tail -1 | awk '{print $3}'`
    if [ "$si" = "Linux" ]; then
	countLinux=`expr $countLinux + 1`
	countproLi=`expr $countproLi + $proces`
    else
	countWindows=`expr $countWindows + 1`
	countproWi=`expr $countproWi + $proces`
    fi
linea=`expr $linea + 1`
done
echo "Linux --> users: $countLinux proc: $countproLi"
echo "Windows --> users: $countWindows proc: $countproWi"
```
### Sixth Script - Remove files with extension .txt
```python
#!/bin/bash
clear
dir=$1
cd $dir
linea=1
list=`ls | grep ".txt$" | wc -l`
while [ $linea -le $list ]; do
    borfil=`ls | grep ".txt$" | head -${linea} | tail -1 `
    rm $borfil
    linea=`expr $linea + 1`
done
echo "Se han borrado `expr $linea - 1` ficheros de extension .txt"
```
### Seventh Script - Improving the script for remove files with extension .txt
```python
#!/bin/bash
clear
dir=$1
if [ -d "$dir" ]; then
cd $dir
linea=1
list=`ls | grep ".txt$" | wc -l`
while [ $linea -le $list ]; do
    borfil=`ls | grep ".txt$" | head -${linea} | tail -1 `
    rm $borfil
    linea=`expr $linea + 1`
done
echo "Se han borrado `expr $linea - 1` ficheros de extension .txt"
else
echo "EL directorio no existe"
fi
```
### Eighth Script - Scan the ips started by 192.168.1.XXX
```python
#!/bin/bash
clear
for i in `seq 1 254`; do
    data=`ping -c 1 192.168.1.$i | grep "^1" | awk '{print $4}'`
    if [ $data = 1 ]; then
	echo "la dirección IP 192.168.1.$i existe"
    else
	echo "la dirección IP 192.168.1.$i no existe"
    fi
done
```