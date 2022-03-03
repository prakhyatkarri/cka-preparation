#### Empty/Drain a node
kubectl drain <node_name> --ignore-daemonsets
kubectl cordon <node_name>

#### Mark Node as Unschedulable
kubectl cordon <node_name>

#### Mark Node as Schedulable
kubectl uncordon <node_name>
