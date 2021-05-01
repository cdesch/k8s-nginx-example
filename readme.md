kubectl apply -f deployments

kubectl delete -f deployments


docker run -it --rm -d -p 8080:80 --name web -v /Users/cj1/projects/k8s-nginx-example/data:/usr/share/nginx/html nginx


Ingress

  
k8s ingress https://kubernetes.io/docs/concepts/services-networking/ingress/

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.45.0/deploy/static/provider/cloud/deploy.yaml
https://kubernetes.github.io/ingress-nginx/deploy/#verify-installation

kubectl delete -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.45.0/deploy/static/provider/cloud/deploy.yaml

kubectl apply -f ingress.yaml
kubectl delete -f ingress.yaml