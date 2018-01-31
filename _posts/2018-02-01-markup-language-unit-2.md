---
layout: post
title:  "Mark Up Language Unit 2"
date:   2018-02-01
excerpt: "Unit 2 XML, DTD and XSD"
image: "/images/xml2.png"
---

## UNIT 2 EXERCISE 1
### XML Copy Editor Application
```xml
<?xml version="1.0" encoding="UTF-8"?>
<lista_programas xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="ej1.xsd">
<programa>XML Copy Editor</programa>
</lista_programas>
```
### XSD Copy Editor Application
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <xsd:element name="lista_programas">
      <xsd:complexType>
          <xsd:sequence>
            <xsd:element name="programa" type="xsd:string"/>
          </xsd:sequence>
      </xsd:complexType>
  </xsd:element>
</xsd:schema>
```

## UNIT 2 EXERCISE 2
### Diary XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
    <agenda xmlns:xsd="http://www.w3.org/2001/XMLSchema-instance" xsd:noNamespaceSchemaLocation="tarea2.xsd">
      <persona nacimiento="1999-10-20">
	      <datos>
			    <nombre>Pepe</nombre>
			    <apellidos>Garcia</apellidos>
			    <dni>25390952</dni>
	      </datos>
	      <comentario>buena gente...</comentario>
      </persona>
      <persona nacimiento="1980-11-25">
	      <datos>
			    <nombre>Juani</nombre>
			    <apellidos>Pérez</apellidos>
			    <dni>25364578</dni>
	      </datos>
	      <comentario>amigo de Pepe...</comentario>
      </persona>
    </agenda>
```
### Diary XSD
```xml
<?xml version="1.0" encoding="UTF-8"?>
  <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <xsd:element name="agenda">
          <xsd:complexType>
                <xsd:sequence>
                  <xsd:element name="persona" maxOccurs="unbounded">
                      <xsd:complexType>
                        <xsd:sequence>
                          <xsd:element name="datos" >
                            <xsd:complexType>
                              <xsd:sequence>
                                <xsd:element name="nombre" type="xsd:string"/>
                                <xsd:element name="apellidos" type="xsd:string"/>
                                <xsd:element name="dni" type="xsd:integer"/>
                              </xsd:sequence>
                            </xsd:complexType>
                          </xsd:element>
                          <xsd:element name="comentario">
                            <xsd:simpleType>
                              <xsd:restriction base="xsd:string">
                                <xsd:whiteSpace value="preserve"/>
                              </xsd:restriction>
                            </xsd:simpleType>
                          </xsd:element>
                        </xsd:sequence>
                        <xsd:attribute name="nacimiento" type="xsd:string"/>
                      </xsd:complexType>
                  </xsd:element>
                </xsd:sequence>
          </xsd:complexType>
      </xsd:element>
  </xsd:schema>
```

## UNIT 2 EXERCISE 3
### Vehicles XML
```xml
<?xml version="1.0" encoding="utf-8"?>
<vehiculos xmlns:xsd="http://www.w3.org/2001/XMLSchema-instance" xsd:noNamespaceSchemaLocation="auto.xsd">
 <vehiculo>
  <nickname>Count Zero</nickname>
  <modelo>Series I, 80"</modelo>
  <construccion>
   <comienzo>
    <dia>21</dia>
    <mes>July</mes>
    <año>1949</año>
   </comienzo>
   <fin>
    <dia>9</dia>
    <mes>August</mes>
    <año>1949</año>
   </fin>
  </construccion>
  <modelos>
   <model>Change Engine</model>
   <model>Change pedals</model>
   <model>Change gearbox</model>
   <model>Fit Rollcage</model>
  </modelos>
 </vehiculo>
</vehiculos>
```
### Vehicles XSD
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <!---Definición de los elementos simples-->
  <!--nombre nickname y modelo-->
    <xsd:simpleType name="nombreType">
      <xsd:restriction base="xsd:string">
        <xsd:maxLength value="32"/>
      </xsd:restriction>
    </xsd:simpleType>
  <!---dia-->
    <xsd:simpleType name="diaType">
      <xsd:restriction base="xsd:integer">
        <xsd:minInclusive value="1"/>
        <xsd:maxInclusive value="31"/>
      </xsd:restriction>
    </xsd:simpleType>
  <!---mes-->
    <xsd:simpleType name="mesType">
      <xsd:restriction base="xsd:string">
        <xsd:maxLength value="10"/>
      </xsd:restriction>
    </xsd:simpleType>
  <!---año-->
    <xsd:simpleType name="añoType">
      <xsd:restriction base="xsd:integer">
        <xsd:minInclusive value="1900"/>
        <xsd:maxInclusive value="2017"/>
      </xsd:restriction>
    </xsd:simpleType>
    <!---****************************************************************-->
  <!---Definición de los elementos complejos-->
  <!---Comienzo-->
    <xsd:complexType name="comienzoType">
      <xsd:sequence>
        <xsd:element name="dia" type="diaType"/>
        <xsd:element name="mes" type="mesType"/>
        <xsd:element name="año" type="añoType"/>
      </xsd:sequence>
    </xsd:complexType>
  <!---Fin-->
    <xsd:complexType name="finType">
      <xsd:sequence>
        <xsd:element name="dia" type="diaType"/>
        <xsd:element name="mes" type="mesType"/>
        <xsd:element name="año" type="añoType"/>
      </xsd:sequence>
    </xsd:complexType>
  <!---Construccion-->
    <xsd:complexType name="construccionType">
      <xsd:sequence>
        <xsd:element name="comienzo" type="comienzoType"/>
        <xsd:element name="fin" type="finType"/>
      </xsd:sequence>
    </xsd:complexType>
  <!--Modelos-->
   <xsd:complexType name="modelosType">
      <xsd:sequence>
        <xsd:element name="model" type="xsd:string" maxOccurs="unbounded"/>
      </xsd:sequence>
    </xsd:complexType>
<!---Vehiculo-->
    <xsd:complexType name="vehiculoType">
      <xsd:sequence>
        <xsd:element name="nickname" type="nombreType"/>
        <xsd:element name="modelo" type="nombreType"/>
       <xsd:element name="construccion" type="construccionType"/>
       <xsd:element name="modelos" type="modelosType"/>
      </xsd:sequence>
    </xsd:complexType>
  <!---VEHICULOS-->
    <xsd:complexType name="vehiculosType">
      <xsd:sequence>
       <xsd:element name="vehiculo" type="vehiculoType" maxOccurs="unbounded"/>
      </xsd:sequence>
    </xsd:complexType>
    <xsd:element name="vehiculos" type="vehiculosType"/>
