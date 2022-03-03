## Find kube scheduler
kubectl get po -n kube-system

## Find the manifest file
Usually at /etc/kubernetes/manifests/<kube-scheduler>.yml

## Create custom scheduler
Update above manifest file and add these flags under "command" in containers
    - --port=10282
    - --leader-elect=false
    - --scheduler-name=my-scheduler
    - --secure-port=0

## Create a pod using custom scheduler
Add "schedulerName" field to pod definition at "spec.*" level

schedulerName: my-scheduler
