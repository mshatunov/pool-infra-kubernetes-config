# Deployment of pool applications with infrastructure

## Dashboard url:  
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/

## Start minikube
minikube stop &&
minikube delete &&
minikube --memory 8192 --cpus 4 start

## Install ingress on kubernetes  
`helm init`

`helm install stable/nginx-ingress --set rbac.create=true`

If using kubectl proxy
`kubectl --namespace=kube-system edit deployment/tiller-deploy`
and change automountServiceAccountToken to true.

`kubectl --namespace=kube-system create clusterrolebinding add-on-cluster-admin --clusterrole=cluster-admin --serviceaccount=kube-system:default`

## Deploy pool apps
From scratch
`kubectl create -f config/ --recursive --save-config`

Update config
`kubectl apply -f config/ --recursive`

## Useful links
### Common kubernetes examples
>https://piotrminkowski.wordpress.com/2017/03/31/microservices-with-kubernetes-and-docker/

### Ingress example
>https://hackernoon.com/setting-up-nginx-ingress-on-kubernetes-2b733d8d2f45