</xsd:schema>
```
## UNIT 2 EXERCISE FINAL
### Clinics XML + DTD Restrictions
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE clinicas[
<!ELEMENT clinicas (clinica*)>
<!ATTLIST clinicas id ID #REQUIRED>
<!ELEMENT clinica (nombre, contacto, direccion, pacientes, empleados)>
<!ATTLIST clinica id ID #IMPLIED>
<!ATTLIST clinica central IDREF #REQUIRED>
<!ELEMENT nombre (#PCDATA)>
<!ELEMENT contacto (telefono, email)>
<!ELEMENT telefono (#PCDATA)>
<!ELEMENT email (#PCDATA)>
<!ELEMENT direccion (calle, numero, puerta, cpostal)>
<!ELEMENT calle (#PCDATA)>
<!ELEMENT numero (#PCDATA)>
<!ELEMENT puerta (#PCDATA)>
<!ELEMENT cpostal (#PCDATA)>
<!ELEMENT pacientes (paciente*)>
<!ATTLIST paciente nump ID #REQUIRED>
<!ELEMENT paciente (historial, datos)>
<!ELEMENT historial (tratamientos*)>
<!ATTLIST historial num ID #REQUIRED>
<!ELEMENT tratamientos (#PCDATA)>
<!ELEMENT datos (nif_paciente, nombre_paciente, apellidos_paciente, direccion_paciente, edad_paciente, contacto_paciente)>
<!ELEMENT nif_paciente (#PCDATA)>
<!ELEMENT nombre_paciente (#PCDATA)>
<!ELEMENT apellidos_paciente (#PCDATA)>
<!ELEMENT direccion_paciente (calle_paciente, numero_paciente, puerta_paciente, cpostal_paciente)>
<!ELEMENT calle_paciente (#PCDATA)>
<!ELEMENT numero_paciente (#PCDATA)>
<!ELEMENT puerta_paciente (#PCDATA)>
<!ELEMENT cpostal_paciente (#PCDATA)>
<!ELEMENT edad_paciente (#PCDATA)>
<!ELEMENT contacto_paciente (telefono_paciente, email_paciente)>
<!ELEMENT telefono_paciente (#PCDATA)>
<!ELEMENT email_paciente (#PCDATA)>
<!ELEMENT empleados (empleado*)>
<!ELEMENT empleado (nombre_empleado, apellidos_empleado, nif_empleado, edad_empleado, contacto_empleado, direccion_empleado, puesto_empleado)>
<!ATTLIST empleado nume ID #REQUIRED>
<!ELEMENT nombre_empleado (#PCDATA)>
<!ELEMENT apellidos_empleado (#PCDATA)>
<!ELEMENT nif_empleado (#PCDATA)>
<!ELEMENT edad_empleado (#PCDATA)>
<!ELEMENT contacto_empleado (telefono_empleado, email_empleado)>
<!ELEMENT telefono_empleado (#PCDATA)>
<!ELEMENT email_empleado (#PCDATA)>
<!ELEMENT direccion_empleado (calle_empleado, numero_empleado, puerta_empleado, cpostal_empleado)>
<!ELEMENT calle_empleado (#PCDATA)>
<!ELEMENT numero_empleado (#PCDATA)>
<!ELEMENT puerta_empleado (#PCDATA)>
<!ELEMENT cpostal_empleado (#PCDATA)>
<!ELEMENT puesto_empleado (#PCDATA)>
]>

<clinicas id="aigaalma8888">
     <!--clinica 01-->
   <clinica id="CA001" central="aigaalma8888">
     <nombre>Clínica Aitana</nombre>
     <contacto>
        <telefono>968342521</telefono>
        <email>caita@aitanaclinic.com</email>
     </contacto>
      <direccion>
        <calle>Horta</calle>
        <numero>4</numero>
        <puerta>7</puerta>
        <cpostal>46900</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="V12385202">
         <historial num="V123852020010">
          <tratamientos>Operación maxilodental</tratamientos>
         </historial>
         <datos>
           <nif_paciente>54230021Y</nif_paciente>
           <nombre_paciente>Sofia</nombre_paciente>
           <apellidos_paciente>Martin Almas</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Jesus</calle_paciente>
              <numero_paciente>2</numero_paciente>
              <puerta_paciente>1</puerta_paciente>
              <cpostal_paciente>21500</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>34</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>621110412</telefono_paciente>
              <email_paciente>sofi@jotas.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="R54525452">
         <historial num="R545254520018">
          <tratamientos>Caries</tratamientos>
          <tratamientos>Extraccion muela r3</tratamientos>
         </historial>
         <datos>
           <nif_paciente>54525452R</nif_paciente>
           <nombre_paciente>Mateo</nombre_paciente>
           <apellidos_paciente>Mas Colomer</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Turis</calle_paciente>
              <numero_paciente>25</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>22411</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>18</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>632222480</telefono_paciente>
              <email_paciente>mateo.colomermateo@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
        <empleado nume="K25318450001">
          <nombre_empleado>Fernando</nombre_empleado>
          <apellidos_empleado>Mondejar Castilla</apellidos_empleado>
          <nif_empleado>25318450K</nif_empleado>
          <edad_empleado>35</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>639582142</telefono_empleado>
            <email_empleado>fermoncas@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Rene Luce</calle_empleado>
            <numero_empleado>10</numero_empleado>
            <puerta_empleado>8</puerta_empleado>
            <cpostal_empleado>46091</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Asesor</puesto_empleado>
       </empleado>
        <empleado nume="Q22523041001">
          <nombre_empleado>Antonio</nombre_empleado>
          <apellidos_empleado>Monedero Martinez</apellidos_empleado>
          <nif_empleado>22523041Q</nif_empleado>
          <edad_empleado>30</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>545821412</telefono_empleado>
            <email_empleado>antmonmar@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Lorca</calle_empleado>
            <numero_empleado>7</numero_empleado>
            <puerta_empleado>2</puerta_empleado>
            <cpostal_empleado>22500</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Odontologo</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
     <!--clinica 02-->
    <clinica id="CG002" central="aigaalma8888">
      <nombre>Clínica Garbi</nombre>
      <contacto>
        <telefono>968220287</telefono>
        <email>cgarbi@hotmail.com</email>
      </contacto>
      <direccion>
        <calle>Mar</calle>
        <numero>34</numero>
        <puerta>10</puerta>
        <cpostal>46901</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="L14588770">
         <historial num="L1458877000074">
          <tratamientos>Operación cadera</tratamientos>
         </historial>
         <datos>
           <nif_paciente>14588770L</nif_paciente>
           <nombre_paciente>Tomas</nombre_paciente>
           <apellidos_paciente>Rubio Casals</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente> Garcia Marquez</calle_paciente>
              <numero_paciente>14</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>22564</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>20</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>620200412</telefono_paciente>
              <email_paciente>tomascasa@hotmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="J53822145">
         <historial num="J538221450078">
          <tratamientos>Luxacion de hombro</tratamientos>
          <tratamientos>Ataque de Ansiedad</tratamientos>
         </historial>
         <datos>
           <nif_paciente>53822145J</nif_paciente>
           <nombre_paciente>Raquel</nombre_paciente>
           <apellidos_paciente>Esteve Castell</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Mont</calle_paciente>
              <numero_paciente>20</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>46900</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>28</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>635685480</telefono_paciente>
              <email_paciente>raquel.ec@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
       <empleado nume="P25333822002">
          <nombre_empleado>Clara</nombre_empleado>
          <apellidos_empleado>Sanz Montiano</apellidos_empleado>
          <nif_empleado>25333822P</nif_empleado>
          <edad_empleado>40</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>774514212</telefono_empleado>
            <email_empleado>clarsanz@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Ludovico</calle_empleado>
            <numero_empleado>15</numero_empleado>
            <puerta_empleado>7</puerta_empleado>
            <cpostal_empleado>52200</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Traumatologa</puesto_empleado>
       </empleado>
        <empleado nume="R45212320002">
          <nombre_empleado>Carlos</nombre_empleado>
          <apellidos_empleado>Castello Marcos</apellidos_empleado>
          <nif_empleado>45212320R</nif_empleado>
          <edad_empleado>35</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>774513332</telefono_empleado>
            <email_empleado>carcasmar@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Lima</calle_empleado>
            <numero_empleado>2</numero_empleado>
            <puerta_empleado>3</puerta_empleado>
            <cpostal_empleado>46001</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Enfermero</puesto_empleado>
       </empleado>
        <empleado nume="S52452357">
          <nombre_empleado>Ana</nombre_empleado>
          <apellidos_empleado>Merino Cacorla</apellidos_empleado>
          <nif_empleado>52452357S</nif_empleado>
          <edad_empleado>24</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654513212</telefono_empleado>
            <email_empleado>anmerca@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Teruel</calle_empleado>
            <numero_empleado>30</numero_empleado>
            <puerta_empleado>5</puerta_empleado>
            <cpostal_empleado>45100</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Administrativa</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
   <!--clinica 03-->
   <clinica id="CA003" central="aigaalma8888">
      <nombre>Clínica Almerich</nombre>
      <contacto>
        <telefono>963354484</telefono>
        <email>calmerich@almerich.com</email>
      </contacto>
      <direccion>
        <calle>Puerta</calle>
        <numero>3</numero>
        <puerta>8</puerta>
        <cpostal>46522</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="S11542690">
         <historial num="S115426900024">
          <tratamientos>Operación molares</tratamientos>
          <tratamientos>Funda dental</tratamientos>
         </historial>
         <datos>
           <nif_paciente>11542690S</nif_paciente>
           <nombre_paciente>Maria</nombre_paciente>
           <apellidos_paciente>Reus Vall</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente> Llanterners</calle_paciente>
              <numero_paciente>1</numero_paciente>
              <puerta_paciente>21</puerta_paciente>
              <cpostal_paciente>46220</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>18</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>621041287</telefono_paciente>
              <email_paciente>Mreus@hotmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="G54201553">
         <historial num="G54201553001">
          <tratamientos>Caries</tratamientos>
          <tratamientos>Limpieza dental</tratamientos>
         </historial>
         <datos>
           <nif_paciente>54201553G</nif_paciente>
           <nombre_paciente>Roman</nombre_paciente>
           <apellidos_paciente>Valero Miralles</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Waxman</calle_paciente>
              <numero_paciente>25</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>46900</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>29</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>632285370</telefono_paciente>
              <email_paciente>rvalmir@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
       <empleado nume="H53851223003">
          <nombre_empleado>Elisa</nombre_empleado>
          <apellidos_empleado>Rus Boira</apellidos_empleado>
          <nif_empleado>53851223H</nif_empleado>
          <edad_empleado>36</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>633222112</telefono_empleado>
            <email_empleado>elirubo@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Tirant lo Blanc</calle_empleado>
            <numero_empleado>10</numero_empleado>
            <puerta_empleado>8</puerta_empleado>
            <cpostal_empleado>46900</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Odontologa</puesto_empleado>
       </empleado>
        <empleado nume="H45651260003">
          <nombre_empleado>Jordi</nombre_empleado>
          <apellidos_empleado>Clerigues Mont</apellidos_empleado>
          <nif_empleado>45651260R</nif_empleado>
          <edad_empleado>38</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>677753212</telefono_empleado>
            <email_empleado>jorclemont@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Chile</calle_empleado>
            <numero_empleado>1</numero_empleado>
            <puerta_empleado>3</puerta_empleado>
            <cpostal_empleado>46901</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Enfermero</puesto_empleado>
       </empleado>
        <empleado nume="S87545210003">
          <nombre_empleado>Amparo</nombre_empleado>
          <apellidos_empleado>Boirent Fernandez</apellidos_empleado>
          <nif_empleado>87545210S</nif_empleado>
          <edad_empleado>28</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654522212</telefono_empleado>
            <email_empleado>ambofer@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Toledo</calle_empleado>
            <numero_empleado>3</numero_empleado>
            <puerta_empleado>3</puerta_empleado>
            <cpostal_empleado>45220</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Administrativa</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
   <!--clinica04-->
   <clinica id="CM004" central="aigaalma8888">
      <nombre>Clínica Malluna</nombre>
      <contacto>
        <telefono>961110287</telefono>
        <email>cmallu@malluna.com</email>
      </contacto>
      <direccion>
        <calle>Reak</calle>
        <numero>3</numero>
        <puerta>20</puerta>
        <cpostal>46902</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="D45251247">
         <historial num="D452512470025">
          <tratamientos>Operación rotula</tratamientos>
          <tratamientos>Esguince pie izquierdo</tratamientos>
         </historial>
         <datos>
           <nif_paciente>45251247D</nif_paciente>
           <nombre_paciente>Teresa</nombre_paciente>
           <apellidos_paciente>Casals Sanz</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Damasco</calle_paciente>
              <numero_paciente>11</numero_paciente>
              <puerta_paciente>5</puerta_paciente>
              <cpostal_paciente>45880</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>29</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>620200111</telefono_paciente>
              <email_paciente>teresa_tesa@hotmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="E14521457">
         <historial num="E145214570018">
          <tratamientos>Rotura de radio</tratamientos>
          <tratamientos>Luxación de hombro</tratamientos>
         </historial>
         <datos>
           <nif_paciente>14521457E</nif_paciente>
           <nombre_paciente>Marina</nombre_paciente>
           <apellidos_paciente>Garcia Lenzo</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Rio</calle_paciente>
              <numero_paciente>8</numero_paciente>
              <puerta_paciente>8</puerta_paciente>
              <cpostal_paciente>46900</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>20</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>635681122</telefono_paciente>
              <email_paciente>MarMarina.GL@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
       <empleado nume="R75894889004">
          <nombre_empleado>Carla</nombre_empleado>
          <apellidos_empleado>Pardo Muñoz</apellidos_empleado>
          <nif_empleado>75894889R</nif_empleado>
          <edad_empleado>38</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654453212</telefono_empleado>
            <email_empleado>carparmu@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Castaño</calle_empleado>
            <numero_empleado>18</numero_empleado>
            <puerta_empleado>6</puerta_empleado>
            <cpostal_empleado>46902</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Traumatologa</puesto_empleado>
       </empleado>
        <empleado nume="R54225521004">
          <nombre_empleado>Marc</nombre_empleado>
          <apellidos_empleado>Miravet Sanz</apellidos_empleado>
          <nif_empleado>54225521R</nif_empleado>
          <edad_empleado>35</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654512565</telefono_empleado>
            <email_empleado>marmirsanz@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Donatelo</calle_empleado>
            <numero_empleado>1</numero_empleado>
            <puerta_empleado>2</puerta_empleado>
            <cpostal_empleado>45822</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Asesor</puesto_empleado>
       </empleado>
        <empleado nume="T58954585">
          <nombre_empleado>Clara</nombre_empleado>
          <apellidos_empleado>Ros Cacorla</apellidos_empleado>
          <nif_empleado>58954585T</nif_empleado>
          <edad_empleado>34</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654457212</telefono_empleado>
            <email_empleado>clarrosca@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Albana</calle_empleado>
            <numero_empleado>10</numero_empleado>
            <puerta_empleado>10</puerta_empleado>
            <cpostal_empleado>46901</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Enfermera</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
  </clinicas>
```
### Clinics XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
<clinicas id="aigaalma8888" xmlns:xsd="http://www.w3.org/2001/XMLSchema-instance" xsd:noNamespaceSchemaLocation="clinicas.xsd">
     <!--clinica 01-->
   <clinica id="CA001" central="aigaalma8888">
     <nombre>Clínica Aitana</nombre>
     <contacto>
        <telefono>968342521</telefono>
        <email>caita@aitanaclinic.com</email>
     </contacto>
      <direccion>
        <calle>Horta</calle>
        <numero>4</numero>
        <puerta>7</puerta>
        <cpostal>46900</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="V12385202">
         <historial num="V123852020010">
          <tratamientos>Operación maxilodental</tratamientos>
         </historial>
         <datos>
           <nif_paciente>54230021Y</nif_paciente>
           <nombre_paciente>Sofia</nombre_paciente>
           <apellidos_paciente>Martin Almas</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Jesus</calle_paciente>
              <numero_paciente>2</numero_paciente>
              <puerta_paciente>1</puerta_paciente>
              <cpostal_paciente>21500</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>34</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>621110412</telefono_paciente>
              <email_paciente>sofi@jotas.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="R54525452">
         <historial num="R545254520018">
          <tratamientos>Caries</tratamientos>
          <tratamientos>Extraccion muela r3</tratamientos>
         </historial>
         <datos>
           <nif_paciente>54525452R</nif_paciente>
           <nombre_paciente>Mateo</nombre_paciente>
           <apellidos_paciente>Mas Colomer</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Turis</calle_paciente>
              <numero_paciente>25</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>22411</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>18</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>632222480</telefono_paciente>
              <email_paciente>mateo.colomermateo@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
        <empleado nume="K25318450001">
          <nombre_empleado>Fernando</nombre_empleado>
          <apellidos_empleado>Mondejar Castilla</apellidos_empleado>
          <nif_empleado>25318450K</nif_empleado>
          <edad_empleado>35</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>639582142</telefono_empleado>
            <email_empleado>fermoncas@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Rene Luce</calle_empleado>
            <numero_empleado>10</numero_empleado>
            <puerta_empleado>8</puerta_empleado>
            <cpostal_empleado>46091</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Asesor</puesto_empleado>
       </empleado>
        <empleado nume="Q22523041001">
          <nombre_empleado>Antonio</nombre_empleado>
          <apellidos_empleado>Monedero Martinez</apellidos_empleado>
          <nif_empleado>22523041Q</nif_empleado>
          <edad_empleado>30</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>545821412</telefono_empleado>
            <email_empleado>antmonmar@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Lorca</calle_empleado>
            <numero_empleado>7</numero_empleado>
            <puerta_empleado>2</puerta_empleado>
            <cpostal_empleado>22500</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Odontologo</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
     <!--clinica 02-->
    <clinica id="CG002" central="aigaalma8888">
      <nombre>Clínica Garbi</nombre>
      <contacto>
        <telefono>968220287</telefono>
        <email>cgarbi@hotmail.com</email>
      </contacto>
      <direccion>
        <calle>Mar</calle>
        <numero>34</numero>
        <puerta>10</puerta>
        <cpostal>46901</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="L14588770">
         <historial num="L1458877000074">
          <tratamientos>Operación cadera</tratamientos>
         </historial>
         <datos>
           <nif_paciente>14588770L</nif_paciente>
           <nombre_paciente>Tomas</nombre_paciente>
           <apellidos_paciente>Rubio Casals</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente> Garcia Marquez</calle_paciente>
              <numero_paciente>14</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>22564</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>20</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>620200412</telefono_paciente>
              <email_paciente>tomascasa@hotmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="J53822145">
         <historial num="J538221450078">
          <tratamientos>Luxacion de hombro</tratamientos>
          <tratamientos>Ataque de Ansiedad</tratamientos>
         </historial>
         <datos>
           <nif_paciente>53822145J</nif_paciente>
           <nombre_paciente>Raquel</nombre_paciente>
           <apellidos_paciente>Esteve Castell</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Mont</calle_paciente>
              <numero_paciente>20</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>46900</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>28</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>635685480</telefono_paciente>
              <email_paciente>raquel.ec@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
       <empleado nume="P25333822002">
          <nombre_empleado>Clara</nombre_empleado>
          <apellidos_empleado>Sanz Montiano</apellidos_empleado>
          <nif_empleado>25333822P</nif_empleado>
          <edad_empleado>40</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>774514212</telefono_empleado>
            <email_empleado>clarsanz@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Ludovico</calle_empleado>
            <numero_empleado>15</numero_empleado>
            <puerta_empleado>7</puerta_empleado>
            <cpostal_empleado>52200</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Traumatologa</puesto_empleado>
       </empleado>
        <empleado nume="R45212320002">
          <nombre_empleado>Carlos</nombre_empleado>
          <apellidos_empleado>Castello Marcos</apellidos_empleado>
          <nif_empleado>45212320R</nif_empleado>
          <edad_empleado>35</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>774513332</telefono_empleado>
            <email_empleado>carcasmar@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Lima</calle_empleado>
            <numero_empleado>2</numero_empleado>
            <puerta_empleado>3</puerta_empleado>
            <cpostal_empleado>46001</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Enfermero</puesto_empleado>
       </empleado>
        <empleado nume="S52452357">
          <nombre_empleado>Ana</nombre_empleado>
          <apellidos_empleado>Merino Cacorla</apellidos_empleado>
          <nif_empleado>52452357S</nif_empleado>
          <edad_empleado>24</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654513212</telefono_empleado>
            <email_empleado>anmerca@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Teruel</calle_empleado>
            <numero_empleado>30</numero_empleado>
            <puerta_empleado>5</puerta_empleado>
            <cpostal_empleado>45100</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Administrativa</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
   <!--clinica 03-->
   <clinica id="CA003" central="aigaalma8888">
      <nombre>Clínica Almerich</nombre>
      <contacto>
        <telefono>963354484</telefono>
        <email>calmerich@almerich.com</email>
      </contacto>
      <direccion>
        <calle>Puerta</calle>
        <numero>3</numero>
        <puerta>8</puerta>
        <cpostal>46522</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="S11542690">
         <historial num="S115426900024">
          <tratamientos>Operación molares</tratamientos>
          <tratamientos>Funda dental</tratamientos>
         </historial>
         <datos>
           <nif_paciente>11542690S</nif_paciente>
           <nombre_paciente>Maria</nombre_paciente>
           <apellidos_paciente>Reus Vall</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente> Llanterners</calle_paciente>
              <numero_paciente>1</numero_paciente>
              <puerta_paciente>21</puerta_paciente>
              <cpostal_paciente>46220</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>18</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>621041287</telefono_paciente>
              <email_paciente>Mreus@hotmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="G54201553">
         <historial num="G54201553001">
          <tratamientos>Caries</tratamientos>
          <tratamientos>Limpieza dental</tratamientos>
         </historial>
         <datos>
           <nif_paciente>54201553G</nif_paciente>
           <nombre_paciente>Roman</nombre_paciente>
           <apellidos_paciente>Valero Miralles</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Waxman</calle_paciente>
              <numero_paciente>25</numero_paciente>
              <puerta_paciente>2</puerta_paciente>
              <cpostal_paciente>46900</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>29</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>632285370</telefono_paciente>
              <email_paciente>rvalmir@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
       <empleado nume="H53851223003">
          <nombre_empleado>Elisa</nombre_empleado>
          <apellidos_empleado>Rus Boira</apellidos_empleado>
          <nif_empleado>53851223H</nif_empleado>
          <edad_empleado>36</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>633222112</telefono_empleado>
            <email_empleado>elirubo@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Tirant lo Blanc</calle_empleado>
            <numero_empleado>10</numero_empleado>
            <puerta_empleado>8</puerta_empleado>
            <cpostal_empleado>46900</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Odontologa</puesto_empleado>
       </empleado>
        <empleado nume="H45651260003">
          <nombre_empleado>Jordi</nombre_empleado>
          <apellidos_empleado>Clerigues Mont</apellidos_empleado>
          <nif_empleado>45651260R</nif_empleado>
          <edad_empleado>38</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>677753212</telefono_empleado>
            <email_empleado>jorclemont@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Chile</calle_empleado>
            <numero_empleado>1</numero_empleado>
            <puerta_empleado>3</puerta_empleado>
            <cpostal_empleado>46901</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Enfermero</puesto_empleado>
       </empleado>
        <empleado nume="S87545210003">
          <nombre_empleado>Amparo</nombre_empleado>
          <apellidos_empleado>Boirent Fernandez</apellidos_empleado>
          <nif_empleado>87545210S</nif_empleado>
          <edad_empleado>28</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654522212</telefono_empleado>
            <email_empleado>ambofer@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Toledo</calle_empleado>
            <numero_empleado>3</numero_empleado>
            <puerta_empleado>3</puerta_empleado>
            <cpostal_empleado>45220</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Administrativa</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
   <!--clinica04-->
   <clinica id="CM004" central="aigaalma8888">
      <nombre>Clínica Malluna</nombre>
      <contacto>
        <telefono>961110287</telefono>
        <email>cmallu@malluna.com</email>
      </contacto>
      <direccion>
        <calle>Reak</calle>
        <numero>3</numero>
        <puerta>20</puerta>
        <cpostal>46902</cpostal>
      </direccion>
      <pacientes>
       <paciente nump="D45251247">
         <historial num="D452512470025">
          <tratamientos>Operación rotula</tratamientos>
          <tratamientos>Esguince pie izquierdo</tratamientos>
         </historial>
         <datos>
           <nif_paciente>45251247D</nif_paciente>
           <nombre_paciente>Teresa</nombre_paciente>
           <apellidos_paciente>Casals Sanz</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Damasco</calle_paciente>
              <numero_paciente>11</numero_paciente>
              <puerta_paciente>5</puerta_paciente>
              <cpostal_paciente>45880</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>29</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>620200111</telefono_paciente>
              <email_paciente>teresa_tesa@hotmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
      <paciente nump="E14521457">
         <historial num="E145214570018">
          <tratamientos>Rotura de radio</tratamientos>
          <tratamientos>Luxación de hombro</tratamientos>
         </historial>
         <datos>
           <nif_paciente>14521457E</nif_paciente>
           <nombre_paciente>Marina</nombre_paciente>
           <apellidos_paciente>Garcia Lenzo</apellidos_paciente>
           <direccion_paciente>
              <calle_paciente>Rio</calle_paciente>
              <numero_paciente>8</numero_paciente>
              <puerta_paciente>8</puerta_paciente>
              <cpostal_paciente>46900</cpostal_paciente>
           </direccion_paciente>
           <edad_paciente>20</edad_paciente>
            <contacto_paciente>
              <telefono_paciente>635681122</telefono_paciente>
              <email_paciente>MarMarina.GL@gmail.com</email_paciente>
            </contacto_paciente>
         </datos>
       </paciente>
     </pacientes>
     <empleados>
       <empleado nume="R75894889004">
          <nombre_empleado>Carla</nombre_empleado>
          <apellidos_empleado>Pardo Muñoz</apellidos_empleado>
          <nif_empleado>75894889R</nif_empleado>
          <edad_empleado>38</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654453212</telefono_empleado>
            <email_empleado>carparmu@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Castaño</calle_empleado>
            <numero_empleado>18</numero_empleado>
            <puerta_empleado>6</puerta_empleado>
            <cpostal_empleado>46902</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Traumatologa</puesto_empleado>
       </empleado>
        <empleado nume="R54225521004">
          <nombre_empleado>Marc</nombre_empleado>
          <apellidos_empleado>Miravet Sanz</apellidos_empleado>
          <nif_empleado>54225521R</nif_empleado>
          <edad_empleado>35</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654512565</telefono_empleado>
            <email_empleado>marmirsanz@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Donatelo</calle_empleado>
            <numero_empleado>1</numero_empleado>
            <puerta_empleado>2</puerta_empleado>
            <cpostal_empleado>45822</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Asesor</puesto_empleado>
       </empleado>
        <empleado nume="T58954585">
          <nombre_empleado>Clara</nombre_empleado>
          <apellidos_empleado>Ros Cacorla</apellidos_empleado>
          <nif_empleado>58954585T</nif_empleado>
          <edad_empleado>34</edad_empleado>
          <contacto_empleado>
            <telefono_empleado>654457212</telefono_empleado>
            <email_empleado>clarrosca@gmail.com</email_empleado>
          </contacto_empleado>
          <direccion_empleado>
           <calle_empleado>Albana</calle_empleado>
            <numero_empleado>10</numero_empleado>
            <puerta_empleado>10</puerta_empleado>
            <cpostal_empleado>46901</cpostal_empleado>
          </direccion_empleado>
          <puesto_empleado>Enfermera</puesto_empleado>
       </empleado>
     </empleados>
   </clinica>
  </clinicas>
