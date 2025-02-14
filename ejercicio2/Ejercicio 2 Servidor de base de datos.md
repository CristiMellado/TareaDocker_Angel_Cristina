# Ejercicio 2: Servidor de base de datos

> **Autores**: Ángel Villabrille Fernández, Cristina Mellado Malacara.
> 

## 1.Abre Docker Desktop. Busca `mariadb` en la selección de imágenes. Selecciona la imagen oficial. Descárgala si no la tienes.

- Nos situamos en la pestaña `Docker hub`  y buscamos la imagen oficial en el buscador.

![image.png](imagenes/image.png)

- Seleccionamos el botón pull para descargar la imagen. Se puede observar que se bajó correctamente.

![image.png](imagenes/image%201.png)

- Nos dirigimos a nuestra pestaña `images` para hacer la comprobación de que se encuentra la imagen en la lista.

![image.png](imagenes/image%202.png)

## 2. Despliega un contenedor utilizando esta imagen:

     *Características:*

    *Nombre del contenedor `bbdd`* 

    *Puerto: 3306 - debe poder conectarse externamente*

    *Utiliza un volumen llamado `datos-mariadb`* 

    *Usa las variables de entorno necesarias para que el usuario `root` tenga la password `root` , la base*       

    *de datos por defecto sea `base` , y se cree un usuario `daw` , conpassword `daw` .*

- Comprobamos la ruta para proceder a introducir los datos en nuestro contenedor.

![image.png](imagenes/image%203.png)

- Seleccionamos la pestaña `volumes` y hacemos click en el botón create.

![image.png](imagenes/image%204.png)

- Configuramos los datos.

![image.png](imagenes/image%205.png)

- Comprobamos en Docker Desktop que se creó el contenedor y se está haciendo uso del volumen `datos-mariadb` .

![image.png](imagenes/image%206.png)

![image.png](imagenes/image%207.png)

## 3. Arranca el contenedor

- Pulsamos el botón de arrancar y comprobamos que funcionó con éxito

![image.png](imagenes/image%208.png)

## 4. Accede a la base de datos usando una herramienta gráfica, como, por ejemplo `dbeaver` .Conéctate con el usuario `daw` . Crea una base de datos y alguna tabla.

1. Accedemos a `dbeaver` y pulsamos en nueva conexión.

![image.png](imagenes/image%209.png)

- Seleccionamos nuestra base de datos `mariadb`

![image.png](imagenes/image%2010.png)

b. Me conecto exitosamente con el usuario `daw` .

![image.png](imagenes/image%2011.png)

![image.png](imagenes/image%2012.png)

c. Creamos una base de datos y una tabla.

- Tenemos que otorgarle permisos al usuario `daw` para que pueda crear base de datos y tabla, eso lo hacemos desde nuestro usuario `root` .

![image.png](imagenes/image%2013.png)

- Ahora que tenemos los permisos, volvemos a nuestro usuario `daw` , y creamos la base de datos `mi_nueva_base.`

```sql
CREATE DATABASE mi_nueva_base;
```

![image.png](imagenes/image%2014.png)

- Creamos una tabla llamada `usuarios`  y comprobamos que se creó correctamente.

```sql
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    edad INT
);
```

![image.png](imagenes/image%2015.png)

![image.png](imagenes/image%2016.png)

## 5. Borra el contenedor.

![image.png](imagenes/image%2017.png)

![image.png](imagenes/image%2018.png)

## 6. Ver en Docker Desktop que el volumen que contiene los datos no se ha borrado.

- En la imagen se puede observar que no se eliminó el volumen `datos-mariadb`

![image.png](imagenes/image%2019.png)

## 7. Crear otro contenedor con un servidor de base de datos que use el mismo volumen. Llamar al contenedor `bbdd-2` . Comprobar que la base de datos y la tabla creada anteriormente siguen ahí.

- Creamos el nuevo contenedor

![image.png](imagenes/image%2020.png)

- Comprobamos que arrancó correctamente.

![image.png](imagenes/image%2021.png)

- Se comprueba que la base de datos y la tabla creada anteriormente siguen ahí.

![image.png](imagenes/image%2022.png)

## 8. Intenta borrar la imagen de `mariadb` ¿Qué sucede?

- Al intentar eliminar la imagen `mariadb` nos pone el siguiente mensaje:
    
    *Error al eliminar: La imagen mariadb:lts-ubi9 está en uso. Elimina el contenedor que la está usando y vuelve a intentarlo.*
    
    Esto sucede porque Docker no permite borrar una imagen si hay algún contenedor que la está utilizando. Para poder eliminarla, primero es necesario detener y borrar todos los contenedores que dependen de esa imagen.
    

![image.png](imagenes/image%2023.png)

## 9. Borra todo, volumen, imagen y contenedor.

- Eliminamos primero el contenedor: Para que posteriormente nos permita eliminar el volumen y después la imagen.

![image.png](imagenes/image%2024.png)

- Eliminamos el volumen.
    
    ![image.png](imagenes/image%2025.png)
    

- Eliminamos la imagen.

![image.png](imagenes/image%2026.png)
