# Ejercicio 3 - Contenedores en red: Adminer y MariaDB

> **Autores**: Ángel Villabrille Fernández, Cristina Mellado Malacara.
> 

# 1. Crea una red bridge `redbd`

```bash
docker network create redbd
```

![image.png](imagenes/image.png)

# 2. Crea un contenedor con una imagen de `mariaDB` que estará en la red `redbd`

- Este contenedor se ejecutará en segundo plano, y será accesible a través del puerto `3306`. (Es necesario definir la contraseña del usuario `root` y un volumen de datos persistente).

```bash
docker run -d --name mariadb_container --network redbd -e 
MYSQL_ROOT_PASSWORD=docker -v mariadb_data:/var/lib/mysql -p 
3306:3306 mariadb:latest
```

![image.png](imagenes/image%201.png)

- Comprobamos que el contenedor está en funcionamiento:

```bash
docker ps
```

![image.png](imagenes/image%202.png)

- Lo podemos ver también desde Docker Desktop:

![image.png](imagenes/image%203.png)

# 3. Crear un contenedor con `Adminer` que se pueda conectar al contenedor de la BD

```bash
docker run -d --name adminer_container --network redbd -p 8080:8080 adminer:latest
```

### **Explicación del comando:**

1. `docker run`: Ejecuta un nuevo contenedor de Docker.
2. `d`: Ejecuta el contenedor en segundo plano.
3. `-name adminer_container`: Nombra el contenedor como `adminer_container`.
4. `-network redbd`: Conecta el contenedor a la misma red (`redbd`) que el contenedor de MariaDB.
5. `p 8080:8080`: Mapea el puerto 8080 del contenedor al puerto 8080 de tu máquina local.
6. `adminer:latest`: Utiliza la imagen oficial más reciente de Adminer.

![image.png](imagenes/image%204.png)

- Comprobamos que el contenedor está en ejecución:

![image.png](imagenes/image%205.png)

![image.png](imagenes/image%206.png)

# 4. Desde la interfaz gráfica, crear una base de datos y una tabla en el servidor de base de datos

- Rellenamos los campos del formulario y accedemos:

![image.png](imagenes/image%207.png)

![image.png](imagenes/image%208.png)

- Ahora procedemos a crear la base de datos:

![image.png](imagenes/image%209.png)

- Le ponemos un nombre y creamos la base de datos:

![image.png](imagenes/image%2010.png)

- Ahora creamos una tabla:

![image.png](imagenes/image%2011.png)

- A esta tabla la llamaremos `usuarios` y procedemos a insertarle valores como su `id` , `nombre`  y `correo` . Después haremos click en ‘guardar’.

![image.png](imagenes/image%2012.png)

- Aquí podemos ver la tabla `usuarios` creada de manera correcta con todos sus campos:

![image.png](imagenes/image%2013.png)
