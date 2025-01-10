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

# Certificados Digitales

Acreditan una entidad es quien dice ser, Utilizan otras entidades con una cierta reputacion para ello. DIGICERT

Un certificado es basicamente un documento que contiene:Los dadis de una entidad o persona, su clave publica y la firma digital de una empresa certificadora

**PKI** es la estructura que define esto

Autoridad certificadora **CA**: emite certificados
Autoridad de Registro **RA**: Sucursales de lo anterior

**CA RAIZ** son los que estan autofirmados por entidades certificadoras

Tipos **CA**: Comerciales, Gubernamentales,Open SOurce,Propios de una entidad y Autofirmado

## SSL/TLS

Establece un canal seguro en el nivel de transporte entre dos partes

Certificacion Mutua
**En la simple solo se autentica el servidor**

1. El cliente solicita una conexión segura, y envía al servidor una lista de los cifrados y hash que el navegador soporta,
así como un número aleatorio y la versión del protocolo que desea usar.
2. El servidor responde con la versión de protocolo que se usará en relación con la recibida por el cliente, así como el
método de cifrado y hash que se usará.
3. El servidor envía a continuación su certificado al cliente . El cliente comprobará la validez del certificado, comprobando
su firma y el CA correspondiente.
4. El servidor solicita al cliente que envíe su certificado. El cliente envía su certificado al servidor, y este lo verificará
comprobando su firma y el CA correspondiente.
5. El cliente envía al servidor una prekey cifrada con la clave publica del servidor .
6. El cliente firma (resumido y cifrado con su clave privada) los mensajes de negociación previos. El servidor verificará
esto con la clave pública del cliente.
7. El cliente y el servidor generan la Key para el cifrado simétrico que van a usar gracias al número aleatorio generado al
comienzo y a la prekey.
8. El cliente envía un mensaje de finalización cifrado conteniendo el hash de los mensajes de la negociación y otros datos.
9. El servidor descifrará el mensaje y validará los hash.
10.El servidor enviará un mensaje de finalización cifrado conteniendo el hash de los mensajes de negociación y otros datos.
11. El cliente descifrará el mensaje y los validará
