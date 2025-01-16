## Para Habilitar el proceso  
        #router ospf 10(Numero de proceso)
        ### se añaden las rutas que quieres compartir por OSPF##
        #network IP (Mascara invertida/WildCard) area 0
        #network IP 0.0.0.0 (QuadCero puede funcionar en IOS ""modernos"") area 0

## Otro Metodo  
        #interface (La que quieras difundir)
        #ip ospf 10 area 0

## Para no mandar paquedes de OSPF por la interfaz  
        # IP ospf 10
        #(config-routers) passive-interface fa0/0
    
## DR BDR => Router Rey / Backaup del DR  
    Un router DR por red
    Tiene que ser adyacente a los demas routers de la red
        #router ospf 10
        #(config-routers)routers-id 1.1.1.1 (VALE CUALQUIERA referible la menor para que sea rey 100%) 
