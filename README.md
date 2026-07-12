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


2-prepare Cd" ArgoCD " 
