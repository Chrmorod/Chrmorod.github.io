---
layout: llmm
title:  "Mark Up Language Unit 1"
date:   2018-01-31
excerpt: "Unit 1 XML and DTD"
image: "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRv%0D%0AcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVy%0D%0Ac2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgdmVyc2lvbj0iMS4xIiBpZD0iTGF5ZXJfMSIg%0D%0AeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3%0D%0Ady53My5vcmcvMTk5OS94bGluayIgeD0iMHB4IiB5PSIwcHgiCgkgdmlld0JveD0iMCAwIDQ3My45%0D%0AMzEgNDczLjkzMSIgc3R5bGU9ImVuYWJsZS1iYWNrZ3JvdW5kOm5ldyAwIDAgNDczLjkzMSA0NzMu%0D%0AOTMxOyIgeG1sOnNwYWNlPSJwcmVzZXJ2ZSI+CjxjaXJjbGUgc3R5bGU9ImZpbGw6I0Q3REFCQTsi%0D%0AIGN4PSIyMzYuOTY2IiBjeT0iMjM2Ljk2NiIgcj0iMjM2Ljk2NiIvPgo8cGF0aCBzdHlsZT0iZmls%0D%0AbDojRUY4QTIxOyIgZD0iTTE0NC4zOTUsOTMuNzkxYy04LjgyMywwLTE1Ljk4MSw3LjE1NC0xNS45%0D%0AODEsMTUuOTgxdjI1NS43NTdjMCw4LjgyNyw3LjE1OCwxNS45ODEsMTUuOTgxLDE1Ljk4MQoJSDMy%0D%0AOC4yMmM4LjgyNywwLDE1Ljk4MS03LjE1NCwxNS45ODEtMTUuOTgxVjE2Ny44MTRsLTc3LjA0Ny03%0D%0ANC4wMjNIMTQ0LjM5NXoiLz4KPGc+Cgk8cGF0aCBzdHlsZT0iZmlsbDojRDU3OTI3OyIgZD0iTTM0%0D%0ANC4yMDUsMTY3LjgxNGgtNjEuMDY2Yy04LjgyNywwLTE1Ljk4MS03LjE1NC0xNS45ODEtMTUuOTgx%0D%0AVjkzLjc5MUwzNDQuMjA1LDE2Ny44MTR6Ii8+Cgk8cGF0aCBzdHlsZT0iZmlsbDojRDU3OTI3OyIg%0D%0AZD0iTTI2My45NjYsMjcxLjc3MmMwLDEwLjE4OS04LjI1OCwxOC40NDctMTguNDQzLDE4LjQ0N0gx%0D%0AMTAuODc2CgkJYy0xMC4xODksMC0xOC40NDMtOC4yNTgtMTguNDQzLTE4LjQ0N3YtNTYuMzUxYzAt%0D%0AMTAuMTg5LDguMjU0LTE4LjQ0MywxOC40NDMtMTguNDQzaDEzNC42NDdjMTAuMTg1LDAsMTguNDQz%0D%0ALDguMjU0LDE4LjQ0MywxOC40NDMKCQlWMjcxLjc3MnoiLz4KPC9nPgo8Zz4KCTxwYXRoIHN0eWxl%0D%0APSJmaWxsOiNGRkZGRkY7IiBkPSJNMTI2LjUwOSwyNTYuOThsOC4zODktMTIuMjUxbC03LjA2MS0x%0D%0AMC44OTZjLTAuNjY2LTEuMDU5LTEuMTY0LTEuOTY0LTEuNDk3LTIuNzI0CgkJYy0wLjMyOS0wLjc2%0D%0ALTAuNDk4LTEuNDg1LTAuNDk4LTIuMTg1YzAtMC43MTUsMC4zMjItMS4zNTgsMC45NTgtMS45MzFj%0D%0AMC42NDQtMC41NzIsMS40MjItMC44NTcsMi4zNDItMC44NTcKCQljMS4wNTUsMCwxLjg4MiwwLjMx%0D%0AMSwyLjQ2NiwwLjkzNWMwLjU5MSwwLjYyNSwxLjQwMywxLjc3NywyLjQ0MywzLjQ2NWw1LjYyOCw5%0D%0ALjEwN2w2LjAwOS05LjEwNwoJCWMwLjQ5NC0wLjc2NywwLjkxNy0xLjQyMiwxLjI2NS0xLjk2OGMw%0D%0ALjM1Mi0wLjU0NiwwLjY4OC0wLjk5OSwxLjAxNC0xLjM1NWMwLjMyNi0wLjM1NSwwLjY4OC0wLjYy%0D%0ANSwxLjA4NS0wLjgwNAoJCWMwLjQtMC4xOCwwLjg2NC0wLjI2OSwxLjM5Ni0wLjI2OWMwLjk1NCww%0D%0ALDEuNzM2LDAuMjg0LDIuMzM5LDAuODU3YzAuNjA2LDAuNTcyLDAuOTA5LDEuMjUsMC45MDksMi4w%0D%0AMzIKCQljMCwxLjE0MS0wLjY1OSwyLjY5NC0xLjk2OCw0LjY1NWwtNy4zOTQsMTEuMDQ5bDcuOTU1%0D%0ALDEyLjI1MWMwLjcxNSwxLjA3NCwxLjIzNSwxLjk2NCwxLjU2LDIuNjcyCgkJYzAuMzI2LDAuNzA3%0D%0ALDAuNDg2LDEuMzc3LDAuNDg2LDIuMDA5YzAsMC41OTktMC4xNDYsMS4xNDEtMC40MzQsMS42Mzlj%0D%0ALTAuMjg4LDAuNDk4LTAuNywwLjg4Ny0xLjIyNywxLjE3NQoJCWMtMC41MjgsMC4yODgtMS4xMjYs%0D%0AMC40MzQtMS43OTIsMC40MzRjLTAuNzE1LDAtMS4zMjUtMC4xNS0xLjgxNS0wLjQ0OXMtMC44OTQt%0D%0AMC42Ny0xLjIwMS0xLjExMQoJCWMtMC4zMDctMC40NDItMC44NzYtMS4zMDYtMS43MTQtMi41ODJs%0D%0ALTYuNi0xMC4zODNsLTcuMDA4LDEwLjY5Yy0wLjU0NiwwLjg1My0wLjkzNSwxLjQ0OC0xLjE2NCwx%0D%0ALjc5MgoJCWMtMC4yMzYsMC4zNDEtMC41MDksMC42NzQtMC44MzQsMC45OTlzLTAuNzA3LDAuNTgt%0D%0AMS4xNTIsMC43NjdjLTAuNDQ1LDAuMTg3LTAuOTY1LDAuMjgxLTEuNTYsMC4yODEKCQljLTAuOTIs%0D%0AMC0xLjY4NC0wLjI4MS0yLjI4Ni0wLjg0NmMtMC42MDYtMC41NjEtMC45MDktMS4zODEtMC45MDkt%0D%0AMi40NTVDMTI0LjY0MiwyNjAuMzQ4LDEyNS4yNjMsMjU4LjgwNiwxMjYuNTA5LDI1Ni45OHoiLz4K%0D%0ACTxwYXRoIHN0eWxlPSJmaWxsOiNGRkZGRkY7IiBkPSJNMTcyLjE5MiwyNTguNjE5bC02LjAwOS0y%0D%0AMy44OTF2MjUuODg1YzAsMS40MzMtMC4zMTgsMi41MDctMC45NjIsMy4yMjIKCQljLTAuNjM2LDAu%0D%0ANzE1LTEuNDg1LDEuMDc0LTIuNTQ0LDEuMDc0Yy0xLjAyMSwwLTEuODYtMC4zNTUtMi41MDctMS4w%0D%0ANjNjLTAuNjQ3LTAuNzA3LTAuOTczLTEuNzg5LTAuOTczLTMuMjM3di0yOS42NzIKCQljMC0xLjYz%0D%0AOSwwLjQyNy0yLjczOSwxLjI4LTMuMzExYzAuODUzLTAuNTcyLDIuMDAyLTAuODU3LDMuNDU0LTAu%0D%0AODU3aDIuMzU0YzEuNDE0LDAsMi40NDMsMC4xMjcsMy4wNzksMC4zODUKCQljMC42NDQsMC4yNTQs%0D%0AMS4xMTUsMC43MTUsMS40MjIsMS4zODFjMC4zMDcsMC42NjYsMC42NTksMS43NDcsMS4wNDgsMy4y%0D%0ANDhsNS40NDgsMjAuNTM5bDUuNDQ4LTIwLjUzOQoJCWMwLjM4OS0xLjUsMC43NDEtMi41ODIsMS4w%0D%0ANDgtMy4yNDhjMC4zMDctMC42NjYsMC43NzgtMS4xMjYsMS40MjItMS4zODFjMC42MzYtMC4yNTQs%0D%0AMS42NjUtMC4zODUsMy4wNzktMC4zODVoMi4zNTQKCQljMS40NTIsMCwyLjYwMSwwLjI4NCwzLjQ1%0D%0ANCwwLjg1N2MwLjg1MywwLjU3MiwxLjI4LDEuNjc2LDEuMjgsMy4zMTF2MjkuNjcyYzAsMS40MzMt%0D%0AMC4zMjIsMi41MDctMC45NTgsMy4yMjIKCQljLTAuNjQ0LDAuNzE1LTEuNDk3LDEuMDc0LTIuNTc0%0D%0ALDEuMDc0Yy0xLjAwNywwLTEuODMzLTAuMzU5LTIuNDgxLTEuMDc0Yy0wLjY0Ny0wLjcxNS0wLjk3%0D%0AMy0xLjc5Mi0wLjk3My0zLjIyMnYtMjUuODg2CgkJbC02LjAwOSwyMy44OTFjLTAuMzg5LDEuNTUz%0D%0ALTAuNzExLDIuNjktMC45NTgsMy40MTZzLTAuNzAzLDEuMzg0LTEuMzY5LDEuOTgzYy0wLjY2Niww%0D%0ALjU5OS0xLjU4NywwLjg5NC0yLjc2MSwwLjg5NAoJCWMtMC44ODcsMC0xLjYzOS0wLjE5MS0yLjI1%0D%0AMy0wLjU3NmMtMC42MTQtMC4zODUtMS4wOTMtMC44NzItMS40MzMtMS40NzFzLTAuNjEtMS4yNTct%0D%0AMC44MDgtMS45ODMKCQlDMTcyLjYsMjYwLjE1NywxNzIuMzk4LDI1OS40MDEsMTcyLjE5MiwyNTgu%0D%0ANjE5eiIvPgoJPHBhdGggc3R5bGU9ImZpbGw6I0ZGRkZGRjsiIGQ9Ik0yMTAuNjEyLDIzMC43MzZ2%0D%0AMjcuMjkyaDE1LjM5N2MxLjIyNywwLDIuMTcsMC4yOTksMi44MjksMC44OTQKCQljMC42NTUsMC41%0D%0AOTksMC45ODQsMS4zNDcsMC45ODQsMi4yNTNjMCwwLjkyLTAuMzI2LDEuNjY1LTAuOTczLDIuMjM4%0D%0AYy0wLjY0NywwLjU3Mi0xLjU5NCwwLjg1Ny0yLjg0LDAuODU3aC0xOC4zMzgKCQljLTEuNjU0LDAt%0D%0AMi44NDQtMC4zNjctMy41Ny0xLjFjLTAuNzIyLTAuNzMzLTEuMDg1LTEuOTItMS4wODUtMy41NTV2%0D%0ALTI4Ljg3OWMwLTEuNTM0LDAuMzQ4LTIuNjg3LDEuMDMzLTMuNDU0CgkJYzAuNjk2LTAuNzY3LDEu%0D%0ANjAxLTEuMTUyLDIuNzI4LTEuMTUyYzEuMTQ1LDAsMi4wNjksMC4zODIsMi43NzYsMS4xMzdDMjEw%0D%0ALjI1NywyMjguMDMsMjEwLjYxMiwyMjkuMTg3LDIxMC42MTIsMjMwLjczNnoiLz4KPC9nPgo8Zz4K%0D%0APC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9n%0D%0APgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8%0D%0AZz4KPC9nPgo8Zz4KPC9nPgo8L3N2Zz4K"
---

