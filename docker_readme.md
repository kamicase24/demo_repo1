# Documentacion sobre Docker

Procesos y comandos necesarios para la utilización basica de Docker para _Quipu8_, incluye: Subir imagen a hub.docker.com, utilización de docker-compose, preparación de entorno de producción y desarrollo con Docker

>**Subir Imagen de Docker a un SCV de Docker:**

Este proceso se realizará asumiendo que se ha creado la imagen de docker y ha sido registrada correctamente.

1. Crear Repositorio en hub.docker.com, una vez creado del repositorio tener en cuenta el nombre dado al mismo, por con vención se suele dar el mismo nombre de la imagen creada, el SCV colocará el nombre de usuario mas un `/` al lado izquierdo, teniendo como nombre de repositorio:

        <usuario>/<nombre_repositorio>:<tag>

2. Una vez creado el repositorio, se debe logear desde la consola, ingresando usuario y contraseña del SCV:

        $ docker login

3. Logeado exitozamente se continua definiendo una variante de la imagen de Docker creada con el nombre dado por el repositorio, de la siguiente forma:

        $ docker tag <imagen>:<tag_opcional> <usuario>/<nombre_repositorio>:<tag>

4. Finalmente se envia la imagen de docker al repositorio:

        $ docker push <usuario>/<nombre_repositorio>:<tag>

>**Utilización de docker-compose**

Esta parte de la documentación esta enfocada al producto Odoov14 desarrollado por [Jesus Rojas]((https://github.com/kamicase24)), cubriendo unicamente las necesidades de un terno de producción y de desarrollo de Odoo v14 CE. Se tomara como punto de partida una estructura de docker-compose.yml ya diseñada con directorios y puertos configurados.

- Entorno de Producción:
    1. Una vez configurado el archivo `docker-compose.yml` y demas componentes necesarios, se ejecuta para instanciar los contenedores y odoo:

            $ docker-compose up -d

    2. Apagar, Reiniciar e Inicar el docker-compose:

            $ docker-compose stop # Detener
            $ docker-compose restart # Reiniciar
            $ docker-compose start # Iniciar

    3. Ver logs de Odoo:

            $ docker-compose exec -u root project tail -f <ruta_de_logs>

    4. Ingresar al contenedor de Postgres por medio de `psql`:

            $ docker-compose exec db psql -d <base_de_datos> -U odoo

- Entorno de Desarrollo:
    1. Una vez configurado el archivo docker-compose.yml y los demas componentes necesarios, se ejecuta para iniciar los contenedores:

            $ docker-compose up -d

    2. Apagar, Reiniciar e Iniciar el docker-compose:

            $ docker-compose stop # Detener
            $ docker-compose restart # Reiniciar
            $ docker-compose start # Iniciar

    3. Para Iniciar odoo:

            $ docker-compose exec project odoo -c</ruta/del/odoo.conf> 

        Si se desea actualizar un modulo de odoo:

            $ docker-compose exec project odoo -c</ruta/del/odoo.conf> -u <nombre_de_modulo>

        Lo mismo aplicaría para cualquier otro comando de consola de odoo que se desee utilizar.

    4. Ingresar al contenedor de Postgres por medio de `psql`:

            $ docker-compose exec db psql -d <base_de_datos> -U odoo
