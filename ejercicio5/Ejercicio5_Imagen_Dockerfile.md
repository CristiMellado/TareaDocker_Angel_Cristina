# Ejercicio 5 - Imagen con Dockerfile- Aplicación web.

> **Autores**: Ángel Villabrille Fernández, Cristina Mellado Malacara.
> 

## 1. Creación inicial del contenedor- Pasos hasta el borrado.

- Arranca un contenedor que ejecute una instancia de la imagen `php:7.4-apache` , que se
llame `web` y que sea accesible desde un navegador en el puerto `8000`.

```bash
docker run -d -p 8000:80 --name web 
-v C:\Users\crist\OneDrive\Escritorio\ejercicio5:/var/www/html php:7.4-apache

```

- Comprobamos que se creó el contenedor `web` y confirmamos que en la raíz del servidor web `/var/www/html` se encuentran los archivos `index.html` `estilos.css` y `script.php` .

```bash
docker exec -it web bash
ls
```

![image.png](image.png)

![image.png](image%201.png)

- Observamos la salida del `script.php` y de la página `index.html`  en el navegador.

![image.png](image%202.png)

![image.png](image%203.png)

- Detenemos el contenedor `web`

![image.png](image%204.png)

- Eliminamos el contenedor `web`

![image.png](image%205.png)

- Comprobamos que se eliminó el contenedor.

![image.png](image%206.png)

## 2. Bloque de código con el Dockerfile

```docker
FROM php:7.4-apache
EXPOSE 8000
COPY . /var/www/html/
RUN chown -R www-data:www-data /var/www/html \ 
&& chmod -R 755 /var/www/html
CMD ["apache2-foreground"]
```

![image.png](image%207.png)

## 3. Captura de pantalla y documento donde se vea el comando que crea la nueva imagen.

- Comando para creación de la imagen `apachecristiangel`

```bash
cd C:\Users\crist\OneDrive\Escritorio\ejercicio5
docker build -t apachecristiangel .
```

![image.png](image%208.png)

- Captura de pantalla donde se comprueba que se creó la imagen

![image.png](image%209.png)

![image.png](image%2010.png)

## 4. Captura de pantalla donde se vea la imagen subida a tu cuenta de Docker Hub.

- Docker requiere que cada imagen tenga un tag adecuado. Lo que haces con el `docker tag` es crear un alias para que puedas subir esa misma imagen, pero con un nombre y tag adecuado para Docker Hub.
Para ello utilizamos el siguiente comando.
    
    ```bash
    docker tag apachecristiangel cristimellado/apachecristiangel:latest
    ```
    

- En la sección `images`  ahora nos aparece el nuevo tag creado donde podremos hacer push a Docker Hub.

![image.png](image%2011.png)

- Comprobamos que se subió exitosamente la imagen ya que nos aparece en el buscador de Docker Hub

![image.png](image%2012.png)

## 5. Captura de pantalla donde se vea la bajada de la imagen por parte de otra persona del grupo y la creación de un contenedor.

```bash
docker pull cristimellado/apachecristiangel
docker images
docker run --name practicadocker -d -p 8080:80 cristimellado/apachecristiangel
```

![image.png](image%2013.png)

![image.png](image%2014.png)

## 6. Captura de pantalla donde se ve el acceso al navegador con el sitio web.

![image.png](image%2015.png)

![image.png](image%2016.png)