## CI/CD pipeline 
To install and prepare a CI/CD pipeline using Git + Jenkins to deploy an app on a Kubernetes cluster,we need to prepare both infrastructure components and 
access/configuration prerequisites.

### 1- Source Control : 

- Git repository (GitHub ) : https://github.com/Nadasawah90/Deploy-app-using-jenkins-file-pipline-.git 

- Dockerfile (to containerize the app) .

- Yaml Files to deploy on the Kubernates cluster .

- Docker hub account with repository created to push images on it  .

### 2- Platform 

- Kubernates " kubeadm "  platform " one matser and two workers "

- Jenkins server with required plugin to can work all stages process : 

Git plugin & Pipeline plugin & Docker pipeline plugin & Kubernetes CLI plugin .

and also Docker installed on Jenkins machine and also git packages "yum install git - y " on the server .

### 3- Access & Credentials 

credentials setting s : 

1- Docker Registry  on jenkins credentials 

<img width="1690" height="741" alt="image" src="https://github.com/user-attachments/assets/749e08dd-a27e-43b2-9b74-586b1732ca9a" />

2- Git hub credentials using tokern password 

<img width="1585" height="540" alt="image" src="https://github.com/user-attachments/assets/a8c765a5-f052-4754-a2ed-c0a8499ae523" />


<img width="1743" height="852" alt="image" src="https://github.com/user-attachments/assets/e3fbb205-6c6c-4467-ad01-75c504d48321" />

3- Configured the Jenkinsfile based on the users added in Jenkins.

<img width="738" height="430" alt="image" src="https://github.com/user-attachments/assets/a2335402-cdd6-4b2e-b806-743922327341" />

4- Start to create job PiPline with name " new-one" 

<img width="1875" height="882" alt="image" src="https://github.com/user-attachments/assets/3d9986ef-77e8-4573-a63f-50d73cc913d3" />

<img width="1360" height="497" alt="image" src="https://github.com/user-attachments/assets/49ce96b2-72d5-4d24-8043-d812915ca459" />

We can now Build the Pipline and start it : 

check the workspace created by the new job on the defaut path directory on the VM of jenkins  as below  :

/var/lib/jenkins/workspace   

<img width="1042" height="66" alt="image" src="https://github.com/user-attachments/assets/687515af-5d61-4b97-9e42-1ab8e98a13e2" />


the stages of Pipline is in progress as we have 6 stages : 

1- stage for Checkout SCM 

2- Stage Checkout 

3- stage for BUIld APP Image .

4- Build DB Image 

5- Push to Docker Hub  

6- Deploy to Kubernates 

<img width="1920" height="1040" alt="image" src="https://github.com/user-attachments/assets/a44fc7d5-0c40-460e-b0dc-a25bebc0af2e" />
 
## Hint : 

- be sure to be used main not master and directory on jenkins file the same on repo git hub 

-  make sure to Download git and docker on the jenkins plugin and also on the sever which deployed jenkins .

-  make sure also to add kubernates and credentials on the jenkins to be can deploy the app onn it .

##  The issue :

### 1-  issue with docker hub  registry need also token : 
 
<img width="1187" height="521" alt="image" src="https://github.com/user-attachments/assets/5191f11c-a163-4643-8d04-c67399296035" />

i used tokern password and generate it as the below  :

<img width="1307" height="693" alt="image" src="https://github.com/user-attachments/assets/0d2fb7ac-b0fd-4a3e-b398-146b8c319bba" />


<img width="1652" height="976" alt="image" src="https://github.com/user-attachments/assets/13257ec0-8446-4069-a8af-b1e385b229cd" />
 
and solved the issue after rerun :

 <img width="1362" height="228" alt="image" src="https://github.com/user-attachments/assets/d6de3b06-91df-41af-a8d3-bb14237fb073" />
 
### 2- Issue  in the last stage " Deploy to kubernates " : 

<img width="1566" height="453" alt="image" src="https://github.com/user-attachments/assets/62a19ede-924f-4ab0-841f-66a9421d09aa" />

create tokern for Kubeadmin as below : 

<img width="1490" height="812" alt="image" src="https://github.com/user-attachments/assets/4c00ad6d-89f8-4e43-8402-2c5ee3fc8131" />


add credentisals and secret text token on the below image  fro jenkins : 

<img width="1477" height="945" alt="image" src="https://github.com/user-attachments/assets/a1ea9097-114e-4c90-bebb-fe5fb92358a6" />

### 3- Issue i have facesd again as below : 

<img width="1882" height="532" alt="image" src="https://github.com/user-attachments/assets/04878b15-3425-4978-b7f3-db0dca6e2054" /> 

i create namespace with myapp name on kubernates cluster  and rerun again this stage and create new pipline with new -one name to be delte all cashing issue from the old one  .

### finally success to deploy aapp :
<img width="1870" height="858" alt="image" src="https://github.com/user-attachments/assets/79b47fa5-c971-4261-89b2-b015d1594e79" />

<img width="898" height="548" alt="image" src="https://github.com/user-attachments/assets/9ccc8992-8c7c-4aee-aeb3-c426f19fd7b8" />

<img width="1413" height="442" alt="image" src="https://github.com/user-attachments/assets/d834fa99-fd16-44bc-8a71-bfeb150368e9" />

We can use this port to be forward accessing to app service of Tomcat app   :

<img width="758" height="46" alt="image" src="https://github.com/user-attachments/assets/b6358f70-0cb0-4a0b-ba0c-b3101ec8a579" />

<img width="758" height="46" alt="image" src="https://github.com/user-attachments/assets/970796a7-4d6d-4045-abb7-cd2efa9e0700" />

<img width="1725" height="968" alt="image" src="https://github.com/user-attachments/assets/e9573e21-58c1-4bfc-84d4-3f0134169b07" />

## Benefit of Jenkins Pipeline vs Freestyle Job

Using a Jenkins Pipeline instead of a Freestyle job gives you full automation and better control of the CI/CD process.
## Main Benefits:
we  only change the code in Git repository and Everything "uild, Docker image, push, deploy to Kubernetes"  becomes fully automated  without manual work. 

## What the pipeline does automatically:

1- Detects changes in Git repository

2- Builds the application

3- Creates a Docker image from source code

3- Pushes the image to Docker Hub (or registry)

4- Deploys the application using Kubernetes YAML files (kubeadm cluster)

5- Updates the running application automatically
