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

## affiche tous les services dont ceux prop à k8s comme le dashboard
k get svc -A

## Récupère le token pour accéder à l'administration kubernetes
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-user | awk '{print $1}' )

# affiche les logs
k get logs


## CPU et limits => test memoire
k create deployment hog --image vish/stress

## Namespace
k create namespace low-usage-limit
## Configure namespace depuis fichier
k --namespace=low-usage-limit create -f low-resource-range.yaml 
## affiche les limitrange (-A affiche tous les namespace)
k get limitranges -A
k -n low-usage-limit get limitranges 



## deploie un container en utilisant un namespace et son limitrange associé (-n spécifie le namespace)
k -n low-usage-limit create deployment limited-hog --image vish/stress

## affiche la liste des replicats set
k get rs -A -o wide

## supprime le replicats set sans supprimer les pods
k delete rs rs-one --cascade=false

## modifie un fichier yaml
k edit pod rs-one-4zx7l 
## labels: system: IsolatedPod / ReplicaOne / DaemonSetOne
## isolatedPod permet d'isoler le pod afin de l'étudier



## Afiche le type de system en plus des infos pods
k get pod -L system

## supprime les pod ayant comme label system=IsolatedPod
k delete po -l system=IsolatedPod


## execute une commande sur un pod
k exec -it shell-demo -- /bin/bash -c 'echo $ilike'



## example :
k create -f curl.yaml -n kube-public
k create -f frontend.yaml 
k create -f webapp-service.yaml 
chmod +x curl-test.sh
./curl-test.sh

## Etat du déploiement
k rollout status deployment frontend 
## Historique du déploiement
k rollout history deployment frontend
## RollBack du deployment
k rollout undu deployment frontend
























## dans .bashrc
alias k='kubectl'
## auto completion
source <( kubectl completion bash | sed s/kubectl/k/g)

```