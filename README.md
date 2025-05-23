# Docker-Kubernetes-Portfolio

The idea behind this repo is to learn how to use Kubernetes (using Minikube in this case) in order to deploy a containerized - using Docker - Python/Flask app (i.e. reusing the static Flask app from my [AWS-Terraform](https://github.com/mathieu-boe/AWS-terraform-infrastructure-portfolio)) repo. The project includes:
- Docker
- Minikube / K8s

## Resources

Below are the resources used to get me started:
- https://docs.docker.com/get-started/workshop/
- https://hub.docker.com/_/python
- https://minikube.sigs.k8s.io/docs/
    - https://minikube.sigs.k8s.io/docs/handbook/pushing/
- https://kubernetes.io/docs/home/
- https://flask.palletsprojects.com/en/stable/

## Step by Step

1. Install Docker
2. Install Minikube (brew install minikube)
2.1. Start Minikube (minikube start)
3. Create the Flask app
3.1. Create the requirements.txt file for Flask (echo 'flask' >> /your/project/app/requirements.txt)
4. Create the Dockerfile in your App's root directory
5. Use Minikube Docker Daemon and build the Docker image for the app
5.1. eval $(minikube docker-env)
5.2 docker build -t "docker-app-name" . #Run this command in the directory where the Dockerfile is located
6. Create both deployment.yaml and service.yaml
6.1 Apply Kubernetes manifest
6.1.1 kubectl apply -f deployment.yaml
6.1.2 kubectl apply -f service.yaml
7. Access your app
7.1. minikube service flask-service #flask-service should match the name of the service in service.yaml
7.1.2 Make sure your container is running (kubectl get pods, kubectl logs <pod_ID> if you've got any issue)


## To Do

- [x] Create a basic HelloWorld Flask app
- [x] Create a docker file for the app
- [x] Build the Docker image in a Minikube environment
- [x] Create the Kubernetes manifests (deployment.yaml & service.yaml)

## To Go Further

- [ ] Deploy the app in AWS using AWS EKS