Para empezar he creado un directorio con el comando mkdir y lo he llamado "mkdir yepalo", a partir de crear este directorio he comenzado a poner varios comandos como:
 - vagrant init ubuntu/jammy64: podemos crear un fichero con esta orden
 - vagrant up --provider=virtualbox: con este comando podemos levantar toda la infraestructura
 - vagrant ssh: con este comando podemos inciar session con la clave publica del host con ssh
 - ll /vagrant: aqui vemos todos los archivos/ficheros que hay en este directorio

Despues de utilizar los comandos que he dicho anteriormente tendremos que actualizar la maquina para que se guarde todo lo he hecho.
Para poder actualizar nuestra maquina podemos utilizar dos comandos que son los siguientes:
 - apt update
 - apt upgrade

Despues de actualizar la maquina he tenido que instalar varios servidores web que son los siguientes:
 - sudo apt install -y apache2
 - sudo apt install -y mysql-server
 - sudo apt install -y php libapache2-mod-php
 - sudo apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl
Y despues he tenido que reiniciar el servidor apache2 con el comando: "sudo systemctl restart apache2"

Despues de instalar varios servidores web, tendremos que configurar el MySQL y para poder acceder a la consola de MySQL habra que ejecutar el siguiente comando:
 - mysql

Cuando ya he entrado en la consola de mysql tendremos que crear una base de datos con el siguiente comando:
 - CREATE DATABASE bbdd;

Despues de crear la base de datos tendremos que crear un usuario con su contraseña, y tendremos que ejecutar este comando:
 - CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

Una vez creados la base de datos y el usuario, a este le tendremos que dar privilegios, y tendremos que ejecutar este comando: 
 - GRANT ALL ON bbdd.* to 'usuario'@'localhost';

Una vez que he creado la base de datos, el usuario y darle a este los privilegios tendremos que salirde la base de datos, y tendremos que utilizar este comando:
 - exit

Despues de entrar en la consola MySQL y configurarla tendremos que comprobar la conexión a la base de datos, y tendremos que utilizar este comando:
 - mysql -u usuario -p

Despues de todo lo anterior habra que crear un nuevo directorio para poder darle permisos al directorio que hay que crear, y tendremos que utilizar estos comandos:
 - cd /var/www/html

Y para darle permisos habra que utilizar estos comandos:
 - chmod -R 775 .
 - chown -R root:www-data .

Una vez hemos creado el directorio y le hemos añadido estos permisos, tendremos que entrar a la pagina oficial de nextcloud, tendremos que buscar arriba a la derecha donde hay tres linias y le tendremos que dar a "Get Nextcloud".
Despues de darle nos saldran varias opciones pero le tendremos que dar a "Nextcloud Server", despues habra que descargarse el archivo de NextCloud que sale "Get ZIP file"

Una vez descargado el archivo de NextCloud tendremos que poner el archivo en nuestro directorio en el cual hemos utilizado desde el principio.

Despues habra que utilizar el siguiente comando para tenerlo bien que es el siguiente:
 - sudo unzip latest.zip

Luego tendremos que buscar nuestra ip, y tendremos que utilizar este comando:
 - vagrant ssh

Para poder tener nuestra ip y buscarla en google y nos saldra la opcion de crer un usario y habra que poner nuestro nombre de base de datos, nuestro usuario y la contraseña que hemos puesto
