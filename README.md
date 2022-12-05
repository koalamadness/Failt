
# Desplegar una aplicación localmente, en Docker y en Kubernetes

En este tutorial se muestra cómo desplegar una simple aplicación de buscar información acerca de películas como sus actores, título, directores, duración, fecha de estreno y demás. Se explicará la arquitectura y componentes de K8s utilizados para esta entrega. Al final viene una presentación con vídeos de prueba y despliegue. 

## Flow General
![Flow](https://user-images.githubusercontent.com/22554053/205640395-ea5ef369-8474-4b89-a260-4e3a98df42ff.PNG)
![Captura](https://user-images.githubusercontent.com/22554053/205641133-d7084781-3c96-4d59-9f84-7c90016a8f12.PNG)

1. El usuario accede a la aplicación a través de la interfaz web. El usuario mete un nombre de película en el buscador.
2. La aplicación React is renderizada al usuario al acceder.
3. La aplicación llama a la API OMBb y recibe un objeto JSON de la respuesta para mostrar al usuario.

# Pasos

## Requisitos previos: 
1. Se debe obtener una clave de API de la API de OMDb para obtener una respuesta de la API. Se inserta su clave de API en '/src/actions/index.js' en la línea 42.

2. Crear una variable de entorno para su nombre de usuario docker
```
$ export docker_username="TU_USUARIO_DOCKER"
```

## Correr localmente

### 1. Clone the repo

Se clona el repositorio localmente. En una terminal, ejecutar:

```
$ git clone https://github.com/koalamadness/ProyectoTaF2022B
```

### 2. Correr la aplicación
1. Instalar Node.js
2. Ejecutar los siguientes comandos en una terminal:

```
$ npm install

$ npm run build-css

$ npm run start
```

## Correr la aplicación mediante Docker


## Requisitos previos:
1. Crear una cuenta Docker

2. Instalar Docker CLI

3. Recuperar y guardar el ID de usuario de Docker

### 1. Construir la imagen

En una terminal, ejecutar:
```
$ docker build -t $docker_username/koalamadness/ProyectoTaF2022B .
```

Se puede revisar que está la imagen con:

```
$ docker images
```

### 2. Correr la imagen 

En una terminal, ejecutar:

```
$ docker run -p 3000:3000 -d $docker_username/koalamadness/ProyectoTaF2022B
```

Se puede acceder ahora con http://localhost:3000

## Correr la aplicación en Kubernetes

## Requisitos previos:
1. Instalar kubectl

2. Acceder a tu cuenta docker

### 1. Pushear imagen a cuenta de Docker Hub

De esta manera el archivo yaml del Deployment puede acceder a la imagen, en la terminal correr:

```
$ docker push koalamadness/ProyectoTaF2022B
```
### 2. Aplicar el arhivo yaml

Correr el siguiente comando en terminal:

```
kubectl apply -f deployment.yaml
```

Para revisar cuántos pods están corriendo:
```
kubectl get pods
```
## Presentación

https://docs.google.com/presentation/d/1325yoQ2Haffzx0fGLw-kLgBhacoX9xw-PRf_wqctceg/edit?usp=sharing