```
### Clinics XSD
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!--
	===============================
	Lenguajes de Marcas
	Bloque 2 Schemas, actividad 2.
	Alumno: Christian Molina.
	===============================

	Notas:

  + Las clinicas permanecen con un numero maximo ilimitado por su futuro crecimiento.

	+ Cualquier clinica, tiene obligatoriamente un identificador (atributo) donde son las inicial de la clinica
     seguido del orden en que se fundo la clinica y a su vez un atributo "central" del cual inidica la cadena de clinicas que hay relacionada.

	+ Un paciente o un empleado obligatoriamente tendra un NIF asociado (atributo) + un numero del orden de la clinica fundada.

	+ Los apellidos de los pacientes y empleados son obligatorios (para mayor seguridad para la clinica).

	+ Un paciente, puede tener mas de un tratamiento y puede ser que no tenga ninguno.

	+ El email ya sea de la clinica o de pacientes o de empleados se regula para que no hayan posibles errores.

	+ Cada paciente tendra obligatoriamente un numero de historial (atributo) del cual sera su NIF y un numero aleatorio.

	+ Se ha regulado el numero de telefono a 9 digitos para que no haya ninguna equivocación además de obligar a que sean
	    numeros positivos.

	+ Se ha regulado el codigo postal a 5 digitos para que no haya ninguna equivocación ademas de obligar a que sean
	   numeros positivos.

	+ La edad no puede ser superior a 100 años ni inferior a 1 año para los pacientes y para los empleados de 18 a 68 años

	+ El nombre de la clinica, ha de tener una longitud máxima de 30 caracteres y para paciente o empleados 15 caracteres

	+ Los apellidos del paciente y empleados, han de tener una longitud máxima de 50 caracteres.

	+ El numero de empleados que habra por clinica será de 2 como minimo a 4 como maximo empleados.

	+ Los tipos de trabajo son de un tipo determinado (enfermer@, odontolog@, traumatolog@, administrativ@)

	+ El numero, puerta ha de especificarse como un número positivo,
	  por ejemplo: 52.

  	+ El NIF, ha de contener un número 8 cifras + una letra ,
	  por ejemplo: 52458557K
-->
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <xsd:element name="clinicas">
    <xsd:complexType>
      <xsd:sequence>
        <xsd:element name="clinica" maxOccurs="unbounded">
          <xsd:complexType>
            <xsd:sequence>
              <xsd:element name="nombre">
               <xsd:simpleType>
                  <xsd:restriction base="xsd:string">
                    <xsd:maxLength value="30"/>
                  </xsd:restriction>
                </xsd:simpleType>
              </xsd:element>
              <xsd:element name="contacto">
                <xsd:complexType>
                  <xsd:sequence>
                    <xsd:element name="telefono">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:positiveInteger">
                          <xsd:totalDigits value="9"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                    <xsd:element name="email">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:string">
                          <xsd:pattern value="[^@]+@[^\.]+\..+|"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                  </xsd:sequence>
                </xsd:complexType>
              </xsd:element>
              <xsd:element name="direccion">
                <xsd:complexType>
                 <xsd:sequence>
                    <xsd:element name="calle">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:string">
                          <xsd:maxLength value="70"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                    <xsd:element name="numero" type="xsd:positiveInteger"/>
                    <xsd:element name="puerta" type="xsd:positiveInteger"/>
                    <xsd:element name="cpostal">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:positiveInteger">
                          <xsd:totalDigits value="5"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                  </xsd:sequence>
                </xsd:complexType>
              </xsd:element>
              <xsd:element name="pacientes">
                <xsd:complexType>
                 <xsd:sequence>
                    <xsd:element name="paciente" maxOccurs="unbounded">
                       <xsd:complexType>
                        <xsd:sequence>
                        <xsd:element name="historial">
                          <xsd:complexType>
                            <xsd:sequence>
                              <xsd:element name="tratamientos" type="xsd:string" maxOccurs="unbounded"/>
                            </xsd:sequence>
                            <xsd:attribute name="num" type="xsd:string"/>
                          </xsd:complexType>
                        </xsd:element>
                        <xsd:element name="datos">
                          <xsd:complexType>
                            <xsd:sequence>
                              <xsd:element name="nif_paciente">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:string">
                                    <xsd:pattern value="\d{8}[A-Z]"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                              <xsd:element name="nombre_paciente">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:string">
                                    <xsd:maxLength value="15"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                              <xsd:element name="apellidos_paciente">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:string">
                                    <xsd:maxLength value="50"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                              <xsd:element name="direccion_paciente">
                                <xsd:complexType>
                                  <xsd:sequence>
                                    <xsd:element name="calle_paciente">
                                      <xsd:simpleType>
                                        <xsd:restriction base="xsd:string">
                                          <xsd:maxLength value="70"/>
                                        </xsd:restriction>
                                      </xsd:simpleType>
                                    </xsd:element>
                                    <xsd:element name="numero_paciente" type="xsd:positiveInteger"/>
                                    <xsd:element name="puerta_paciente" type="xsd:positiveInteger"/>
                                    <xsd:element name="cpostal_paciente">
                                      <xsd:simpleType>
                                        <xsd:restriction base="xsd:positiveInteger">
                                          <xsd:totalDigits value="5"/>
                                        </xsd:restriction>
                                      </xsd:simpleType>
                                    </xsd:element>
                                  </xsd:sequence>
                                </xsd:complexType>
                              </xsd:element>
                              <xsd:element name="edad_paciente">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:positiveInteger">
                                    <xsd:maxInclusive value="100"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                              <xsd:element name="contacto_paciente">
                                <xsd:complexType>
                                 <xsd:sequence>
                                    <xsd:element name="telefono_paciente">
                                      <xsd:simpleType>
                                        <xsd:restriction base="xsd:positiveInteger">
                                          <xsd:totalDigits value="9"/>
                                        </xsd:restriction>
                                      </xsd:simpleType>
                                    </xsd:element>
                                    <xsd:element name="email_paciente">
                                      <xsd:simpleType>
                                        <xsd:restriction base="xsd:string">
                                          <xsd:pattern value="[^@]+@[^\.]+\..+|"/>
                                        </xsd:restriction>
                                      </xsd:simpleType>
                                    </xsd:element>
                                 </xsd:sequence>
                                </xsd:complexType>
                              </xsd:element>
                            </xsd:sequence>
                          </xsd:complexType>
                        </xsd:element>
                      </xsd:sequence>
                      <xsd:attribute name="nump" type="xsd:string"/>
                    </xsd:complexType>
                  </xsd:element>
                </xsd:sequence>
              </xsd:complexType>
            </xsd:element>
            <xsd:element name="empleados">
              <xsd:complexType>
                <xsd:sequence>
                  <xsd:element name="empleado" minOccurs="2" maxOccurs="4">
                    <xsd:complexType>
                      <xsd:sequence>
                        <xsd:element name="nombre_empleado">
                          <xsd:simpleType>
                            <xsd:restriction base="xsd:string">
                              <xsd:maxLength value="15"/>
                            </xsd:restriction>
                          </xsd:simpleType>
                        </xsd:element>
                        <xsd:element name="apellidos_empleado">
                          <xsd:simpleType>
                            <xsd:restriction base="xsd:string">
                              <xsd:maxLength value="50"/>
                            </xsd:restriction>
                          </xsd:simpleType>
                        </xsd:element>
                        <xsd:element name="nif_empleado">
                          <xsd:simpleType>
                            <xsd:restriction base="xsd:string">
                              <xsd:pattern value="\d{8}[A-Z]"/>
                            </xsd:restriction>
                          </xsd:simpleType>
                        </xsd:element>
                        <xsd:element name="edad_empleado">
                          <xsd:simpleType>
                            <xsd:restriction base="xsd:positiveInteger">
                              <xsd:minInclusive value="18"/>
                              <xsd:maxInclusive value="68"/>
                            </xsd:restriction>
                          </xsd:simpleType>
                        </xsd:element>
                        <xsd:element name="contacto_empleado">
                          <xsd:complexType>
                            <xsd:sequence>
                              <xsd:element name="telefono_empleado">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:positiveInteger">
                                    <xsd:totalDigits value="9"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                              <xsd:element name="email_empleado">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:string">
                                    <xsd:pattern value="[^@]+@[^\.]+\..+|"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                            </xsd:sequence>
                          </xsd:complexType>
                        </xsd:element>
                        <xsd:element name="direccion_empleado">
                          <xsd:complexType>
                            <xsd:sequence>
                              <xsd:element name="calle_empleado">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:string">
                                    <xsd:maxLength value="70"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                              <xsd:element name="numero_empleado" type="xsd:positiveInteger"/>
                              <xsd:element name="puerta_empleado" type="xsd:positiveInteger"/>
                              <xsd:element name="cpostal_empleado">
                                <xsd:simpleType>
                                  <xsd:restriction base="xsd:positiveInteger">
                                    <xsd:totalDigits value="5"/>
                                  </xsd:restriction>
                                </xsd:simpleType>
                              </xsd:element>
                            </xsd:sequence>
                          </xsd:complexType>
                        </xsd:element>
                        <xsd:element name="puesto_empleado">
                          <xsd:simpleType>
                            <xsd:restriction base="xsd:string">
                              <xsd:enumeration value="Odontologo"/>
                              <xsd:enumeration value="Odontologa"/>
                              <xsd:enumeration value="Traumatologo"/>
                              <xsd:enumeration value="Traumatologa"/>
                              <xsd:enumeration value="Asesor"/>
                              <xsd:enumeration value="Asesora"/>
                              <xsd:enumeration value="Enfermero"/>
                              <xsd:enumeration value="Enfermera"/>
                              <xsd:enumeration value="Administrativo"/>
                              <xsd:enumeration value="Administrativa"/>
                            </xsd:restriction>
                          </xsd:simpleType>
                        </xsd:element>
                      </xsd:sequence>
                      <xsd:attribute name="nume" type="xsd:string"/>
                    </xsd:complexType>
                  </xsd:element>
                </xsd:sequence>
              </xsd:complexType>
            </xsd:element>
          </xsd:sequence>
          <xsd:attribute name="id" type="xsd:string"/>
          <xsd:attribute name="central" type="xsd:string"/>
        </xsd:complexType>
      </xsd:element>
    </xsd:sequence>
    <xsd:attribute name="id" type="xsd:string"/>
  </xsd:complexType>
</xsd:element>
</xsd:schema>
```
### Clinics XSD - Different Method
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!--
	===============================
	Lenguajes de Marcas
	Bloque 2 Schemas, actividad 2.
	Alumno: Christian Molina.
	===============================

	Notas:

  + Las clinicas permanecen con un numero maximo ilimitado por su futuro crecimiento.

	+ Cualquier clinica, tiene obligatoriamente un identificador (atributo) donde son las inicial de la clinica
     seguido del orden en que se fundo la clinica y a su vez un atributo "central" del cual inidica la cadena de clinicas que hay relacionada.

	+ Un paciente o un empleado obligatoriamente tendra un NIF asociado (atributo) + un numero del orden de la clinica fundada.

	+ Los apellidos de los pacientes y empleados son obligatorios (para mayor seguridad para la clinica).

	+ Un paciente, puede tener mas de un tratamiento y puede ser que no tenga ninguno.

	+ El email ya sea de la clinica o de pacientes o de empleados se regula para que no hayan posibles errores.

	+ Cada paciente tendra obligatoriamente un numero de historial (atributo) del cual sera su NIF y un numero aleatorio.

	+ Se ha regulado el numero de telefono a 9 digitos para que no haya ninguna equivocación además de obligar a que sean
	    numeros positivos.

	+ Se ha regulado el codigo postal a 5 digitos para que no haya ninguna equivocación ademas de obligar a que sean
	   numeros positivos.

	+ La edad no puede ser superior a 100 años ni inferior a 1 año para los pacientes y para los empleados de 18 a 68 años

	+ El nombre de la clinica, ha de tener una longitud máxima de 30 caracteres y para paciente o empleados 15 caracteres

	+ Los apellidos del paciente y empleados, han de tener una longitud máxima de 50 caracteres.

	+ El numero de empleados que habra por clinica será de 2 como minimo a 4 como maximo empleados.

	+ Los tipos de trabajo son de un tipo determinado (enfermer@, odontolog@, traumatolog@, administrativ@)

	+ El numero, puerta ha de especificarse como un número positivo,
	  por ejemplo: 52.

  	+ El NIF, ha de contener un número 8 cifras + una letra ,
	  por ejemplo: 52458557K
