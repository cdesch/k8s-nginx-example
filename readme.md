# k8s-nginx-example

- [repo](https://github.com/cdesch/k8s-nginx-example)

## Deployment

    kubectl apply -f deployments/setup/namespace.yaml
    kubectl apply -n k8s-nginx-example -f deployments
    kubectl delete -n k8s-nginx-example -f deployments
    kubectl delete -f deployments/setup/namespace.yaml


    kubectl apply -n k8s-nginx-example -f deployments/ingress.yaml
    kubectl delete -n k8s-nginx-example -f deployments/ingress.yaml


## Manual Docker Run

    docker run -it --rm -d -p 8080:80 --name web -v /Users/cj1/projects/k8s-nginx-example/data:/usr/share/nginx/html nginx

## Build Docker

    docker build -t k8s-nginx-example .
    docker run -it --rm -d -p 8080:80 --name web k8s-nginx-example

## Push to docker

    docker
    docker tag 23a2e385147c cdesch/k8s-nginx-example
    docker push cdesch/k8s-nginx-example


Ingress

  
k8s ingress https://kubernetes.io/docs/concepts/services-networking/ingress/

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.45.0/deploy/static/provider/cloud/deploy.yaml

https://kubernetes.github.io/ingress-nginx/deploy/#verify-installation

kubectl delete -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.45.0/deploy/static/provider/cloud/deploy.yaml

kubectl apply -f ingress.yaml
kubectl delete -f ingress.yaml