## UNIT 1 EXERCISE 1
### Student List
''' xml
<?xml version="1.0" encoding="UTF-8"?>
<lista_alumnado>
  <alumno>
    <nombre>Christian</nombre>
    <dni>56578567K</dni>
    <telefono>639185444</telefono>
    <edad>24</edad>
  </alumno>

  <alumno>
    <nombre>Mohammed</nombre>
    <dni>24782946Y</dni>
    <telefono>666666134</telefono>
    <edad>23</edad>
  </alumno>

  <alumno>
    <nombre>Francisco</nombre>
    <dni>23456345L</dni>
    <telefono>625438912</telefono>
    <edad>28</edad>
  </alumno>

  <alumno>
    <nombre>Vicent</nombre>
    <dni>25458110T</dni>
    <telefono>687659321</telefono>
    <edad>27</edad>
  </alumno>

  <alumno>
    <nombre>Nestor</nombre>
    <dni>45676100V</dni>
    <telefono>86574121R</telefono>
    <edad>30</edad>
  </alumno>

  <alumno>
    <nombre>Hector</nombre>
    <dni>23758001J</dni>
    <telefono>669756234</telefono>
    <edad>25</edad>
  </alumno>

  <alumno>
    <nombre>Joan</nombre>
    <dni>46789213Q</dni>
    <telefono>639182275</telefono>
    <edad>31</edad>
  </alumno>
</lista_alumnado>
'''

