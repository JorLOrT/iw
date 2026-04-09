# 🚀 Laboratorio 02: Servidor Web Apache con Virtual Hosts en Docker

Este proyecto automatiza la implementación de un servidor web **Apache 2.4** sobre una imagen base de **Ubuntu 24.04**. El objetivo es gestionar múltiples sitios (Docentes, Alumnos y Administrativos) utilizando tanto subdirectorios como **Virtual Hosts** con sus respectivos alias.

---

### 📂 Estructura del Proyecto

Para que el despliegue sea exitoso, la carpeta `lab02` debe mantener esta jerarquía:

* 📂 **administrativos/** -> Contiene el `index.html` del área administrativa.
* 📂 **alumnos/** -> Contiene `index.html`, carpetas `css/`, `img/` y otros recursos.
* 📂 **profesores/** -> Contiene el `index.html` del área de docentes.
* 📄 **Dockerfile** -> Script de automatización de la imagen.
* 📄 **000-default.conf** -> Configuración de los Virtual Hosts y Alias.
* 📄 **README.md** -> Guía de uso (este archivo).

---

### 🛠️ Comandos Vitales de Docker

Usa estos comandos en tu terminal de Ubuntu (WSL) para gestionar el ciclo de vida del contenedor **container_mfloresl**.

#### 1. Construir la Imagen (Build)
Este comando lee el `Dockerfile` y prepara la imagen con Apache y tus archivos.
```bash
docker build -t imagen_mfloresl .
```
#### 2. Levantar y Correr el Contenedor (Run)
Crea el contenedor, lo nombra y mapea el puerto 8090 de tu máquina al puerto 80 interno.
```bash
docker run -d -p 8090:80 --name container_mfloresl imagen_mfloresl
```
#### 3. Detener el Proceso (Stop)
Pausa la ejecución del servidor sin eliminar los datos del contenedor.
```bash
docker stop container_mfloresl
```
#### 4. Limpiar y Eliminar (RM)
Elimina el contenedor por completo. Útil para reiniciar el proceso desde cero o liberar el nombre.
```bash
docker rm -f container_mfloresl
```
#### 5. Verificación de Estado (Consola)
```bash
docker ps -f name=container_mfloresl
```
| Sitio | URL Local |
| :--- | :--- |
|Profesores|http://localhost:8090/profesores/|
|Alumnos|http://localhost:8090/alumnos/|
|Administrativos|http://localhost:8090/administrativos/|
