# Catalog Service

This application is part of the Polar Bookshop system and provides the functionality for managing
the books in the bookshop catalog. It's part of the project built in the
[Cloud Native Spring in Action](https://www.manning.com/books/cloud-native-spring-in-action) book
by [Thomas Vitale](https://www.thomasvitale.com).

## Useful Commands

| Gradle Command	               | Description                                   |
|:------------------------------|:----------------------------------------------|
| `mvn spring-boot:run`         | Run the application.                          |
| `mvn test`                    | Run tests.                                    |
| `mvn clean package`           | Package the application as a JAR.             |
| `mvn spring-boot:build-image` | Package the application as a container image. |

After building the application, you can also run it from the Java CLI:

```bash
java -jar target/catalog-service-0.0.1-SNAPSHOT.jar
```

## Container tasks

Run Catalog Service as a container

Pour l'instant, la commande `mvn spring-boot:build-image` ne fonctionne pas, solution de contournement :

Création d'un Dockerfile à la racine, puis :

mvn clean package
docker build -t catalog-service .
docker run -p 8080:8080 catalog-service

http://localhost:8080

```bash
docker run --rm --name catalog-service -p 8080:8080 catalog-service:0.0.1-SNAPSHOT
```

### Container Commands

| Docker Command	              | Description       |
|:-------------------------------:|:-----------------:|
| `docker stop catalog-service`   | Stop container.   |
| `docker start catalog-service`  | Start container.  |
| `docker remove catalog-service` | Remove container. |

## Kubernetes tasks

### Create Deployment for application container

```bash
kubectl create deployment catalog-service --image=catalog-service:0.0.1-SNAPSHOT
```

### Create Service for application Deployment

```bash
kubectl expose deployment catalog-service --name=catalog-service --port=8080
```

### Port forwarding from localhost to Kubernetes cluster

```bash
kubectl port-forward service/catalog-service 8000:8080
```

### Delete Deployment for application container

```bash
kubectl delete deployment catalog-service
```

### Delete Service for application container

```bash
kubectl delete service catalog-service
```
