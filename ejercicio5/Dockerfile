FROM php:7.4-apache

#Configurar el puerto en el que se ejecutará Apache
EXPOSE 8000

#Copiar los archivos del proyecto al directorio raíz del servidor web
COPY . /var/www/html/

#Dar permisos adecuados a los archivos
RUN chown -R www-data:www-data /var/www/html \ 
&& chmod -R 755 /var/www/html

#Iniciar Apache en primer plano
CMD ["apache2-foreground"]