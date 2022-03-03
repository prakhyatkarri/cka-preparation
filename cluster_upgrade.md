#### Get Cluster Version
kubectl version

#### Get Next stable version to Upgrade
ssh into node - master or worker
kubeadm upgrade plan

#### Upgrade steps
1. Check current version \
kubectl version

2. Check Next version to upgrade \
kubeadm upgrade plan

3. Drain node \
kubectl drain <node_name> --ignore-daemonsets

4. Upgrade kubeadm \

```
apt update 
apt-cache madison kubeadm 

# find the latest 1.20 version in the list
# it should look like 1.20.x-00, where x is the latest patch

# replace x in 1.20.x-00 with the latest patch version
apt-mark unhold kubeadm && \
apt-get update && apt-get install -y kubeadm=1.20.x-00 && \
apt-mark hold kubeadm
-
# since apt-get version 1.1 you can also use the following method 
apt-get update && \
apt-get install -y --allow-change-held-packages kubeadm=1.20.x-00
```

5. Verify Upgrade Plan \
kubeadm upgrade plan \

6. Run Upgrade Apply with version \
ka upgrade apply v1.20.0 \
When prompted, enter y \

7. Look for Successful confirmation \
[upgrade/successful] SUCCESS! Your cluster was upgraded to "v1.20.0". Enjoy! \

8. Upgrade kubectl and kubelet
```
# replace x in 1.20.x-00 with the latest patch version
apt-mark unhold kubelet kubectl && \
apt-get update && apt-get install -y kubelet=1.20.x-00 kubectl=1.20.x-00 && \
apt-mark hold kubelet kubectl
-
# since apt-get version 1.1 you can also use the following method
apt-get update && \
apt-get install -y --allow-change-held-packages kubelet=1.20.x-00 kubectl=1.20.x-00
```

9. Verify Kubectl and Kubelet versions \
kubectl version \
kubeadm version \

10. Restart Kubelet \
```
sudo systemctl daemon-reload
sudo systemctl restart kubelet
```

11. Uncordon Node and mark it as Schedulable \
kubectl uncordon <node_name> \

#### Upgrade Node (Worker)
1. Drain the node \
kubectl drain <node_name> --ignore-daemonsets \

2. SSH into Node \
ssh <node_name> \

3. Upgrade Kubeadm 
```
# replace x in 1.20.x-00 with the latest patch version
apt-mark unhold kubeadm && \
apt-get update && apt-get install -y kubeadm=1.20.x-00 && \
apt-mark hold kubeadm
-
# since apt-get version 1.1 you can also use the following method
apt-get update && \
apt-get install -y --allow-change-held-packages kubeadm=1.20.x-00
```

4. Upgrade Node \
sudo kubeadm upgrade node \

5. Upgrade Kubectl and Kubeadm 
```
# replace x in 1.20.x-00 with the latest patch version
apt-mark unhold kubelet kubectl && \
apt-get update && apt-get install -y kubelet=1.20.x-00 kubectl=1.20.x-00 && \
apt-mark hold kubelet kubectl
-
# since apt-get version 1.1 you can also use the following method
apt-get update && \
apt-get install -y --allow-change-held-packages kubelet=1.20.x-00 kubectl=1.20.x-00\
```

6. Restart Kubelet
```
sudo systemctl daemon-reload
sudo systemctl restart kubelet
```
7. Uncordon Node and mark is Schedulable \
kubectl uncordon <node_name> \
