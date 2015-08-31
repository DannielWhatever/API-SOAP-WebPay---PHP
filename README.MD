
3. Crea la llave privada. 
    
    openssl genrsa -des3 -out oneclick.key 2048
 
5. Crear requerimiento de certificado. De estos campos no sé bien cuáles son obligatorios, yo siempre pongo el país "CL", la ciudad "VALPARAISO" por ejemplo, lo que si debes poner si o si es la clave y el Common Name, que correspoonde a tú Código de Comercio. Si estás en fase de integración, usa el código de comercio de integración.
    
    openssl req -new -key oneclick.key -out oneclick.csr

6. Respalda el archivo de la llave privada
    
    cp oneclick.key oneclick.key2
    
7. Y aquí hace el cifrado rsa
    
    openssl rsa -in oneclick.key2 -out oneclick.key

8. Crear certificado auto-firmado
    
    openssl x509 -req -days 365 -in oneclick.csr -signkey oneclick.key -out oneclick.crt


##Configura el archvo de constantes
---------------------------------------

1. Copia tus certificados a la carpeta del sitio, puede ser en la carpeta "/include/keys"

2. Define el valor de la variable PRIVATE_KEY como la ruta de tu clave privada

3. Define el valor de la vvariable CERT_FILE que corresponde al certificado que enviarás a Tbk.

4. Define el valor de la variable SERVER_CERT, ruta del certificado público de Tbk.

5. Define la ruta de tu sitio en SITIO_CERT