-->
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">

 <!---Definición de los elementos simples-->

 <!---apellidos [maximo numero de caracteres 50]-->

    <xsd:simpleType name="apellidos">
      <xsd:restriction base="xsd:string">
        <xsd:maxLength value="50"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---edad paciente [maximo de edad 100 minimo 1]-->

    <xsd:simpleType name="edad">
      <xsd:restriction base="xsd:positiveInteger">
      <xsd:maxInclusive value="100"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---edad empleado  [maximo de edad 68 minimo 18]-->

    <xsd:simpleType name="edademple">
      <xsd:restriction base="xsd:positiveInteger">
      <xsd:minInclusive value="18"/>
      <xsd:maxInclusive value="68"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---email [No empiece por @+texto+@+no empiece por "punto"+texto+"punto"+texto(com,es,xyz,org)]-->

    <xsd:simpleType name="email">
      <xsd:restriction base="xsd:string">
      <xsd:pattern value="[^@]+@[^\.]+\..+|"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---calle [Maximo 70 caracteres]-->

    <xsd:simpleType name="calle">
      <xsd:restriction base="xsd:string">
      <xsd:maxLength value="70"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---codigo postal [puede contener 5 digitos positivos]-->

    <xsd:simpleType name="cpostal">
      <xsd:restriction base="xsd:positiveInteger">
      <xsd:totalDigits value="5"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---nif  8 numeros + letra-->

      <xsd:simpleType name="nif">
      <xsd:restriction base="xsd:string">
      <xsd:pattern value="\d{8}[A-Z]"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---nombre [Maximo 30 caracteres]-->

    <xsd:simpleType name="nombre">
      <xsd:restriction base="xsd:string">
        <xsd:maxLength value="30"/>
      </xsd:restriction>
    </xsd:simpleType>

    <!---nombre paciente y empleado [Maximo 15 caracteres]-->

    <xsd:simpleType name="nombrepaemp">
      <xsd:restriction base="xsd:string">
        <xsd:maxLength value="15"/>
      </xsd:restriction>
    </xsd:simpleType>

  <!---numero [numero positivo]-->

    <xsd:simpleType name="numero">
      <xsd:restriction base="xsd:positiveInteger">
      </xsd:restriction>
    </xsd:simpleType>

  <!---puerta [numero positivo]-->

    <xsd:simpleType name="puerta">
      <xsd:restriction base="xsd:positiveInteger">
      </xsd:restriction>
    </xsd:simpleType>

    <!---puesto [Determinacion de puesto de trabajo con enumeration]-->

      <xsd:simpleType name="puesto">
      <xsd:restriction base="xsd:string">
      <xsd:enumeration value="Odontologo"/>
      <xsd:enumeration value="Odontologa"/>
      <xsd:enumeration value="Traumatologo"/>
      <xsd:enumeration value="Traumatologa"/>
      <xsd:enumeration value="Asesor"/>
      <xsd:enumeration value="Asesora"/>
      <xsd:enumeration value="Enfermero"/>
      <xsd:enumeration value="Enfermera"/>
      <xsd:enumeration value="Administrativo"/>
      <xsd:enumeration value="Administrativa"/>
      </xsd:restriction>
    </xsd:simpleType>

