#### Check taints on Node
kubectl describe no <node-name>

#### Taint a node
kubectl taint no <node-name> key=value:effect
```
Effects: NoSchedule/NoExecute
```
### Add toleration to pod
Add below sections in "spec" at "containers" level
```
tolerations:
 - key: key1
   value: value1
   effect: NoSchedule
   operator: Equal
```
#### Untaint a node
Add a "-" after taint value to remove taint on Node \

kubectl taint no <node-name> key1-

