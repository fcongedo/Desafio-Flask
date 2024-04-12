## Paso 0: Instalación de Herramientas/Entorno de trabajo 

 Este `README` proporciona instrucciones básicas para la instalación de herramientas necesarias y la configuración de una máquina virtual con Vagrant con las herramientas necesarias para el desafio (docker, minikube, kubectl)

## Configuración de Vagrant :

En el directorio de tu proyecto, encontrarás una carpeta llamada "Vagrant". Esta carpeta contiene la configuración necesaria para levantar una máquina virtual.

1. **Iniciar la Máquina Virtual**: Ejecuta el siguiente comando dentro del directorio "Vagrant":
   ```bash
   vagrant up
   ```
2. **Conexión SSH**:  Para conectarte a la máquina virtual por SSH, utiliza el siguiente comando:
   ```bash
   vagrant ssh
   ```
3. **Túnel a la Máquina Host**: Puedes crear un túnel desde la máquina virtual a tu máquina host para acceder a servicios que se ejecuten en la VM desde el host. Utiliza el siguiente comando para configurar el túnel:
   ```bash
   vagrant ssh -- -L 5000:localhost:5000
   ```

## Paso 1: Dockerfile

 Para construir la imagen de docker podremos hacerlo de forma manual descargando el codigo y haciendo un docker build o utilizar la github action ya configurada para que en cada cambio que hagamos en algun archivo del directorio Docker, se ejecute y haga el proceso de construir la imagen y subirla a dockerhub, es importante haber activado Github Actions y configurado los secretos para subir la imagen a dockerhub.

## Uso de docker

1. **Primero debemos descargar la imagen manualmente**: Para descargar la imagen alojada en un repositorio de dockerhub, debemos ejecutar el siguiente comando:
   ```bash
   docker pull fcongedo/app-flask:1
   ```
   
2. **Crear la Imagen de Docker Manualmente**:Para crear una imagen de Docker de manera manual, ejecuta el siguiente comando, que mapea el puerto 5000 de la máquina virtual al puerto  del contenedor. Asegúrate de cambiar los nombres y versiones según tu configuración:
   ```bash
   docker run -d -p 5000:5000 --name mi-app-flask fcongedo/app-flask:1 
   ```

3. **Crear la Imagen de Docker con Docker Compose**: Dirígete al directorio /desafio-flask/Docker-compose en la máquina virtual y ejecuta el siguiente comando para crear la imagen utilizando Docker Compose
   ```bash
   docker compose up -d
   ```
4. **Verificar su funcionamiento**: utilizando un tunel de vagrant o desde curl localhost:5000
   ```bash
   vagrant ssh -- -L 5000:localhost:5000
   ```

## Paso 2: Kubernetes

0. **Iniciar Minikube:** Ejecuta el siguiente comando para iniciar minikube:

   ```bash
   minikube start
   ```
 Para este paso es tan simple como verificar estar conectados a nuestro cluster de kubernetes (poder ejecutar un kubectl get pods -A sin errores) y asi crear nuestros recursos dentro del directorio Kubernetes con el siguiente comando (asegurarse de estar dentro del directorio desafio-flask):

1. **Crear Recursos en Kubernetes:** Asegúrate de estar dentro del directorio `desafio-flask` y ejecuta:
    ```bash
    kubectl apply -f Kubernetes/ns.yaml
    kubectl apply -f Kubernetes/deployment.yaml
    ```

2. **Exponer la Aplicación:** Utiliza port-forward para exponer la aplicación:
    ```bash
    kubectl port-forward deployment/app-flask 8080:5000 -n prueba-flask
    ```

3. **Verificar su funcionamiento**: utilizando un tunel de vagrant o desde curl localhost:5000 (el tunel recordar hacerlo desde otra terminal de vagrant)

   ```bash
   vagrant ssh -- -L 5000:localhost:8080
   ```


## Readme de la aplicacion:   

