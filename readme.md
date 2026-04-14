1. Configura tu .env.
2. ```docker compose up``` Para crear el container con los servicios requeridos.
3. Espera y verifica que se haya creado el proyecto.
4. ```docker compose exec php php artisan migrate``` Para migrar la base de datos. (Si es necesario)

- ¿Que hace el proyecto?
Para empezar se configura un contenedor los servicios de PHP, MySQL y Nginx con docker-compose.yml. Dentro de PHP se encuentra un Dockerfile que se encarga de instalar las dependencias del sistema a utilizar, extensiones de PHP necesarias y descarga la ultima version de composer para posteriormente establecer el directorio de trabajo y ejecutar el script init.sh que se encarga de crear el proyecto Laravel, dentro de este init.sh, verifica si ya existe el proyecto Laravel comprobando si existe un archivo 'artisan', en caso de que no exista, crea el proyecto. Posteriormente configura el .env del proyecto, tomando los datos del .env de la raiz y reemplaza la configuracion con sed y posteriormente las descomenta, para finalizar establece los permisos necesarios y ejecuta php-fpm.
Para el caso del servicio de MySQL, este se configuro en el puerto default (3306).
Se utiliza Nginx y su respectivo default.conf para renderizar la aplicacion web.