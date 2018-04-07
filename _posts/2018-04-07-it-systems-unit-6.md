---
layout: post
title:  "It Systems"
date:   2018-04-07
excerpt: "Unit 6 Shell Scripts"
image: "/images/scrip.png"
---

## UNIT 6 EXERCISE 1
### My first Shell Script - More o less number
```python
#!/bin/bash
clear
read -p "Introduce un valor: " valor1
read -p "Introduce un segundo valor: " valor2
if [ $valor1 -gt $valor2 ]; then
    echo "$valor1 es mayor que $valor2"
elif [ $valor1 -lt $valor2 ]; then
    echo "$valor1 es menor que $valor2"
else
    echo "$valor1 es igual que $valor2"
fi
```
### Second Script - Odd or even number
```python
#!/bin/bash
clear
read -p "Introduzca un valor que no sea menor que 0: " num1
while [ $num1 -lt 0 ]; do
read -p "Valor no permitido, introduzca otro valor: " num1
done
res=`expr $num1 % 2`
if [ $res -eq 0 ]; then
    echo "El numero $num1 es un numero par"
else
    echo "El numero $num1 es un numero impar"
fi
```
### Third Script - Califications
```python
#!/bin/bash
clear
read -p "Introduzca un valor de nota: " nota1
while [ $nota1 -lt 0 ] || [ $nota1 -gt 10 ]; do
read -p "Valor incorrecto, por favor introduzca un valor de nota correcto: " nota1
done
if [ $nota1 -lt 5 ]; then
    echo "La nota introducida es $nota1 es un suspenso"
elif [ $nota1 -ge 5 ] && [ $nota1 -lt 7 ]; then
    echo "La nota introducida es $nota1 es un aprobado"
elif [ $nota1 -ge 7 ] && [ $nota1 -lt 9 ]; then
    echo "La nota introducida es $nota1 es un notable"
else
    echo "La nota introducida es $nota1 es un sobresaliente"
fi
```
### Fourth Script - Count from 0 to the input number
```python
#!/bin/bash
clear
read -p "Introduce un valor mayor que 0: " val1
while [ $val1 -le 0 ]; do
    read -p "Valor incorrecto, por favor introduzca otro valor: " val1
done
for i in `seq 0 $val1`; do
    echo "$i"
done
```
### Fifth Script - Add
```python
#!/bin/bash
clear
sum=0
cont=0
read -p "Introduzca un valor para añadir a la suma: " num1
while [ $num1 -ne 0 ]; do
    sum=`expr $sum + $num1`
    cont=`expr $cont + 1`
    read -p "Introduzca un valor para añadir a la suma: " num1
done
echo "El valor de la suma es $sum"
med=`expr $sum / $cont`
echo "El valor de la suma es $med"
```
### Sixth Script - Price for consume liters
```python
#!/bin/bash
clear
cant=0
resol=0
read -p "Introduzca la cantidad de litros de agua consumidos: " lit
while [ $lit -le 0 ]; do
    read -p "Cantidad incorrecta, introduzca de nuevo la cantidad de litros de agua consumidos: " lit
done
if [ $lit -le 50 ]; then
    resol=$(echo "$resol+20.00"|bc)
    echo "20.00 €---- cuota primeros 50 litros"
    echo "____________\n"
    echo "$resol €-----Total a pagar"
elif [ $lit -le 200 ]; then
    res=`expr $lit - 50`
    cal=$(echo "$res*0.20"|bc)
    echo "20.00 €---- cuota primeros 50 litros"
    echo "$cal €---- cuota 0.20/l hasta 200 litros"
    resol=$(echo "$cal+20"|bc)
    echo "____________\n"
    echo "$resol €-----Total a pagar"
else
    res=`expr $lit - 50`
    if [ $res -le 200 ]; then
	cal=$(echo "scale=2; $res*0.20"|bc)
	echo "20.00 €---- cuota primeros 50 litros"
	echo "$cal €---- cuota 0.20/l hasta 200 litros"
	resol=$(echo "$cal+20"|bc)
	echo "____________\n"
	echo "$resol €-----Total a pagar"
    else
	echo "20.00 €---- cuota primeros 50 litros"
	res=`expr $res - 200`
	cal=$(echo "200*0.20"|bc)
	echo "$cal €---- cuota 0.20/l hasta 200 litros"
	cal2=$(echo "$res*0.10"|bc)
	echo "$cal2 €---- cuota 0.10/l por encima de 200 litros (restantes)"
	resol2=$(echo "$cal + $cal2"|bc)
	resol=$(echo "$resol2+20"|bc)
	echo "____________\n"
	echo "$resol €-----Total a pagar"
    fi
fi
```
### Seventh Script - Simple meter of days
```python
#!/bin/bash
clear
read -p "Por favor, introduzca un día numerico del mes: " dia
while [ $dia -le 0 ] || [ $dia -gt 30 ]; do
    read -p "Valor incorrecto, introduzca de nuevo un dia numerico del mes" dia
done
for i in `seq 1 7 30`; do
	 if [ $dia -eq $i ]; then
	     echo "El $dia es Lunes de este mes."
	 fi
done
for i in `seq 2 7 30`; do
	 if [ $dia -eq $i ]; then
	     echo "El $dia es Martes de este mes."
	 fi
done
for i in `seq 3 7 30`; do
	 if [ $dia -eq $i ]; then
	     echo "El $dia es Miercoles es de este mes."
	 fi
done
for i in `seq 4 7 30`; do
	 if [ $dia -eq $i ]; then
	     echo "El $dia es Jueves es de este mes."
	 fi
done
for i in `seq 5 7 30`; do
	 if [ $dia -eq $i ]; then
	     echo "El $dia es Viernes es de este mes."
	 fi
done
for i in `seq 6 7 30`; do
	 if [ $dia -eq $i ]; then
	     echo "El $dia es Sabado es de este mes."
	 fi
done
for i in `seq 7 7 30`; do
	 if [ $dia -eq $i ]; then
	     echo "El $dia es Domingo es de este mes."
	 fi
done
```