[![Issues](https://img.shields.io/github/issues/jainamoswal/Flask-Example?style=for-the-badge&color=green)](https://github.com/jainamoswal/Flask-Example/issues)
[![Forks](https://img.shields.io/github/forks/jainamoswal/Flask-Example?style=for-the-badge&color=green)](https://github.com/jainamoswal/Flask-Example/fork)
[![Stars](https://img.shields.io/github/stars/jainamoswal/Flask-Example?style=for-the-badge&color=green)](https://github.com/jainamoswal/Flask-Example)
[![Size](https://img.shields.io/github/repo-size/jainamoswal/Flask-Example?style=for-the-badge&color=green)](https://github.com/jainamoswal/Flask-Example)
[![Contributors](https://img.shields.io/github/contributors/jainamoswal/Flask-Example?style=for-the-badge&color=green)](https://github.com/jainamoswal/Flask-Example)

---
| 🗺 Routes 🗺 | 🚧 Usage 🚧 | 
| :-: | :-: |
| `/api` | For API. |
| `/file` | For streaming files. |
| `/dl` | For downloading a file. |
| `/<name>` | Says Hello! 🤚 |
| `/code` | For redirection. |
| `/cookies/set` | For setting cookies. |
| `/cookies/get` | For retrieving cookies. |
| `/cookies/del` | For deleting cookies. |
| `/headers` | For working with Headers. |
| `/ip` | For location based user interface. |
| `/q` | For getting the parameters passed with URL. |

---
## How to use this ? 
- Don't be scared 😬 by watching a ton files, Most are just to configure the deploy settings. 🏋️‍♂️
- Star this repository. ⭐️
- Make a new repository by clicking [here.](https://github.com/jainamoswal/Flask-Example/generate) 👲
- Go to [modules folder](modules). 📂
- Add or modify the plugins. ✏️
- Crawl any hosting provider. 🕷
- Link your (Newly generated 🍽) repository with it. 🔗
- Deploy it there or replace your username [here](#deployments) and deploy using buttons. 🚀 
- And done. ✅

#### OR 
- Just [deploy](#deployments) this repository for testing. 🧪

### Deployments



<details><summary>Heroku.com 🚀</summary>
<br>

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/jainamoswal/Flask-Example)
</details>
 
<details><summary>Replit.com 🌀</summary>
<br>

[![Run on Repl.it](https://repl.it/badge/github/jainamoswal/Flask-Example)](https://repl.it/github/jainamoswal/Flask-Example)
</details>

<details><summary>Zeet.co 💪</summary>
<br>
 
[![Deploy](https://deploy.zeet.co/Flask-Example.svg)](https://deploy.zeet.co?url=https://github.com/jainamoswal/Flask-Example)
</details>

#### Adding some other hosting providers too 🤧 soon.

prueba


---

<details>
<summary>Support ground. ⛹️‍♂️🤝</summary>
<br>  
  
- [![Channel](https://img.shields.io/badge/Telegram-Channel-green?style=for-the-badge&logo=telegram)](https://t.me/J_projects)
- [![Support](https://img.shields.io/badge/Telegram-Group-green?style=for-the-badge&logo=telegram)](https://t.me/J_projects_chat)
</details>



<details>
<summary>Donate. 💰💷</summary>
<br>  
  
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/jainamoswal) 
[![paypal](https://www.paypalobjects.com/webstatic/en_AU/i/buttons/btn_paywith_primary_s.png)](https://paypal.me/joswal105)
</details>



## License 
### [Flask-Example](https://github.com/jainamoswal/Flask-Example) is licensed under [IDC v1](https://github.com/jainamoswal/idc) or later.
[![idc](https://telegra.ph/file/e52d9b970e6967b3d6b6a.png)](https://github.com/jainamoswal/idc)

`This LICENSE is widely used when the owner of the content does not care what you do from the source.
No one can appeal copyright or DMCA takedown notices. The end user is free to do anything from the content. Nor the owners or distributors are affiliated with any crime done by the content of the LICENSE. `
