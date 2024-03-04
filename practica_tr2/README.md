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

