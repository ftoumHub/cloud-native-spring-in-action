# Catalog Service

This application is part of the Polar Bookshop system and provides the functionality for managing
the books in the bookshop catalog.<br>
It's part of the project built in the [Cloud Native Spring in Action](https://www.manning.com/books/cloud-native-spring-in-action) book
by [Thomas Vitale](https://www.thomasvitale.com).

## Commandes utiles

| Commande Maven	               | Description                                                       |
|:------------------------------|:------------------------------------------------------------------|
| `mvn spring-boot:run`         | Lancer l'application.                                             |
| `mvn test`                    | Lancer les tests.                                                 |
| `mvn clean package`           | Packager l'application sous forme de JAR.                         |
| `mvn spring-boot:build-image` | Packager l'application sous forme d'un conteneur. |


Après avoir construit l'application, on peut également l'à lancer à partir d'une invite de commande :

```bash
java -jar target/catalog-service-0.0.1-SNAPSHOT.jar
```

## Conteneurisation

Lancer 'Catalog Service' en tant que conteneur

Pour l'instant, la commande `mvn spring-boot:build-image` ne fonctionne pas. La solution de contournement consiste
à créer un Dockerfile à la racine du projet puis à construire le conteneur correspondant :

```bash
mvn clean package && docker build -t catalog-service:0.0.1-SNAPSHOT .
```

```bash
colima start
export DOCKER_HOST="unix:///Users/75774P/.colima/default/docker.sock"
```

```bash
docker run --rm --name catalog-service -p 8080:8080 catalog-service:0.0.1-SNAPSHOT
```

```
docker run : Runs a container from an image
--rm : Removes the container after its execution completes
--name catalog-service : Name of the container
-p 8080:8080 : Exposes service outside the container through port 8080
catalog-service:0.0.1-SNAPSHOT : Name and version of the image to run 
```
```bash
open http://localhost:8080
```

### Container Commands

| Docker Command	              | Description       |
|:-------------------------------:|:-----------------:|
| `docker stop catalog-service`   | Stop container.   |
| `docker start catalog-service`  | Start container.  |
| `docker remove catalog-service` | Remove container. |

## Kubernetes tasks

https://www.tutorialworks.com/kubernetes-imagepullbackoff/?utm_content=cmp-true
https://stackoverflow.com/questions/42564058/how-to-use-local-docker-images-with-minikube

# Démarrer minikube
```bash
$ minikube delete
$ minikube start --kubernetes-version=v1.27.0-rc.0
```

# Set docker env
```bash
$ eval $(minikube docker-env)             # Pour que minikube utilise le démon docker
```
# Run in minikube
```bash
$ kubectl run catalog-service --image=catalog-service:0.0.1-SNAPSHOT --image-pull-policy=Never
```

# Create service
```bash
$ kubectl create deployment catalog-service --image=catalog-service:0.0.1-SNAPSHOT
```
Description de la commande :
kubectl create                         : Create a Kubernetes resource
deployment                             : Type of resource to create
catalog-service                        : Name of the deployment
--image=catalog-service:0.0.1-SNAPSHOT : Name and version of the image to run

The Kubernetes command to create a Deployment from a container image. Kubernetes 
will take care of creating Pods for the application.

You can verify the creation of the Deployment object as follows:
```bash
$ kubectl get deployment
```
NAME              READY   UP-TO-DATE   AVAILABLE   AGE
catalog-service   1/1     1            1           7s

Behind the scenes, Kubernetes created a Pod for the application defined in the 
Deployment resource. You can verify the creation of the Pod object as follows:
```bash
$ kubectl get pods
```
NAME              READY   STATUS    RESTARTS   AGE
catalog-service   1/1     Running   0          10s
 
TIP : You can check the application logs by running **kubectl logs deployment/ catalog-service**.

# Expose service

By default, applications running in Kubernetes are not accessible. Let's fix that. First,
you can expose Catalog Service to the cluster through a Service resource by running
the following command :

```bash
$ kubectl expose deployment catalog-service --name=catalog-service --port=8080
```

# Forward port
```bash
$ kubectl port-forward service/catalog-service 8000:8080
```
```bash
open http://localhost:8000
```

# Clean up

Suppression du service :
```bash
kubectl delete service catalog-service
```

Suppression du déploiement
```bash
kubectl delete deployment catalog-service
```

Arret du cluster Kubernetes
```bash
minikube stop
```