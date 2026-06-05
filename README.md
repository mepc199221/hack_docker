# SOCIAL OPLESK
### 🏴‍☠️ HACKS 
<br/>
## ⚡️ Hack de Docker ⚡️## 
# debes tenerr docker engine en wsl en caso de emplear windows, ideal sobre debian / ubuntu / fedora.

**Requisitos previos**
<br/>
- docker engine enlace:  https://docs.docker.com/engine/install/

```diff
- NOTA HACER LAS PRÁCTICAS MEDIANTE LA CONSOLA - TERMINAL  
```
|Hacks | Details | 
|----------|---------|
| H-1      | Enviar |
| H-2      | Enviar|
| H-3      | Hacer | 
| H-4      | Extraer |
| H-5      | Enviar  |
| H-6      | Clonando|
| H-7      | Eliminar | 
| H-8      | Volver |
<br/> 

## 🏆 H-1(aplicar la image optima)

1. Crear un directorio llamado docker_1

2. Dentro del directorio docker_1 crear el archivo Dockerfile

3. Debes crear el Dockerfile sin elegir un FROM de image incorrecto
   
4. las versiones slim siempre se deben seleccionar sobre una version latest
   
```
#❌
FROM ubuntu:latest

# ✅ Bien
FROM ubuntu:24.04-slim
--------------------------

FROM ?

RUN apt update -y && apt install nginx -y

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```


## 🏆 H-2(usar apt con el estilo correcto en docker)
1. Crear un directorio llamado docker_2

2. Dentro del directorio docker_2 crear el archivo Dockerfile

3. Debes crear el Dockerfile con una image de ubuntu correcta e instalar nginx. 
   
4. apt está diseñado para humanos: Es un comando interactivo para la terminal del día a día.<br/> 
   apt-get está diseñado para scripts y automatización: Es una herramienta de "bajo nivel" mucho más estable y predecible.
   
5. apt-get clean: borra los archivos .deb descargados que ya se instalaron.

6. --no-install-recommends y --no-install-suggests:<br/>
   Estas banderas le dicen: "Instala solo lo estrictamente necesario para que curl funcione".<br/>
   Esto te puede ahorrar cientos de megabytes de basura.

7. rm -rf /var/lib/apt/lists/* <br/>
   Elimina los índices de los repositorios (las listas de qué paquetes existen).    
   
```
# ❌ Mal (crea 3 capas)
RUN apt update
RUN apt install -y curl
RUN rm -rf /var/lib/apt/lists/*

# ✅ Bien (1 sola capa)
RUN apt-get update && \
    apt-get install -y --no-install-recommends --no-install-suggests curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
--------------------------

FROM ?

RUN ?

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```


## 🏆 H-3(Usuario no rott)

1. Crear un directorio llamado docker_3

2. Dentro del directorio docker_3 crear el archivo Dockerfile

3. Debes crear el Dockerfile sin elegir un FROM de image incorrecto
   
4. las versiones slim siempre se deben seleccionar sobre una version latest
   
```
# ✅ Crea y usa usuario no root
RUN useradd -m -u 1000 appuser
USER appuser
WORKDIR /home/appuser/app
--------------------------

FROM ?

RUN apt update -y && apt install nginx -y

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```





<br/>
<div style="text-align: center">Social Oplesk</div>
