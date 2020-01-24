# k8s-webforce3

## Check
```shell script
  kubectl get nodes
  kubectl get node
  kubectl get node -o wide

## Deployment example
  kubectl create deployment nginx --image=nginx
  kubectl get deployments
  kubectl describe deployment nginx
  kubectl get events
  kubectl get deployment nginx -o yaml 
  kubectl get deployment nginx -o yaml > first.yaml

## Deployment with file
  kubectl create -f file.yaml

## delete deployment
  kubectl delete deployments nom

## permet d'afficher la config sans deployer : --dry-run
 k create deployment two --image=nginx --dry-run -o yaml
 k create deployment two --image=nginx --dry-run -o json


## 
k expose -h

## recharge la configuration du déploiement
k replace -f no.yaml

## affiche les infos
k get deploy,pod,svc

## 
k expose deployment/nginx


## affiche les services
k get svc 

## Explication kubernetes
https://www.padok.fr/blog/architecture-kubernetes-clusters
https://www.padok.fr/blog/kubernetes-pods-services

## affiche l'endpoint : les adresses ip des services
k get ep 

# indique sur quel noeud le pod tourne
k get pod -o wide

## Crée 3 pods
k scale deployment nginx --replicas=3

# arrète tous les pods d'un déployment
k scale deployment nginx --replicas=0

## affiche le
k get deployments nginx 

## raccourci deployment nginx = deploy nginx = deploy/nginx

## execute une command sur le pod
k exec nginx-85ff79dd56-s4z4h -- printenv | grep KUBERNETES

## expose le service à l'extérieur
k expose deployment nginx --type=LoadBalancer

##
k get svc -A

## Récupère le token pour accéder à l'administration kubernetes
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}' )

# affiche les logs



## CPU et limits
k create deployment hog --image vish/stress


## dans .bashrc
alias k='kubectl'
## auto completion
source <( kubectl completion bash | sed s/kubectl/k/g)

```