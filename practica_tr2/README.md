Lo primero será instalar los programas que vamos a necesitar:

Apache con "sudo apt-get install apache2"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/0b9b7b9b-29b2-4110-a01a-eb7a04fea1de)

El DNS, en este caso instalamos bind9, con "sudo apt-get bind9"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/cb8dfb56-b8e8-41d9-b270-3a3ffc9cb8d4)

Después instalamos las librerias de php para apache con "sudo apt-get install libapache2-mod-php"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/455a3e14-0ddf-42ee-999e-3a6639800f2e)

Ahora instalamos el servidor mysql con "sudo apt install mysql-server"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/86886815-cbdb-4789-81b1-a6b97e8b6d7e)

Ahora instalo el administrador de php con "sudo apt install phpmyadmin"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/1511a443-4408-4193-bc85-372c782fb4f5)

Después instalamos el modulo de python para apache con "sudo apt-get install libapache2-mod-wsgi-py3"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/66e3b2f4-918d-4d53-8aaa-196714b16a53)

Ahora instalamos ProFtpd con "sudo apt-get install proftpd"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/3bd2ed2b-49a7-435f-a512-60ed457723d3)

OpenSsl con "sudo apt-get install openssl"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/1c68bb71-03eb-4ffb-b5fa-5615e23da8e1)

Filezilla con "sudo apt-get install filezilla"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/c929dd3e-4c6a-4b50-a805-4445224dc8e0)

Postfix con "sudo apt-get install postfix"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/26d7c90a-2b56-4791-9975-e7c0d9e0f87c)

Dovecot con "sudo apt-get install dovecot-imapd dovecot-pop3d"

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/a6865a3b-fc61-4301-b809-bebd7ec3e13c)

configuración

Configuramos postfix:

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/49ae752b-4ede-4979-b552-6312261d21f7)

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/e62a1f66-a955-4dd3-8570-dff9660a6853)

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/3b0d1983-3d56-45cf-a982-885b570756c1)

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/48027d0b-69d7-4e0b-b6a8-8518c806ddef)

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/26ac8ffe-b6f6-499a-8c5f-fc0d3ebf9072)

Generamos certificado ssl:

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/c9491a55-56e6-41f2-a67b-48e77cfd4792)

Ahora configuramos filezilla para entrar utilizando este certificado:

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/f9ec8cce-3f5c-4785-b44a-75193a19c1a6)

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/1f72e2ba-87d2-4c8a-9cb8-adda98148e17)

Permitimos los protocolos pop3 e imap en dovecot

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/774fd03c-a352-49a5-a481-6d8b30ec7eef)

Comprobamos que ssl está activado para dovecot

![image](https://github.com/juanjo002/ejerciciosSRI/assets/122454341/80e6be38-fe1f-4cc9-bf73-353d56557bf5)

Script:
```bash
#!/bin/bash

# Verificación de argumentos
if [ $# -ne 3 ]; then
    echo "Error: Debes proporcionar 3 argumentos - nombre, contraseña e IP."
    exit 1
fi

# Asignación de variables
usuario=$1
contra=$2
ip=$3
dominio="${usuario}.marisma.local"
zona_directa="/etc/bind/zones/db.marisma.local"
zona_inversa="/etc/bind/zones/db.192.168.195"
ruta_a="/etc/apache2/sites-available/${dominio}.conf"
ruta_e="/etc/apache2/sites-enabled/${dominio}"
document_root="/var/www/html/$usuario"
dir_python="${document_root}/python-web"
app_python="${dir_python}/mypythonapp"
public_python="${dir_python}/public_html"
controller_py="${app_python}/controller.py"

# Creación del directorio de trabajo y configuración de la contraseña
sudo useradd -m -d /home/$usuario -s /bin/bash $usuario
echo "$usuario:$contra" | sudo chpasswd

# Configuración subdominio DNS
echo "\$ORIGIN ${dominio}." >> $zona_directa
echo "@ IN A ${ip}" >> $zona_directa
echo "www IN A ${ip}" >> $zona_directa
echo "${ip} IN PTR ns.${dominio}." >> $zona_inversa

# Configuración de Apache y host virtual
echo "${ip} ${dominio}" >> /etc/hosts
echo "127.0.0.1 ${dominio}" >> /etc/hosts
mkdir $document_root
mkdir $dir_python
mkdir $app_python
mkdir $public_python
touch $controller_py
echo "# -*- coding: utf-8 -*-
def application(environ,start_response):
status= '200 OK'
html = 'Página del usuario ${usuario} python'
html = bytes(html,encoding='utf-8')
response_header = [('Content-type','text/html')]
start_response(status,response_header)
yield html" > ${controller_py}
echo "<VirtualHost *:80>
ServerAdmin admin@$dominio
ServerName $dominio
WSGIScriptAlias / $controller_py
DocumentRoot $public_python
<Directory />
Options FollowSymLinks
AllowOverride all
</Directory>
ErrorLog /var/log/apache2/$dominio.errorLog.log
CustomLog /var/log/apache2/$dominio.customLog.log combined
</VirtualHost>" | sudo tee $ruta_a > /dev/null

# Verificar configuración de Apache
apache2ctl configtest

# Habilitar el sitio y reiniciar Apache en caso de éxito
if [ $? -eq 0 ]; then
    a2ensite $dominio > /dev/null
    systemctl restart apache2
else
    echo "Error en la configuración de Apache. No se ha habilitado el sitio."
fi

# Configuración base de datos MySQL
mysql -u root -e "CREATE DATABASE $usuario;"
mysql -u root -e "CREATE USER '$usuario'@'localhost' IDENTIFIED BY  '$contra';"
mysql -u root -e "GRANT ALL PRIVILEGES ON $usuario.* TO '$usuario'@'localhost';"
mysql -u root -e "FLUSH PRIVILEGES;"

echo "El usuario ${usuario} ha sido creado con éxito"
```
