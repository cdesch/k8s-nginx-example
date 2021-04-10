kubectl apply -f deployments

kubectl delete -f deployments


docker run -it --rm -d -p 8080:80 --name web -v /Users/cj1/projects/k8s-nginx-example/data:/usr/share/nginx/html nginx