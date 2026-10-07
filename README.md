# Mini Web Application – Docker & Kubernetes

## Project Overview

This project demonstrates how to develop a simple web application, containerize it using Docker, push the Docker image to Docker Hub, and deploy the application using Kubernetes.

The application is a simple responsive web page developed using HTML and CSS.

## Technologies Used

* HTML5
* CSS3
* Docker
* Docker Hub
* Kubernetes
* Nginx
* Git & GitHub

## Project Structure

```text
Mini-Web-App-Docker-Kubernetes/
│
├── index.html
├── Dockerfile
├── deployment.yaml
├── service.yaml
└── README.md
```

## Docker Implementation

### 1. Build Docker Image

```bash
docker build -t mini-web-app .
```

### 2. Run Docker Container

```bash
docker run -d -p 8080:80 --name mini-web-container mini-web-app
```

The application can be accessed at:

```text
http://localhost:8080
```

### 3. Tag Docker Image

```bash
docker tag mini-web-app 24ucs214/mini-web-app:latest
```

### 4. Push Image to Docker Hub

```bash
docker push 24ucs214/mini-web-app:latest
```

## Kubernetes Deployment

The Docker image is deployed using Kubernetes.

### Deployment

The `deployment.yaml` file creates two replicas of the application.

```bash
kubectl apply -f deployment.yaml
```

Check the Pods:

```bash
kubectl get pods
```

Expected result:

```text
mini-web-app-xxxxxxxxxx-xxxxx   1/1   Running
mini-web-app-xxxxxxxxxx-xxxxx   1/1   Running
```

## Kubernetes Service

The `service.yaml` file creates a NodePort service to expose the application.

```bash
kubectl apply -f service.yaml
```

Check the service:

```bash
kubectl get services
```

The application uses NodePort:

```text
30080
```

## Access the Application

Open the following URL in a web browser:

```text
http://localhost:30080
```

## Kubernetes Architecture

```text
                    Browser
                       │
                       ▼
              Kubernetes Service
                 NodePort 30080
                       │
              ┌────────┴────────┐
              ▼                 ▼
          Pod 1             Pod 2
              │                 │
              └────────┬────────┘
                       ▼
                 Nginx Container
                       │
                       ▼
                   index.html
```

## GitHub Repository

The complete source code, Dockerfile, and Kubernetes configuration files are maintained in this GitHub repository.

## Docker Hub Image

Docker image:

```text
24ucs214/mini-web-app:latest
```

## Conclusion

This project demonstrates the basic DevOps workflow of developing a web application, containerizing it with Docker, storing the image in Docker Hub, and deploying and exposing the application using Kubernetes.
