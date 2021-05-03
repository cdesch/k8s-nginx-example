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

    docker images k8s-nginx-example 
    docker tag 66d3a62e4086 cdesch/k8s-nginx-example
    docker tag cdesch/k8s-nginx-example cdesch/k8s-nginx-example:1.0.0
    docker tag cdesch/k8s-nginx-example cdesch/k8s-nginx-example:latest
    docker push cdesch/k8s-nginx-example:latest
    docker push cdesch/k8s-nginx-example:1.0.0


$ sed -i 's/{OLD_TERM}/{NEW_TERM}/' {file}
gsed -i 's/cdesch\/k8s-nginx-example:1.0.0/cdesch\/k8s-nginx-example:1.0.1/' ./deployments/deployment.yaml
cdesch/k8s-nginx-example:1.0.0
    


Ingress

  
k8s ingress https://kubernetes.io/docs/concepts/services-networking/ingress/

kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.45.0/deploy/static/provider/cloud/deploy.yaml

https://kubernetes.github.io/ingress-nginx/deploy/#verify-installation

kubectl delete -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.45.0/deploy/static/provider/cloud/deploy.yaml

kubectl apply -f ingress.yaml
kubectl delete -f ingress.yaml


HPS

https://unofficial-kubernetes.readthedocs.io/en/latest/tasks/run-application/horizontal-pod-autoscale-walkthrough/


kubectl run -i --tty load-generator --image=busybox /bin/sh
$ while true; do wget -q -O- http://prod-k8s-nginx-example.default.svc.cluster.local; done
my-service.my-namespace.svc.cluster.local
prod-k8s-nginx-example


https://forum.gitlab.com/t/git-push-from-inside-a-gitlab-runner/30554/5
https://docs.gitlab.com/ee/ci/multi_project_pipelines.html
https://stackoverflow.com/questions/63633737/how-to-version-or-tag-incrementally-in-gitlab-ci-cd-when-merging-from-production
https://www.reddit.com/r/gitlab/comments/6d1kri/help_increment_version_number_with_runner/
https://threedots.tech/post/automatic-semantic-versioning-in-gitlab-ci/
https://www.baeldung.com/linux/find-replace-text-in-file


function escape_slashes {
    sed 's/\//\\\//g' 
}

function change_line {
    local OLD_LINE_PATTERN=$1; shift
    local NEW_LINE=$1; shift
    local FILE=$1

    local NEW=$(echo "${NEW_LINE}" | escape_slashes)
    sed -i .bak '/'"${OLD_LINE_PATTERN}"'/s/.*/'"${NEW}"'/' "${FILE}"
  
}


change_line "cdesch/k8s-nginx-example:1.0.0" "cdesch/k8s-nginx-example:1.0.1" ./deployments/deployment.yaml
change_line "TEXT_TO_BE_REPLACED" "This line is removed by the admin." yourFile
sed -i 's/cdesch\/k8s-nginx-example:1.0.0/cdesch\/k8s-nginx-example:1.0.1/' deployments/deployment.yaml
PACKAGE_VERSION=$(cat package.json \
  | grep version \
  | head -1 \
  | awk -F: '{ print $2 }' \
  | sed 's/[",]//g')

echo $PACKAGE_VERSION