<!---telefono [ Maximo numero de digitos 9]-->

    <xsd:simpleType name="telefono">
      <xsd:restriction base="xsd:positiveInteger">
      <xsd:totalDigits value="9"/>
      </xsd:restriction>
    </xsd:simpleType>

<!---tratamientos-->

    <xsd:simpleType name="tratamientos">
      <xsd:restriction base="xsd:string">
      </xsd:restriction>
    </xsd:simpleType>

    <!---****************************************************************-->

  <!---Definición de los elementos complejos-->

  <!---HISTORIAL-->

    <xsd:complexType name="historial">
      <xsd:sequence>
        <xsd:element name="tratamientos" type="tratamientos" minOccurs="0" maxOccurs="unbounded"/>
      </xsd:sequence>
      <xsd:attribute name="num" type="xsd:string" use="required"/>
    </xsd:complexType>

  <!---CONTACTOS(clinica, paciente, empleado)-->

  <!---C.clinica-->

    <xsd:complexType name="contacto">
      <xsd:sequence>
        <xsd:element name="telefono" type="telefono"/>
        <xsd:element name="email" type="email"/>
      </xsd:sequence>

  <!---C.paciente-->

    </xsd:complexType>
    <xsd:complexType name="contacto_paciente">
      <xsd:sequence>
        <xsd:element name="telefono_paciente" type="telefono"/>
        <xsd:element name="email_paciente" type="email"/>
      </xsd:sequence>
    </xsd:complexType>

    <!---C.empleado-->

      <xsd:complexType name="contacto_empleado">
      <xsd:sequence>
        <xsd:element name="telefono_empleado" type="telefono"/>
        <xsd:element name="email_empleado" type="email"/>
      </xsd:sequence>
    </xsd:complexType>

