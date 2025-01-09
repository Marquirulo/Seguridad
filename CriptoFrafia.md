# Resumen Rapido para repasar

### Objetivos Seguridad
  1.Confidencialidad (Asegurar info solo para usuarios autorizados, Cifrado de datos)
  2.Integridad datos 
  3.Gestion de la identidad (Autenticacion,autorizacion y auditoria)(Contraseñas,Certificados,Tarjetas inteligentes,Biometria...)
  4.No repudio
  5.Disponibilidad

### (Autenticacion,autorizacion y auditoria)
  **Autenticacion**:(Contraseñas,Certificados,Tarjetas inteligentes,Biometria...)
  **Autorizacion**:Una vez autenticado este dispondra de una serie de Derechos
  **Auditoria**:Los procesos de autenticacion y autorizacion deben ser registrados

**Sistemas:AAA(Radius,Tacas)**

### Integridad
  Es el encargado de asegurar que el mensaje recibido fue el enviado por la otra parte y no un  mensaje manipulado por un tercero. Se usan Resumenes generados con funciones hush

## Criptografia
  Sistemas clasica sustitucion y transposicon
  Sistemas Modernos: **Clave Publica y Clave Privada**

### Algoritmos Clave Simetrica (Para Privada) SOFTWARE PGP GPG
  **AES**,DES,IDE,RC2
### Algoritomos Clave Publica (Asimetrica)
  **RSA**,DSA,DSS
### HASH
  **SHA256**,MD5
## algoritomos de intercambio de claves
  **Diffie-Hellman**

## Cifrado de clave Privada (Simetrica)
  Con gpg:
    gpg -c (cipher) lala.txt --> cifra la informacion y te  pide contraseña para luego desencriptarla
## Cifrado clave Publica (Asimetrica)
  Se cifra la info con la clave privada y se descifra con la publica

Asimetricos: Largos  y complejos  1024  Bits
Simetricos: Cortos y "ligeros"

## Message Diggest (SHA256,MD5)
  Probar la integridad de los ficheros(Explicacion mas adelante)

#  Cifrado Hibrido
  Se utiliza claves simtericas "Temporales"  que solo duran la sesion o transmision **Clave de Sesion**

![imagen](https://github.com/user-attachments/assets/b50a43b0-2d90-49f9-a000-f7848fe3d198)

1. Se hace un  hash de los datos, se cifra (Asimetrico)  con la clave privada del emisor  y se envia para ser descifrado por el receptor con la clave publica del emisor
2. Se cifran los dados simtericamente con la clave de sesion  y se mandan
2.5  Se cifra la clave de sesion con la clave  publica del receptor  para que el la descifre con SU privada  y utilizarla para descifrar los datos



  
