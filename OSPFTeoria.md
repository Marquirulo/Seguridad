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
-Show ip ospf neighbor --> Ver los routers(con OSPF) que hemos aprendido por OSPF
-shoiw ip ospf database
-show ip route


Problemas de OSPF a gran escala: Calculo de SPF habituales,Tabla de routing extensa, LSDB muy extensa  
## OSPF Multiarea soluciona los problemas anteriores.