<!---DIRECCION(clinica, paciente, empleado)-->

<!---D.clinica-->

    <xsd:complexType name="direccion">
      <xsd:sequence>
        <xsd:element name="calle" type="calle"/>
        <xsd:element name="numero" type="numero"/>
         <xsd:element name="puerta" type="puerta"/>
          <xsd:element name="cpostal" type="cpostal"/>
      </xsd:sequence>
    </xsd:complexType>

  <!---D.paciente-->

    <xsd:complexType name="direccion_paciente">
      <xsd:sequence>
        <xsd:element name="calle_paciente" type="calle"/>
        <xsd:element name="numero_paciente" type="numero"/>
         <xsd:element name="puerta_paciente" type="puerta"/>
          <xsd:element name="cpostal_paciente" type="cpostal"/>
      </xsd:sequence>
    </xsd:complexType>

<!---D.empleado-->

    <xsd:complexType name="direccion_empleado">
      <xsd:sequence>
        <xsd:element name="calle_empleado" type="calle"/>
        <xsd:element name="numero_empleado" type="numero"/>
         <xsd:element name="puerta_empleado" type="puerta"/>
          <xsd:element name="cpostal_empleado" type="cpostal"/>
      </xsd:sequence>
    </xsd:complexType>

<!---DATOS-->

    <xsd:complexType name="datos">
      <xsd:sequence>
        <xsd:element name="nif_paciente" type="nif"/>
        <xsd:element name="nombre_paciente" type="nombrepaemp"/>
        <xsd:element name="apellidos_paciente" type="apellidos"/>
        <xsd:element name="direccion_paciente" type="direccion_paciente"/>
        <xsd:element name="edad_paciente" type="edad"/>
        <xsd:element name="contacto_paciente" type="contacto_paciente"/>
      </xsd:sequence>
    </xsd:complexType>

