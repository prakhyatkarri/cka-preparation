#### Install Metrics server
git clone https://github.com/kodekloudhub/kubernetes-metrics-server.git
k apply -f kubernetes-metric-server/

#### Get Pods metrics
kubectl top po
kubectl top po --sort-by=top

#### Get Nodes metrics
kubectl top no
kubectl top no --sort-by=memory


#### Get pod logs
kubectl logs <pod_name>
kubectl logs <pod_name> -c <container_name>

#### Get previous pod logs
kubectl logs -p <pod_name>

#### Follow pod logs
kubectl logs -f <pod_name>