## UNIT 1 EXERCISE 2
### Student List with DTD Restrictions
''' xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE lista_alumnado
[
<!ELEMENT lista_alumnado (alumno*)>
<!ELEMENT alumno (nombre, dni, telefono, edad)>
<!ELEMENT nombre (#PCDATA)>
<!ELEMENT dni (#PCDATA)>
<!ELEMENT telefono (#PCDATA)>
<!ELEMENT edad (#PCDATA)>
]>

<lista_alumnado>
  <alumno>
    <nombre>Christian</nombre>
    <dni>51432214K</dni>
    <telefono>639184444</telefono>
    <edad>24</edad>
  </alumno>

  <alumno>
    <nombre>Mohammed</nombre>
    <dni>24782946Y</dni>
    <telefono>666666134</telefono>
    <edad>23</edad>
  </alumno>

  <alumno>
    <nombre>Francisco</nombre>
    <dni>23456345L</dni>
    <telefono>625438912</telefono>
    <edad>28</edad>
  </alumno>

  <alumno>
    <nombre>Vicent</nombre>
    <dni>25458110T</dni>
    <telefono>687659321</telefono>
    <edad>27</edad>
  </alumno>

  <alumno>
    <nombre>Nestor</nombre>
    <dni>45676100V</dni>
    <telefono>86574121R</telefono>
    <edad>30</edad>
  </alumno>

  <alumno>
    <nombre>Hector</nombre>
    <dni>23758001J</dni>
    <telefono>669756234</telefono>
    <edad>25</edad>
  </alumno>

  <alumno>
    <nombre>Joan</nombre>
    <dni>46789213Q</dni>
    <telefono>639182275</telefono>
    <edad>31</edad>
  </alumno>
</lista_alumnado>
'''

