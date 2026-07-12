# Multi-tier-Web-Java-application-Pipline-using-gitlab-Argocd-"CICD"
prprequieats :

1- K8S environemnt 
2-Argocd app 
3- Gillab repository ==> upload images in the Docker hub 
4- create Docker hub _username & Docker hub_Token on the github 
Docker hub : 
-from account seeting ==> Generate new Token 
Add secrets to Github :
from settings==> secretand variables ==> Actions ==> create  new repo secret as below : 
<img width="1472" height="757" alt="image" src="https://github.com/user-attachments/assets/c36bf9a9-c152-40c0-8643-9eed524a0665" />

steps : 
1- prpepare gillab "CI"
create Wokflow file with main.yml file to be start CI " Action" on my repo github 
to be start A runner to create new VM temp as it is is simply a temporary computer that GitHub uses to run your workflow and after push images , the runner is deleted after the jobs finished .
error :
<img width="1090" height="490" alt="image" src="https://github.com/user-attachments/assets/aac13c67-07ef-4d01-9c28-dcb983ef4c2b" />
<img width="1875" height="778" alt="image" src="https://github.com/user-attachments/assets/4773ba4b-9859-488c-a1bb-6fecc43ce1e3" />
<img width="1559" height="900" alt="image" src="https://github.com/user-attachments/assets/7a94b933-22a6-417c-90d0-634e4bd9b8f8" />
and also make all is lower case as the below error appeared also : 
ERROR: failed to build: invalid tag "***/vprofile-App:latest": repository name must be lowercase
Error: buildx failed with: ERROR: failed to build: invalid tag "***/vprofile-App:latest": repository name must be lowercase
after edit all Dockerfiles with small leterr rerun the jobs or commit the branch :
<img width="1077" height="501" alt="image" src="https://github.com/user-attachments/assets/b6681ac1-6c6c-412e-87ab-b60fa7ac802f" />
successfully tasks 
and check images on the docker hub :
<img width="1455" height="175" alt="image" src="https://github.com/user-attachments/assets/f65585da-baec-42c0-94b2-2debae2e1553" />


2-prepare Cd" ArgoCD " 
open app :
<img width="1641" height="1048" alt="image" src="https://github.com/user-attachments/assets/85bbfcd1-2a9b-465f-b960-58d9df7199e9" />

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/6aafb289-e8b4-4cc4-9b5a-93e4a70d1321" />
and create new application : 
Add Repo URL Of github : https://github.com/Nadasawah90/Multi-tier-Web-Java-application-Pipline-using-gitlab-Argocd-
as the below setting : 
<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/90bfe9b2-b052-472f-9c82-eb88caba4340" />
check :**
<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/ab5dbd51-1692-4d5e-b96b-88979d07dd76" />

check pods on K8s Master node : 
<img width="1641" height="1048" alt="image" src="https://github.com/user-attachments/assets/c1b4f860-91a6-452d-806e-fc6a96bdec98" />

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/cbb24ca6-42d6-4a7e-a77d-034a48209e3c" />
<img width="1641" height="1048" alt="image" src="https://github.com/user-attachments/assets/04a3ff2b-3ca5-4b59-ab1a-80596f763b5f" />


check URL  Load balancer node : 
http://192.168.142.159:30612/login
<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/b0973d33-ceae-4b98-a784-d08bc99ea30b" />



