# Practica 3.2 3.4

## Introduccion
 En la práctica 3.2, vamos a clonar un repositorio, y inicializar un proyecto Node.js. Luego en la páctica 3.4 vamos desplegar nuestro proyecto en remoto mediante la plataforma Netlify de dos formas, la primera usando el netlify deploy y otra es enlazando netlify con github.

## Práctica 3.3:
### Clonar repositorio:
Primero vamos a clonar el repositorio ```https://github.com/StackAbuse/color-shades-generator``` usando el comando de git:

    git clone https://github.com/StackAbuse/color-shades-generator

Luego nos metemos en la carpeta clonada:

    cd color-shades-generator

### Node:
Instalamos el paquete de Node.js usando ```npm``` (Node Package Manager):

    npm install

![](assets/02_npm_install.png)

Y ahora ejecutmos el comando:

    npm run start

nos sale el error: 

    sh: 1: nodemon: not found

Este error indica que no esta instalado el nodemon.

Para solucionarlo hay que instala el ```nodemon``` que es una herramienta muy útil en el desarrollo de aplicaciones Node.js, y su propósito principal es automatizar el proceso de reiniciar la aplicación cada vez que detecta cambios en los archivos del proyecto.

![](assets/03_install_nodemon_locally.png)

![](assets/04_install_nodemon_globally.png)


## Practica 3.4:
En esta practica vamos a desplegar nuestro proyecto ```Node.js``` usando ```Netlify```:

### Habilitamos ```SSH```:
Para poder controlar el servidor desde nuestra maquina anfitriona:

![](assets/05_login_ssh.png)

### Nos conectamos con el servidor:
Y ahora vamos a conectarnos con el servidor ejecutando el comando:

    ssh <nombre-servidor>@<IP-SERVIDOR>

![](assets/06_connection_ssh_powershell.png)

### Crear app:
Creamos una aplicacion con la estructura siguiente:

    |__ head.html <br>
    |__ tail.html <br>
    |__ aplicacion.js <br>

![](assets/07_crear_app.png)

### Crear el package JSON:

![](assets/08_npm_init.png)

### Y desplegamos la app en local en el puerto 8080:

![](assets/09_deploy_app.png)

Visualizamos la pagina desplegada:

![](assets/10_access_deployed_web.png)

### Despliegue NETLIFY:
Ahora procedemos al despliegue en ```NETLIFY```

#### Nos clonamos el repositorio necesario:

    git clone https://github.com/StackAbuse/color-shades-generator

![](assets/11_createntliftydir_clonerepo.png)

#### Nos registramos en ```NETLIFY```:

![](assets/12_registro_netlify.png)

#### Instalacion y login:

Nos instalamos NETLIFY y creamos una variable de entorno que tendrá el token generado para que podamos logearnos sin usar un entorno grafico ya que en un escenario real todo se manejará mediante SSH.

![](assets/13_install_netlify_create_token.png)

Nos logeamosÑ

![](assets/14_loging_in.png)

#### Build & Deploy

Ejecutamos el siguiente comando para generar el directorio ```build``` que se va a desplegar.

![](assets/15_npm_build.png)

![](assets/16_netlify_deploy.png)


Visualizamos la pagina desplegada mediante NETLIFY:

![](assets/17_ver_pagina_desplegada.png)

### Despliegue NETLIFY enlazando un repositorio de GitHub:

#### Borramos la web desplegada antes:

![](assets/18_borrar_elsite.png)

#### Nos descargamos el zin que tiene la nueva aplicacion ```main.zip```:   

    wget https://github.com/StackAbuse/color-shades-generator/archive/refs/heads/main.zip

Lo descomprimimos en la carpeta practica3.4

![](assets/19_descargarzip_descomprimirlo.png)

#### Crear Repo

Creamos un repositorio en nuestra cuenta de GitHub.
Hacemos el primer commit y subimos el proyecto:

![](assets/20_gitinit_add_commit.png)

![](assets/21_gitpush.png)

### Enlazar con NETLIFY

Enlazamos nuestro repositorio de GitHub con la plataforma NETLIFY para que cada vez que se hace un push, despliega los cambios.

1. Le damos a import from Git

![](assets/22_import_git.png)

2. Elegimos la opcion Github

![](assets/23_GitHub_.png)

3. Rellenamos los campos necesarios y le damos a desplegar

![](assets/24_deploy_practica_button.png)

Y ya nuestra aplicacion se desplegará.

para probar l auto despliegue de la app.

Miramos el archivo robots.txt que está en public.

![](assets/25_robots.txt.png)

Lo modificamos poniendo /yahya-limouni/
y verificamos si se ha desplegado correctamente

![](assets/26_robots_modificado.png)
