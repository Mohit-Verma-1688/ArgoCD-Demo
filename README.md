# ArgoCD-Demo


> Create the Kind cluster with kind.yaml
 
 kind create cluster

> Deploy the argocd in the cluster.

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

> Get the username of the default user admin 

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

> Reset the default passworrd 

argocd account update-password --current-password Bt1rNqgyujKQm3U3 --new-password admin123  

> Login to the argocd after port forwarding 

kubectl -n argocd port-forward svc/argocd-server 8085:80 &

argocd login localhost:8085 --insecure

> First add the ssh public keys to the git hub and then create argocd repo 

argocd repo add git@github.com:Mohit-Verma-1688/ArgoCD-Demo.git --name=repo-argocd --insecure-ignore-host-key --ssh-private-key-path ~/.ssh/id_rsa  
