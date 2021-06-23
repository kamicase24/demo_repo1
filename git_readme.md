# Pasos para crear un nuevo repositorio de modulos de Odoo

1. Ubicarse en el directorio que se desea hacer repositorio

        $ cd ~/nuevo_repositorio

2. Una vez creado o agregados los archivos y directorios que poseerá el repositorio se procede a crear un nuevo repositorio en el Sistema de Control de Versiones de su agrado.

3. Con el repositorio creado se debe ejecutar los siguientes comandos para agregar todos los archivos y directorios, y despues hacer commit y escribir un mensaje, en este caso el commit y mensaje inicial.

        $ git add .
        $ git commit -m "[INIT] Commit Inicial"

4. Escrito el commit inicial, se sincroniza un nuevo origen con el repositorio creado.

        $ git add <nombre_del_origen> <link_de_repositorio>

5. Finalmente se hace push de los cambios.

        $ git push origin master

# Crear ramas de Producción y Desarrollo
Una vez creado y sincronizado el repositorio es recomendable, por buenas practicas y para el mantenimiento ideal del producto es tener distintas ramas de trabajo, la master, que representaría el producto estable, la de producción que tendria la versión actualizada del producto y la de desarrollo, donde se estaria haciendo las modificaciones y todo lo que ello implica. Si bien no es obligatorio este paso, por convención se recomienda tener esta estructura. 

- Crear una nueva rama:

        $ git -b <nombre_nueva_rama>

- Subir una rama creada al repositorio

        $ git push --set-upstream <nombre_del_origen> <nombre_nueva_rama>

- Cambiar entre ramas:

        $ git checkout <rama_a_la_cual_cambiar>