<!---PACIENTE-->

    <xsd:complexType name="paciente">
      <xsd:sequence>
        <xsd:element name="historial" type="historial"/>
        <xsd:element name="datos" type="datos"/>
      </xsd:sequence>
      <xsd:attribute name="nump" type="xsd:string" use="required"/>
    </xsd:complexType>

  <!---PACIENTES-->

    <xsd:complexType name="pacientes">
      <xsd:sequence>
        <xsd:element name="paciente" type="paciente" maxOccurs="unbounded"/>
      </xsd:sequence>
    </xsd:complexType>

  <!---EMPLEADO-->

    <xsd:complexType name="empleado">
      <xsd:sequence>
        <xsd:element name="nombre_empleado" type="nombrepaemp"/>
        <xsd:element name="apellidos_empleado" type="apellidos"/>
       <xsd:element name="nif_empleado" type="nif"/>
       <xsd:element name="edad_empleado" type="edademple"/>
       <xsd:element name="contacto_empleado" type="contacto_empleado"/>
       <xsd:element name="direccion_empleado" type="direccion_empleado"/>
       <xsd:element name="puesto_empleado" type="puesto"/>
      </xsd:sequence>
      <xsd:attribute name="nume" type="xsd:string" use="required"/>
    </xsd:complexType>

  <!---EMPLEADOS-->

    <xsd:complexType name="empleados">
      <xsd:sequence>
        <xsd:element name="empleado" type="empleado" minOccurs="2" maxOccurs="4"/>
      </xsd:sequence>
    </xsd:complexType>

    <!--CLINICA-->

    <xsd:complexType name="clinica">
      <xsd:sequence>
        <xsd:element name="nombre" type="nombre"/>
        <xsd:element name="contacto" type="contacto"/>
        <xsd:element name="direccion" type="direccion"/>
        <xsd:element name="pacientes" type="pacientes"/>
        <xsd:element name="empleados" type="empleados"/>
      </xsd:sequence>
      <xsd:attribute name="id" type="xsd:string" use="required"/>
      <xsd:attribute name="central" type="xsd:string" use="required"/>
    </xsd:complexType>

    <!--CLINICAS-->

    <xsd:complexType name="clinicas">
      <xsd:sequence>
        <xsd:element name="clinica" type="clinica" maxOccurs="unbounded"/>
      </xsd:sequence>
      <xsd:attribute name="id" type="xsd:string" use="required"/>
    </xsd:complexType>
    <xsd:element name="clinicas" type="clinicas"/>