## UNIT 1 EXERCISE 3
### Order List with DTD Restrictions
''' xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE lista_pedidos
[
<!ELEMENT lista_pedidos (pedido*)>
<!ELEMENT pedido (cliente, importe, productos)>
<!ATTLIST pedido cod ID #IMPLIED>
<!ELEMENT cliente (#PCDATA)>
<!ELEMENT importe (#PCDATA)>
<!ELEMENT productos (producto*)>
<!ELEMENT producto (descripcion, cantidad)>
<!ATTLIST producto ref ID #IMPLIED>
<!ELEMENT descripcion (#PCDATA)>
<!ELEMENT cantidad (#PCDATA)>
]>
<lista_pedidos>
          <pedido cod="p001">
                 <cliente>Paco Pérez</cliente>
                 <importe>1200</importe>
                 <productos>
                  <producto ref="r001">
                  <descripcion>tuercas 2mm</descripcion>
                  <cantidad>20</cantidad>
                  </producto>
                  <producto ref="r003">
                  <descripcion>tornillo 2mm</descripcion>
                  <cantidad>10</cantidad>
                  </producto>
                 </productos>
          </pedido>
          <pedido cod="p002">
                 <cliente>Pepe Pérez</cliente>
                 <importe>100</importe>
                 <productos>
                  <producto ref="r004">
                  <descripcion>martillo</descripcion>
                  <cantidad>1</cantidad>
                  </producto>
                  <producto ref="r007">
                  <descripcion>maza</descripcion>
                  <cantidad>2</cantidad>
                  </producto>
                 </productos>
          </pedido>
</lista_pedidos>
'''

