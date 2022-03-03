#### Check existing services on cluster
kubectl get svc

#### Check Service information
kubectl describe svc <svc-name>

#### Create Nodeport service
kubectl create service nodeport <service-name> --node-port 30080 --tcp 8080:8080 --dry-run=client -o yaml > svc.yml
k get svc
k describe svc <service-name>
