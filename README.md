# Deployment of pool applications with infrastructure

## Install ingress on kubernetes  
`helm install --name my-release stable/nginx-ingress --set rbac.create=true`

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