## UNIT 1 EXERCISE 4
### Subjects of  Multiplatform Applications Development Course with DTD Restrictions
''' xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE Lista_Asignaturas[
<!ELEMENT Lista_Asignaturas (Nombre_Asignatura*)>
<!ELEMENT Nombre_Asignatura (#PCDATA)>
<!ATTLIST Nombre_Asignatura cod ID #REQUIRED>
<!ATTLIST Nombre_Asignatura dep_1 IDREF #IMPLIED>
<!ATTLIST Nombre_Asignatura dep_2 IDREF #IMPLIED>
<!ATTLIST Nombre_Asignatura dep_3 IDREF #IMPLIED>
]>
<Lista_Asignaturas>
<Nombre_Asignatura cod="DAM1001500">Lenguaje de Marcas</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1002600">Entornos de Desarrollo</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1003700">Formación y Orientación Laboral</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1004800">Base de Datos</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1005900">Sistemas Informaticos</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1006001">Programación</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1007002">Ingles1º</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1008003" dep_1="DAM1001500">Acceso a datos</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1009004" dep_1="DAM1006001">Programación de servicios y procesos</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1010005" dep_1="DAM1003700">Sistemas de gestión empresarial</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1011006" dep_1="DAM1003700">Empresa e iniciativa emprendedora</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1012007" dep_1="DAM1006001" dep_2="DAM1009004">Proyecto de desarrollo de aplicaciones multiplataforma</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1013008" dep_1="DAM1003700" dep_2="DAM1010005" dep_3="DAM1011006">Formación en Centros de Trabajo</Nombre_Asignatura>
<Nombre_Asignatura cod="DAM1014009" dep_1="DAM1007002">Ingles Técnico2º</Nombre_Asignatura>
</Lista_Asignaturas>
'''
## UNIT 1 FINAL EXERCISE
### Hospital Patients List with DTD Restrictions
''' xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE pacientes[
<!ELEMENT pacientes (paciente*)>
<!ELEMENT paciente (nombre, apellido1, apellido2, dni, sexo, historial, fecha_nacimiento, direccion)>
<!ATTLIST paciente id ID #REQUIRED>
<!ELEMENT nombre (#PCDATA)>
<!ELEMENT apellido1 (#PCDATA)>
<!ELEMENT apellido2 (#PCDATA)>
<!ELEMENT dni (#PCDATA)>
<!ELEMENT sexo (#PCDATA)>
<!ELEMENT historial (n_historial, episodio*)>
<!ELEMENT n_historial (#PCDATA)>
<!ELEMENT episodio (antecedentes, farmacos*, analisis, seguimiento)>
<!ELEMENT antecedentes (#PCDATA)>
<!ELEMENT farmacos (#PCDATA)>
<!ATTLIST farmacos farm ID #IMPLIED>
<!ATTLIST farmacos dep IDREF #IMPLIED>
<!ELEMENT analisis (#PCDATA)>
<!ELEMENT seguimiento (#PCDATA)>
<!ELEMENT fecha_nacimiento (#PCDATA)>
<!ELEMENT direccion (calle, numero, puerta)>
<!ELEMENT calle (#PCDATA)>
<!ELEMENT numero (#PCDATA)>
<!ELEMENT puerta (#PCDATA)>
]>
<pacientes>
<paciente id="K53856420">
  <nombre>Antonio</nombre>
  <apellido1>Marco</apellido1>
  <apellido2>Perez</apellido2>
  <dni>53856420K</dni>
  <sexo>Varón</sexo>
  <historial>
  <n_historial>1888325</n_historial>
  <episodio>
  <antecedentes>El paciente presenta una dermatitis atopica G3, presenta la piel levemente seca, presenta alergias. Consume alcohol y fuma</antecedentes>
  <farmacos farm="A">Suniderma</farmacos>
  <farmacos farm="B" dep="A"> Corticoides 2.2</farmacos>
  <analisis> glucosa.... Bilirrubina.... Urea....</analisis>
  <seguimiento>Rosacea grado 2, acne hormonal 3 omnicomicosis</seguimiento>
  </episodio>
  </historial>
  <fecha_nacimiento>17/08/08</fecha_nacimiento>
  <direccion>
  <calle>Cabo Jubi</calle>
  <numero>4</numero>
  <puerta>11</puerta>
  </direccion>
</paciente>
<paciente id="V53438939">
  <nombre>José</nombre>
  <apellido1>Esparza</apellido1>
  <apellido2>Jumilla</apellido2>
  <dni>53438939V</dni>
  <sexo>Varón</sexo>
  <historial>
  <n_historial>1888225</n_historial>
  <episodio>
  <antecedentes>El paciente presenta una dermatitis seborreica, piel seca, no presenta alergias. fuma pero no bebe</antecedentes>
  <farmacos farm="C">gel de baño dermatologico</farmacos>
  <analisis> glucosa.... Bilirrubina.... Urea....</analisis>
  <seguimiento>Blanquezina grado 2, acne estable 1 omnicomicosis</seguimiento>
  </episodio>
  <episodio>
  <antecedentes>El paciente presenta una dermatitis atopica, levemente piel seca, no presenta alergias. fuma pero no bebe</antecedentes>
  <farmacos> Corticoides 2, gel de baño dermatologico, suniderma</farmacos>
  <analisis> glucosa.... Bilirrubina.... Urea....</analisis>
  <seguimiento>rosacea grado 2, acne inestable 1 omnicomicosis</seguimiento>
  </episodio>
  </historial>
  <fecha_nacimiento>05/12/92</fecha_nacimiento>
  <direccion>
  <calle>Lope de vega</calle>
  <numero>13</numero>
  <puerta>5</puerta>
  </direccion>
</paciente>
<paciente id="T25343225">
  <nombre>Francisco</nombre>
  <apellido1>Mendez</apellido1>
  <apellido2>Gutierrez</apellido2>
  <dni>25343225T</dni>
  <sexo>Varón</sexo>
  <historial>
  <n_historial>1888425</n_historial>
  <episodio>
  <antecedentes>El paciente presenta una vitigilio, presenta alergias, bebe</antecedentes>
  <farmacos farm="D" dep="B"> Corticoides 4</farmacos>
  <analisis> glucosa.... Bilirrubina.... Urea....</analisis>
  <seguimiento>rojiza grado 2, acne inestable, omnicomicosis 3</seguimiento>
  </episodio>
  </historial>
  <fecha_nacimiento>01/05/12</fecha_nacimiento>
  <direccion>
  <calle>Federico Maicas</calle>
  <numero>10</numero>
  <puerta>6</puerta>
  </direccion>
</paciente>
<paciente id="G22025421">
  <nombre>Marta</nombre>
  <apellido1>Mateo</apellido1>
  <apellido2>Fernandez</apellido2>
  <dni>22025421G</dni>
  <sexo>Mujer</sexo>
  <historial>
  <n_historial>1888125</n_historial>
  <episodio>
  <antecedentes>El paciente presenta una pitiriasis versicolor, presenta alergias, fuma</antecedentes>
  <farmacos farm="E" dep="A"> suniderma 2.2</farmacos>
  <analisis> glucosa.... Bilirrubina.... Urea....</analisis>
  <seguimiento>amarillenta grado 2, acne inestable, omnicomicosis 3</seguimiento>
  </episodio>
  </historial>
  <fecha_nacimiento>10/09/10</fecha_nacimiento>
  <direccion>
  <calle>Horta</calle>
  <numero>1</numero>
  <puerta>8</puerta>
  </direccion>
</paciente>
<paciente id="L35874544">
  <nombre>Silvia</nombre>
  <apellido1>Requena</apellido1>
  <apellido2>Sanchez</apellido2>
  <dni>35874544L</dni>
  <sexo>Varón</sexo>
  <historial>
  <n_historial>1888525</n_historial>
  <episodio>
  <antecedentes>El paciente presenta una dermatitis seborreica, presenta alergias, no fuma</antecedentes>
  <farmacos> Corticoides 2, gel de baño dermatologico</farmacos>
  <analisis> glucosa.... Bilirrubina.... Urea....</analisis>
  <seguimiento>Blanquezina grado 2, acne estable 1 omnicomicosis</seguimiento>
  </episodio>
  <episodio>
  <antecedentes>El paciente presenta una pitiriasis versicolor, presenta alergias, fuma</antecedentes>
  <farmacos> suniderma 2.2</farmacos>
  <analisis> glucosa.... Bilirrubina.... Urea....</analisis>
  <seguimiento>amarillenta grado 2, acne inestable, omnicomicosis 3</seguimiento>
  </episodio>
  </historial>
  <fecha_nacimiento>22/12/10</fecha_nacimiento>
  <direccion>
  <calle>San Valeriano</calle>
  <numero>7</numero>
  <puerta>3</puerta>
  </direccion>
</paciente>
</pacientes>
'''
