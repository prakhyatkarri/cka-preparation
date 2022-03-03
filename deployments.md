#### Check existing replicasets on cluster
kubectl get rs

#### Check existing deployments on cluster
kubectl get deploy

#### Create a deployment with name "nginx-deployment" with image "nginx" and 5 replicas
kubectl create deploy nginx-deployment --image nginx --replicas=5 --dry-run=client -o yaml > nginx-deployment.yml
k apply -f nginx-deployment.yml
k get deploy
k get po


#### Check deployment/rollout status
kubectl rollout status deploy <deployment_name>

#### Check deployment/rollout history
kubectl rollout history deploy <deployment_name>

#### Undo deployment to previous version
kubectl rollout undo deploy <deployment_name>
kubectl rollout undo deploy <deployment_name> --to-revision=<version_number>
