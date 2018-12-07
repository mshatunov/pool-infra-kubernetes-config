# Deployment of pool applications with infrastructure

## Start minikube
`minikube stop && minikube delete && minikube --memory 8192 --cpus 4 start`

## Cluster init
`helm init`
`minikube addons enable ingress`
`sudo echo "$(minikube ip) mshatunov.dev" | sudo tee -a /etc/hosts`

### ssl
`openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout tls.key -out tls.crt -subj "/CN=mshatunov.dev" -days 3650`
`kubectl create secret tls mshatunov-dev-tls --cert=tls.crt --key=tls.key`

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