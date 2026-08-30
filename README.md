# Deploy-web-app-using-Argo-CD-

ArgoCD (Argo Continuous Delivery) is a GitOps-based continuous delivery tool for Kubernetes.

It automates the deployment of applications into Kubernetes clusters by synchronizing the cluster state with what’s defined in a Git repository.
and it is different with jeb=nkins as it is PIPline not only continous Delivery it also continpus integration  

Jenkins is a general-purpose automation server mainly used for Continuous Integration (CI) and sometimes for Continuous Delivery (CD).
It can build, test, and deploy code using pipelines written in Groovy or YAML.

Jenkins builds your app → runs tests → pushes Docker image → updates Helm chart or manifest in Git.

Jenkins = CI (build/test)

ArgoCD detects the Git change → automatically deploys new version to Kubernetes

 ArgoCD = CD (deploy/sync)

##  Requiremnet  : 

create ArgoCD mainfests on  kubernates cluster  : 

## Steps : 

on master node :

1- create new namespae with name ArgoCD  : 

kubectl create namespace argocd

2- Deploy deployment and services to implement ArgoCD using it's mainfest yamll file 

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/83c62ff6-1988-4b05-a025-9ffdb6e0fecf" />

check for all deployment with it's pods and services : 

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/fa48e41c-163e-487f-992b-9b2ee9a51bdf" />

3- to be port node to access ArgoCD :

[root@master01 ~]# kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'

service/argocd-server patched

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/75f3c8ec-fdb9-4129-b096-8ecfefeb4ddf" />

4- check for which node deployed to access with it's ip : 

deployed on worker 01 ==>  (https://192.168.142.160:32527/)

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/6e862bc6-f41f-499f-9cc3-0f25bc99a9cd" />

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/40d8875a-a6b2-4318-948d-51e3046b55ad" />

5- to get the password : 

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

and access with admin and the password : 

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/1c66a302-9656-49b7-bfb1-fb10f3755a2c" />

6- start to create application : 

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/71c98ad1-1b1a-48ae-90da-0baf7b9ac689" />

7-Start to create 

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/03bfc357-d3b9-4321-90a9-f4bbfe45c9a6" />

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/17bd8771-77c1-4096-91c5-decbbcd83c55" />

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/5a175999-4e41-437a-83b0-6ba7b4142f30" />


Note : the application is deployed on worker 01 so we can use the ip and port node to access it from master node .

7-acceess application  : 

http://192.168.142.160:32415/login

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/15952b7d-c98f-458b-a465-ed138b9afc5a" />
