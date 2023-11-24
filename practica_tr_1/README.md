Instalación del servidor web apache. Usaremos dos dominios mediante el archivo hosts: centro.intranet y departamentos.centro.intranet. El primero servirá el contenido mediante wordpress y el segundo una aplicación en python

Empezamos por instalar apache, lo primero que vamos a hacer es comprobar que apt esté actualizado

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/7af81ded-81cf-4c5c-87f3-4644a1abf279)

Después pasamos a instalar apache

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/e8aeecbc-e553-418a-b9b3-0cfcae43a2f4)

Ahora instalamos mysql

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/20812629-96c8-4280-9699-485e55489a2f)

A continuación instalamos php

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/d495c83d-2daf-4c21-9fb9-190523409565)

creamos el directorio para el primer dominio

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/60d9d6c6-4070-4816-af52-3dbd0fd93da6)

Una vez tenemos listos apache, mysql y php pasamos a instalar wordpress, para ello lo primero que haremos es acceder a mysql como root:

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/ddf6928e-70da-4998-a1c1-9672704a2793)

Ahora creamos la base de datos que necesitaremos para utilizar wordpress

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/00274a4f-ecf7-4da3-8e80-0489c56b57a4)

Ahora creamos un usuario que usaremos para gestionar todo lo relacionado con wordpress y le damos permisos

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/9c689380-31b1-48c2-8545-d131efc8a332)

Ahora habilitamos reemplazos .htaccess

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/5312f4d1-dbc7-499a-a520-605596da5711)

tengo que cambiar el nombre del primer dominio de dominio1 a centro.intranet ya que le di el nombre equivocado por error

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/149cb2ca-5545-491b-a43b-36578cae93a7)

Ahora habilito el módulo de escritura

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/f7319cd9-f2df-43ce-93d8-6a8484eb274f)

Una vez hecho todo esto ya podemos instalar wordpress, empezamos por descargarlo y descomprimirlo para crear la estructura de archivos de wordpress

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/0e4bca6d-0047-48e8-be5e-b20d6b432d58)

Ahora creamos un archivo .htaccess para que wordpress lo utilice, también copiamos sobre el archivo de configuración de muestra al nombre de archivo que lee WordPress

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/8aa221d3-f851-4774-a4e1-bbec7338c75b)

Ahora creamos la carpeta de actualización para wordpress 

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/5589de06-91fb-493a-9704-551b37f19f82)

Una vez hecho esto copiamos todos los archivos a nuestra carpeta centro.intranet

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/f14b6c4a-9533-4a1f-9854-e0c190f77ff8)
