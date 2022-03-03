#### Check existing pods on cluster
kubectl get po

#### Check existing pods and their nodes information
kubectl get po -o wide

#### Get pods by label
kubectl get po -l key1=value1,key2=value2

#### Create a pod with name and image "nginx"
kubectl run nginx --image nginx --dry-run=client -o yaml > nginx.yml
kubectl apply -f nginx.yml
kubectl get po
kubectl describe po nginx

### Check image for running pod
kubectl get po nginx
kubectl describe po nginx | grep -i image:

#### Delete a pod
Assumption: Running a pod with nginx image

kubectl delete po nginx
kubectl delete po nginx --force


#### Add commands in pod
command: ["sleep", "4800"]
args: ["--type","code"]