</xsd:schema>
```
##----UNIT 2 COMPLEMENTARY EXERCISES----
### SONGS XML
```xml
<?xml version="1.0" encoding="utf-8"?>
<cancion xmlns:xsd="http://www.w3.org/2001/XMLSchema-instance" duracion="4:29" anio="2008" xsd:noNamespaceSchemaLocation="Act_5_xsd.xsd">
	<titulo> Give it 2 me </titulo>
	<compositores>
		<compositor>
			<nombre> Pharrell </nombre>
			<apellidos> Williams </apellidos>
		</compositor>
	</compositores>
	<productores>
		<productor>
		<nombre> Pharrell </nombre>
		<apellidos> Williams </apellidos>
		</productor>
	</productores>
	<sello> Warner Bros. Records </sello>
	<artista> Madonna </artista>

</cancion>
```
### SONGS XSD
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
<xsd:element name="cancion">
    <xsd:complexType>
      <xsd:sequence>
        <xsd:element name="titulo">
          <xsd:simpleType>
            <xsd:restriction base="xsd:string">
             <xsd:maxLength value="60"/>
            </xsd:restriction>
          </xsd:simpleType>
        </xsd:element>
        <xsd:element name="compositores">
          <xsd:complexType>
            <xsd:sequence>
              <xsd:element name="compositor">
                <xsd:complexType>
                  <xsd:sequence>
                    <xsd:element name="nombre">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:string">
                          <xsd:maxLength value="30"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                    <xsd:element name="apellidos">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:string">
                          <xsd:maxLength value="40"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                  </xsd:sequence>
                </xsd:complexType>
              </xsd:element>
            </xsd:sequence>
          </xsd:complexType>
        </xsd:element>
        <xsd:element name="productores">
          <xsd:complexType>
            <xsd:sequence>
              <xsd:element name="productor">
                <xsd:complexType>
                  <xsd:sequence>
                    <xsd:element name="nombre">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:string">
                          <xsd:maxLength value="30"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                    <xsd:element name="apellidos">
                      <xsd:simpleType>
                        <xsd:restriction base="xsd:string">
                          <xsd:maxLength value="40"/>
                        </xsd:restriction>
                      </xsd:simpleType>
                    </xsd:element>
                  </xsd:sequence>
                </xsd:complexType>
              </xsd:element>
            </xsd:sequence>
          </xsd:complexType>
        </xsd:element>
        <xsd:element name="sello">
          <xsd:simpleType>
            <xsd:restriction base="xsd:string">
            <xsd:maxLength value="60"/>
            </xsd:restriction>
          </xsd:simpleType>
        </xsd:element>
        <xsd:element name="artista">
          <xsd:simpleType>
            <xsd:restriction base="xsd:string">
              <xsd:maxLength value="40"/>
            </xsd:restriction>
          </xsd:simpleType>
        </xsd:element>
      </xsd:sequence>
      <xsd:attribute name="duracion" type="xsd:string" use="required"/>
      <xsd:attribute name="anio" type="xsd:positiveInteger" use="optional"/>
    </xsd:complexType>
  </xsd:element>
</xsd:schema>
```
###STUDENTS TAB XML
```xml
<?xml version="1.0" encoding="utf-8"?>
<ficha_alumno xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="alumnos.xsd">  
	<nombre>
		Pepito Perez Parra
	</nombre>
	<nacimiento>
		<dia>1</dia>
<mes>1</mes>
<anio>1980</anio>
  </nacimiento>
	<direccion>
		<calle> Avda.</calle>
		<poblacion> Torrent </poblacion>
		<provincia> Valencia </provincia>
		<cpostal> 46900 </cpostal>
	</direccion>
 <direccion>
		<calle> Avda.</calle>
		<poblacion> Torrent </poblacion>
		<provincia>Valencia </provincia>
		<cpostal> 46900 </cpostal>
	</direccion>

	<movil valor="si"/>
</ficha_alumno>
```
###STUDENTS TAB XSD
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <xsd:element name="ficha_alumno">
      <xsd:complexType>
        <xsd:sequence>
          <xsd:element name="nombre">
            <xsd:simpleType>
              <xsd:restriction base="xsd:string">
               <xsd:maxLength value="60"/>
              </xsd:restriction>
            </xsd:simpleType>
          </xsd:element>
          <xsd:element name="nacimiento">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="dia">
                  <xsd:simpleType>
                    <xsd:restriction base="xsd:positiveInteger">
                      <xsd:minInclusive value="1"/>
                      <xsd:maxInclusive value="31"/>
                    </xsd:restriction>
                  </xsd:simpleType>
                </xsd:element>
                <xsd:element name="mes">
                  <xsd:simpleType>
                    <xsd:restriction base="xsd:positiveInteger">
                      <xsd:minInclusive value="1"/>
                      <xsd:maxInclusive value="12"/>
                    </xsd:restriction>
                  </xsd:simpleType>
                </xsd:element>
                <xsd:element name="anio">
                  <xsd:simpleType>
                    <xsd:restriction base="xsd:positiveInteger">
                      <xsd:minInclusive value="1800"/>
                      <xsd:maxInclusive value="2018"/>
                    </xsd:restriction>
                  </xsd:simpleType>
                </xsd:element>
              </xsd:sequence>
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="direccion" maxOccurs="unbounded">
            <xsd:complexType>
              <xsd:sequence>
                <xsd:element name="calle" type="xsd:string"/>
                <xsd:element name="poblacion" type="xsd:string"/>
                <xsd:element name="provincia" type="xsd:string"/>
                <xsd:element name="cpostal" type="xsd:positiveInteger"/>
              </xsd:sequence>
            </xsd:complexType>
          </xsd:element>
          <xsd:element name="movil">
            <xsd:complexType>
              <xsd:sequence/>
              <xsd:attribute name="valor" type="xsd:string" use="required"/>
            </xsd:complexType>
          </xsd:element>
        </xsd:sequence>
      </xsd:complexType>
    </xsd:element>
  </xsd:schema>
```
##ID PERSON XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
<persona nacimiento="1999-10-20" xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="Schema2Schema.xsd">
    <datos>
			<nombre>Pepe</nombre>
			<apellidos>Garcia</apellidos>
			<dni>25390952</dni>
    </datos>
    <comentario>buena gente...</comentario>
</persona>
```
##ID PERSON XSD
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
  <xsd:element name="persona">
    <xsd:complexType>
      <xsd:sequence>
        <xsd:element name="datos">
          <xsd:complexType>
            <xsd:sequence>
              <xsd:element name="nombre">
                <xsd:simpleType>
                  <xsd:restriction base="xsd:string">
                   <xsd:maxLength value="15"/>
                  </xsd:restriction>
                </xsd:simpleType>
              </xsd:element>
              <xsd:element name="apellidos">
                <xsd:simpleType>
                  <xsd:restriction base="xsd:string">
                   <xsd:maxLength value="40"/>
                  </xsd:restriction>
                </xsd:simpleType>
              </xsd:element>
              <xsd:element name="dni">
                <xsd:simpleType>
                  <xsd:restriction base="xsd:positiveInteger">
                   <xsd:totalDigits value="8"/>
                  </xsd:restriction>
                </xsd:simpleType>
              </xsd:element>
            </xsd:sequence>
          </xsd:complexType>
        </xsd:element>
        <xsd:element name="comentario" maxOccurs="unbounded">
          <xsd:simpleType>
            <xsd:restriction base="xsd:string">
              <xsd:maxLength value="100"/>
            </xsd:restriction>
          </xsd:simpleType>
        </xsd:element>
      </xsd:sequence>
      <xsd:attribute name="nacimiento" type="xsd:date" use="required"/>
    </xsd:complexType>
  </xsd:element>
</xsd:schema>
```
