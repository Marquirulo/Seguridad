# Listas de Control de Acceso (ACL) y Firewalls
1. Firewalls y su Función  
Los firewalls son dispositivos que protegen la red al filtrar el tráfico entre redes, estableciendo un perímetro de seguridad. Pueden operar como NAT (Network Address Translation) y Proxy.  

## Tipos de firewalls:

Filtrado de paquetes básico: Basado en reglas estáticas.  
Filtrado con Inspección de Estados (SPI): Rastrea conexiones activas.  
Firewall basado en zonas (ZBF): Separa interfaces en zonas con políticas específicas.  
Proxies (ALG): Evalúan tráfico a nivel de aplicación.  
## 2. ACL (Listas de Control de Acceso)
Son reglas aplicadas a routers y switches para filtrar tráfico basado en direcciones IP, protocolos y puertos.

**Tipos de ACL:**

ACL estándar: Filtran solo por dirección IP de origen.
ACL extendidas: Filtran por dirección IP, protocolo y puerto.
ACL nombradas: Permiten mayor flexibilidad y edición.
Ejemplo de configuración de ACL en Cisco:

    access-list 110 deny tcp 192.168.1.0 0.0.0.255 any eq 23
    access-list 110 permit ip any any
    interface Fa0/0
    ip access-group 110 out
    Explicación:

Deniega conexiones Telnet desde la subred 192.168.1.0/24.  
Permite cualquier otro tráfico.  
Asigna la ACL a la interfaz Fa0/0 en sentido de salida.  
## 3. Políticas de Seguridad en ACL  
Denegar todo lo que no esté explícitamente permitido (default deny).  
Permitir todo excepto lo que esté explícitamente denegado.  
Wildcard (máscara inversa) para definir rangos de direcciones.  
Ejemplo de wildcard para 192.168.1.0/24:  

    0.0.0.255
## 4. Aplicación de ACL en IPv6
Solo existen ACL nombradas.  
En lugar de wildcard, se usa la longitud de prefijo.  
Se agregan reglas por defecto para Neighbor Discovery Protocol (NDP).  
## 5. DMZ (Zona Desmilitarizada)  
Es un área de red intermedia entre la red interna y externa.  
Aloja servidores accesibles desde Internet como DNS, correo y web.  
Las ACL controlan qué tráfico se permite entre DMZ e Internet.  
##  6. Consideraciones Finales
Las ACL deben aplicarse lo más cerca posible del origen del tráfico denegado.  
El tráfico generado por el router no es afectado por las ACL.  
Las reglas deben ordenarse desde lo más específico a lo más general.  
El comando log permite registrar eventos, pero puede afectar el rendimiento.
Este resumen cubre los conceptos clave del documento de forma condensada. ¿Necesitas más detalles sobre algún punto en particular? 🚀
