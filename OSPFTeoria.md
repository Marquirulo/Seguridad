# OSPF

  Es un protocolo de enrutamiento dinamico. Objetivos:  
  -Descubrir redes remotas  
  -Mantener la informacion de enrutamiento actualizada  
  -Seleccionar la mejor de las rutas  
  -Brindar la funcionalidad necesarioa para encontrar una mejor ruta si la acutual deja de estar disponible.  

Ventajas enrutamiento dinamico OSPF: Facil de configurar pero pesado y laborioso   
Desventajas: Los cambios requieren reconfiduraciones manuales.Baja escalabilidad a gran escala  

### Clasificacion de protocoles de enrutamiento:

**SA**: Sistema autonomo, es un grupo de routers controlados por una autoridad unica.

Tipos:  
**IGP**:Protocolo de gateway interior, Se usan para redes de un **SA** y de redes individuales(RIP,OSPF,EIGRP)  
**EGP**:Protocolo de gateway exteriores, Se usan para el enrutamiento entre **SA** (BGPv4)

#### IGP
Se basa en dos algoritmos. 
Protocolos basados en **vector Distancia** y Basados en algoritmo **Estado de enlace**

Pasos de los routers:
-Cada router conoce sus redes conectadas directamente  
-Los routers intercambian un paquete saludo para descubrir otros routers ejecutando el protocolo  
-Una vez descubiertas sus adyacencias crea sus paquetes de estado(LSA) con informacion del estado de sus enclaces(Conexiones)  
-Inunda con sus paquetes de estado(LSA) a los demas routers vecinos. Siempre que un router recibe un LSA se lo reenvia al resto de routers vecinos menos por el que llego.  
-Segun envia sus LSA va recibiendolos de los demas routers y crea su propia Base de Datos, arbol SPF independiente de los demas routers.  

Base de datos OSPF matiene 3 bases de datos que se visualizan:  
-Show ip ospf neighbor --> Ver los routers(con OSPF) que hemos aprendido por OSPF **Tabla de Vecinos**  
-shoiw ip ospf database **Tabla de Topologia**  
-show ip route **Tabla de enrutamiento**  


Problemas de OSPF a gran escala: Calculo de SPF habituales,Tabla de routing extensa, LSDB muy extensa   
## OSPF Multiarea soluciona los problemas anteriores.  
OSPF Miultiarea requiere de diversas areas y un diseño de red jerarquico, el area principal se llama **area 0(RED TRONCAL)**  
**ABR (Area Border Router)**Son los ruters que conectan varias zonas  
![image](https://github.com/user-attachments/assets/bae4cd36-4e03-469c-9bd7-355e5b8194a4)

Distancia administrativa:
Conectado directamente:0  
Ruta estatica puesta pot el admin:1  
EIGRP:90  
OSPF:100  

## Topologias OSPF

**Punto a Punto:** Sobre cada red solo existen 2 Routers, Una linea en serie (Conectados con cables serie) es el ejemplo perfecto  
**Broadcast networks:**Con mas de dos routers por red. Redes Ethernet
**Non-Broadcast networks:**Redes con mas de dos routers pero sin capacidad de broadcast. WAN

**Broadcast Multiacces**: Aparece en problema y es que cuando aumenta el numero de routers las adyacencias aumentan y empieza a consumir mucho ancho de banda, esto hace que la difusion de LSA pueda llegar a bloquear la red. Asi que hay que centralizar la red. 

**DR**: Un Router Designado Mantiene las adyacencias con los demas routers del segmento.

**BDR**: Es el router de respaldo del DR

### Eleccion de DR y BDR

DR: Prioridad de interfaz ospf mas alta  
BDR: Segunda priodidad mas alta

Si las prioridades son iguales se utiliza la ID de router mas alta

Una vez designado el DR ñps demas routers(Drothers) SOLO forman adyacencias con el DR y el BDR

### Tipos de paquetes OSPF

Tipo Hello: Descubren vecinos y establecen adyacencias.  
Paquetes de DBD: Lista abreviada de la base de datos de estado de enlaces. Sirven para sincornizar  
Paquetes LSU: Sirven para mandar iuinformacion LSA  
Paqueters LSR: Solicitan informacion especiifica
Paquetes LSAck: Sirven para confimar cualquiera de los paquetes anteriores.




































