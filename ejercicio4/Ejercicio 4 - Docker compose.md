# Ejercicio 4 - Docker compose

> **Autores**: Ángel Villabrille Fernández, Cristina Mellado Malacara.
> 

## Desplegar la aplicación `htop` usando docker-compose

## 1. Captura de pantalla y documento donde se vea el fichero `docker-compose.yaml` .

- Crear el archivo `docker-compose.yaml`

![image.png](image.png)

```docker
version: '3'
services:
  htop:
    image: ubuntu:latest
    container_name: htop-container
    stdin_open: true
    tty: true
    command: bash -c "apt-get update && apt-get install -y htop && htop"
```

- `version: '3'`: Define la versión de `docker-compose` utilizada.
- `services`: Contiene los servicios que se van a ejecutar dentro del contenedor.
- `htop`: Nombre del servicio.
- `image: ubuntu:latest`: Usa la última versión de Ubuntu como base del contenedor.
- `container_name: htop_container`: Define el nombre del contenedor.
- `stdin_open: true`: Mantiene la entrada estándar abierta para la interacción.
- `tty: true`: Habilita un terminal interactivo.
- `command`: Ejecuta una secuencia de comandos al iniciar el contenedor:
    1. `apt-get update`: Actualiza los paquetes de Ubuntu.
    2. `apt-get install -y htop`: Instala `htop`.
    3. `htop`: Ejecuta `htop` para mostrar el monitoreo del sistema.
    
- Construir y ejecutar el contenedor:  Una vez creado el archivo `docker-compose.yaml`, iniciamos el contenedor con el siguiente comando:

```bash
docker-compose up
```

![image.png](image%201.png)

## 2. Captura de pantalla donde se vea la aplicación funcionando.

- Ejecución de la aplicación `htop`

```bash
docker exec -it htop-container htop
```

- Evidencia de funcionamiento.

![image.png](image%202.png)

## 3. Explicar brevemente cómo funciona esta aplicación y que hace.

`htop` es una herramienta interactiva que muestra el uso de recursos del sistema en tiempo real. Esta aplicación es útil para monitorear el rendimiento del sistema y administrar tareas de manera eficiente. Proporciona información detallada sobre:

- Uso de CPU y memoria.
- Procesos en ejecución.
- Prioridad y estado de los procesos.
- Posibilidad de filtrar y gestionar procesos.

Parámetros:

- **PID:** número que identifica al proceso.
- **USER:** usuario que ejecutó el proceso.
- **PRI:** prioridad.
- **NI:** nivel de prioridad.
- **VIRT:** cantidad de memoria virtual utilizada.
- **RES:** memoria RAM en megabytes.
- **SHR:** memoria compartida utilizada.
- **S:** estado del proceso.
- **CPU%:** porcentaje de CPU utilizada.
- **MEM%:** porcentaje de memoria RAM utilizada.
- **TIME+:** tiempo de vida del proceso.
- **Command:** comando utilizado para lanzar el proceso.

Controles básicos dentro de `htop` :

- `F1` → Ayuda.
- `F2` → Configuración (ajustar colores y columnas).
- `F3` → Búsqueda de procesos.
- `F4` → Filtrar procesos.
- `F5` → Modo en árbol (estructura jerárquica de procesos).
- `F6` → Ordenar por diferentes columnas.
- `F9` → Finalizar un proceso.
- `F10` → Salir.