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

Ahora realizamos los ajustes de propiedad y permisos

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/8c06a8f7-f05c-48af-acfb-70434fcecd84)

A continuación, ejecutaremos dos comandos find para establecer los permisos correctos de los directorios y archivos de WordPress

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/50ad075e-9280-4c10-a5b0-93e8493330ba)

editamos el archivo de configuración de wordpress, para esto lo primero que hacemos es generar valores seguros de claves

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/8532c9c8-c07a-40af-9dc5-164fdfc9cddd)

Ahora utilizamos estas claves en nuestro archivo de configuración

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/3f217565-8a1f-43bd-8052-6691a8b91bff)

Ahora completamos la instalación a traves de la interfaz web

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/d95e7f36-d74b-4db3-8e4e-2b2f7423c1e6)

y ya tenemos wordpress en el primer dominio:

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/1557393f-f241-4b29-8fc2-80667dcee021)

Ahora pasamos a instalar wsgi

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/9ca0e25e-37dc-4c04-ba82-3da18b9794ef)

una vez tenemos instalado wsgi nos preparamos para crear nuestra aplicación python, para ello lo primero que hacemos es crear los directorios para la estructura

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/ea9129ad-9f89-456f-81c1-62759e85aae8)

También crearemos una carpeta en la almacenaremos los log de errores

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/9d25be6f-51a2-499b-bb32-15b31f3a8be4)

Creamos un archivo que gestione todas las peticiones del usuario

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/3fd91bab-47f9-4757-a214-99d666663c96)

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/963b8f69-5c69-471a-8a35-26fcb9098472)

Lo proximo que tenemos que hacer es configurar el virtual host

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/8724d1c3-9cc4-4db8-badd-4d97f27d254e)

Una vez configurado nuestro virtual host habilitamos el sitio web

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/1f7b704e-3e3f-43f2-bb9c-e3784ffdf979)

Ahora agregamos la nueva dirección dentro de el archivo hosts

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/dc88991a-c68d-49c7-97ec-4dc5264e20ec)

Y con esto ya podriamos acceder escribiendo en el buscador "http://python-web"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/d4f51f5e-0e6c-428d-a04c-5eaefec8a10c)

Ahora pasamos a proteger la aplicación python con autenticación, para ello lo primero que tenemos que hacer es instalar las utilidades de apache

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/8c5786e1-2b9f-462e-a927-ddca3a8f42b2)

Ahora creamos un archivo de contraseñas

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/fbe93533-6a0b-4587-96b6-cb13ff660b98)

Después configuramos el control de acceso dentro del host virtual

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/c6a02a09-2d0d-47dd-a33a-ec2ef68e1f5d)

Y ya estaría funcionando

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/82238baa-3e17-4af4-9937-2cad5a0b5167)
