# Práctica formativa obligatoria N° 3 - Kubernetes

Este repositorio contiene los archivos y la configuración para la **Práctica formativa obligatoria N° 3** de la materia **Seminario DevOps**.

El objetivo de esta práctica es familiarizarse con la instalación, uso y manejo de Kubernetes (Minikube), incluyendo la creación de *deployments*, *services*, y el despliegue de una aplicación personalizada.

## Contenido del repositorio

* **`/src/index.php`**: Código fuente de la aplicación PHP simple que muestra un mensaje de bienvenida y el *hostname* del Pod.
* **`Dockerfile`**: Archivo de instrucciones para construir la imagen de contenedor de la aplicación PHP.
* **`deploy-mi-app-php.yaml`**: Archivo de manifiesto (YAML) para el *Deployment* de Kubernetes. Este archivo contiene la configuración necesaria para desplegar la aplicación, incluyendo la corrección `imagePullPolicy: Never` para solucionar el error `ImagePullBackOff` con imágenes locales.
* **`/capturas`** (Opcional): Carpeta con capturas de pantalla que documentan el proceso, los comandos ejecutados y los errores encontrados.
* **`DevOps_PFO3_Kubernetes-RACHICH_Alejandra_Lorena.pdf`**: Informe final del trabajo.
## Resumen del proceso

El proyecto sigue dos partes principales:

### Parte I: Exploración de Minikube

1.  **Instalación y configuración:** Se instaló Minikube con el *driver* de VirtualBox. Se solucionaron problemas comunes de virtualización (`PROVIDER_VIRTUALBOX_NOT_FOUND` y `HOST_VIRT_UNAVAILABLE` por conflicto con Hyper-V).
2.  **Gestión de cargas de trabajo:** Se utilizaron comandos como `kubectl get po -A` para explorar los componentes del sistema.
3.  **Dashboard:** Se habilitó y utilizó el Dashboard de Kubernetes.
4.  **Deploy de prueba:** Se desplegó una imagen de prueba (`echo-server`) y se expuso usando un *Service* de tipo `NodePort` y `port-forward`.

### Parte II: Despliegue de aplicación propia

1.  **Creación de imagen:** Se construyó una imagen de Docker personalizada (`mi-app-php`) a partir del `Dockerfile`.
2.  **Conexión a Minikube:** Se utilizó `minikube docker-env` para construir la imagen directamente dentro del entorno de Minikube.
3.  **Generación de YAML:** Se generó el archivo `deploy-mi-app-php.yaml` usando el comando `kubectl create --dry-run`.
4.  **Resolución de error:** Se solucionó el error `ImagePullBackOff` al aplicar el YAML, especificando `imagePullPolicy: Never` para que Kubernetes utilizara la imagen local.
5.  **Despliegue final:** Se aplicó el YAML corregido y se expuso la aplicación PHP mediante un *Service*, accediendo a ella exitosamente desde el navegador.