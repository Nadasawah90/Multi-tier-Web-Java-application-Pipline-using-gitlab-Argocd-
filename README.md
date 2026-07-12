# Multi-tier-Web-Java-application-Pipline-using-gitlab-Argocd-
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
1- prpepare gillab : 
create Wokflow file on my repo github 
to be start A runner to create new VM temp as it is is simply a temporary computer that GitHub uses to run your workflow and after push images , the runner is deleted after the jobs finished .

