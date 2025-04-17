# 🌐 Proyecto Kubernetes – Sitio Web Estático con Volumen Persistente

## ✅ Requisitos previos

Antes de comenzar, asegurate de tener instalado:

- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Git](https://git-scm.com/)
- Docker (si estás usando el driver por defecto en Windows)
- Un editor como VSCode

---

Hay dos repositorios involucrados:

### 📁 1. Contenido Web 
### 📁 2. Manifiestos


## Clona localmente el repo del sitio web
``` git clone https://github.com/Stefaneush/static-website.git website-content ```


## Haz lo mismo con el de manifests
``` git clone https://github.com/Stefaneush/k8-manifests manifests ```

#**⚠ Te recomiendo meter estas carpetas dentro de otra para tener todo más ordenado ⚠**


# 🚀Instrucciones para levantar el entorno

<ins> 1- abre una ventana de powershell como administrador y ejecuta el siguiente comando </ins>

``` minikube start --driver=docker --mount --mount-string="/ruta/a/tu/web:/mnt/web"  (Antes de ":/mnt/web" borra "/ruta/a/tu/web" y pon la ruta donde se encuentra la carpeta website-content que clonaste) ```

<ins> 2- Muevete hacia la carpeta manifests que clonaste </ins>

``` cd /ruta/a/tu/manifests ```

Desde el directorio aplica los manifiestos kubernetes

``` kubectl apply -f persistent-volume/ ```

``` kubectl apply -f deployment/ ```

``` kubectl apply -f service/ ```

<ins> 3- Verifica que esta todo corriendo </ins>

```kubectl get pods```

```kubectl get svc```

Si el pod website está en estado Running, ¡ya casi estás!, sino
espera unos segundos y vuelve a revisar

<ins> 4- Accede a la web local </ins>

```minikube service website-service```

Esto abrirá el navegador en el puerto donde se expone el sitio web. También podés acceder manualmente desde:

http://localhost:30080/


y listo 🎉 

