---
layout: llmm
title:  "Mark Up Language Unit 1"
date:   2018-01-30
excerpt: "Unit 1 XML and DTD"
image: "/images/icon1.svg"
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
