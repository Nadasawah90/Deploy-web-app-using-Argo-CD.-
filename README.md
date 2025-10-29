# Deploy-web-app-using-Argo-CD-
** ArgoCD (Argo Continuous Delivery) is a GitOps-based continuous delivery tool for Kubernetes.
It automates the deployment of applications into Kubernetes clusters by synchronizing the cluster state with what’s defined in a Git repository.
and it is different with jeb=nkins as it is PIPline not only continous Delivery it also continpus integration  

** Jenkins is a general-purpose automation server mainly used for Continuous Integration (CI) and sometimes for Continuous Delivery (CD).
It can build, test, and deploy code using pipelines written in Groovy or YAML.

Jenkins builds your app → runs tests → pushes Docker image → updates Helm chart or manifest in Git.

ArgoCD detects the Git change → automatically deploys new version to Kubernetes

🧩 Jenkins = CI (build/test)
🚀 ArgoCD = CD (deploy/sync)
Reference Link : https://argo-cd.readthedocs.io/en/stable/
##  Requiremnet  : 
create ArgoCD mainfests on  kubernates cluster  : 
## Steps : 
on master node : 
1- create new namespae with name ArgoCD  : 
kubectl create namespace argocd
2- Deploy deployment and services to implement ArgoCD using it's mainfest yamll file 
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/83c62ff6-1988-4b05-a025-9ffdb6e0fecf" />


