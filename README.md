# Multi-tier-Web-Java-application-Pipline-using-gitlab-Argocd-"CICD"

## Prerequisites

Before starting, ensure the following requirements are completed:

1- Kubernetes (K8s) Environment

A working Kubernetes cluster is deployed and accessible.

2- Argo CD

Argo CD is installed and configured in the Kubernetes cluster.

3- GitLab Repository

Store the application source code in the GitLab repository & Build the Docker image and push it to Docker Hub.

4- Genertate  Docker hub _username & Docker hub_Token on the github as the below steps : 

5- Docker Hub
From Account Settings → Personal Access Tokens → Generate New Token.

6- Add Secrets to GitHub

Go to Settings → Secrets and variables → Actions.

Create the following secrets:

DOCKERHUB_USERNAME

DOCKERHUB_TOKEN

<img width="1472" height="757" alt="image" src="https://github.com/user-attachments/assets/c36bf9a9-c152-40c0-8643-9eed524a0665" />

## Steps : 
## 1. Prepare GitHub CI (GitHub Actions)

Create the workflow file:
.github/workflows/main.yml

- Commit and push the file to the GitHub repository.

- GitHub Actions will automatically start the CI pipeline.

- GitHub creates a temporary GitHub-hosted runner (VM) to execute the workflow.

- The runner builds the Docker image and pushes it to Docker Hub.

- After the workflow finishes successfully, the temporary runner is automatically deleted.

Errors : 

<img width="1090" height="490" alt="image" src="https://github.com/user-attachments/assets/aac13c67-07ef-4d01-9c28-dcb983ef4c2b" />

<img width="1875" height="778" alt="image" src="https://github.com/user-attachments/assets/4773ba4b-9859-488c-a1bb-6fecc43ce1e3" />

-i changed the Docker files name  owith  the same on source  code .

<img width="1559" height="900" alt="image" src="https://github.com/user-attachments/assets/7a94b933-22a6-417c-90d0-634e4bd9b8f8" />

- And also make all is with the lower case as the below error appeared also : 

ERROR: failed to build: invalid tag "***/vprofile-App:latest": repository name must be lowercase
Error: buildx failed with: ERROR: failed to build: invalid tag "***/vprofile-App:latest": repository name must be lowercase


- after edit all Dockerfiles with the small letter and  rerun the jobs or commit the branch , successfully tasks as below :

<img width="1077" height="501" alt="image" src="https://github.com/user-attachments/assets/b6681ac1-6c6c-412e-87ab-b60fa7ac802f" />

- and check images on the docker hub :

<img width="1455" height="175" alt="image" src="https://github.com/user-attachments/assets/f65585da-baec-42c0-94b2-2debae2e1553" />

## 2-Prepare CD" ArgoCD " :

- open the application : 

<img width="1641" height="1048" alt="image" src="https://github.com/user-attachments/assets/85bbfcd1-2a9b-465f-b960-58d9df7199e9" />

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/6aafb289-e8b4-4cc4-9b5a-93e4a70d1321" />

-Then create new application : 

Add Repo URL Of github : https://github.com/Nadasawah90/Multi-tier-Web-Java-application-Pipline-using-gitlab-Argocd-

as the below setting : 

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/90bfe9b2-b052-472f-9c82-eb88caba4340" />

check :**

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/ab5dbd51-1692-4d5e-b96b-88979d07dd76" />

- check pods on K8s Master node :

<img width="1641" height="1048" alt="image" src="https://github.com/user-attachments/assets/04a3ff2b-3ca5-4b59-ab1a-80596f763b5f" />

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/cbb24ca6-42d6-4a7e-a77d-034a48209e3c" />

- check URL  Load balancer node : 

http://192.168.142.159:30612/login

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/b0973d33-ceae-4b98-a784-d08bc99ea30b" />

## Result

CI (GitHub Actions): Build and push the Docker image to Docker Hub.

CD (Argo CD): Automatically deploy the latest application version to the Kubernetes cluster.

