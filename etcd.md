#### Check ETCD version
kubectl describe po <etcd_pod_name> -n kube-system | grep -i image:

#### Get Certificate paths 
k describe po <etcd_pod_name> -n kube-system   | grep -i crt

#### Take snapshot
1. Set ETCD version \
ETCDCTL_API=3

2. Take snapshot \
Create and run script with below

```
export ETCDCTL_API=3
echo $ETCDCTL_API
etcdctl --endpoints=127.0.0.1:2379 \
        --cert=/etc/kubernetes/pki/etcd/server.crt \
        --key=/etc/kubernetes/pki/etcd/server.key \
        --cacert=/etc/kubernetes/pki/etcd/ca.crt \
        snapshot save /opt/snapshot-pre-boot.db

```

#### Restore ETCD from snapshot
1. Restore from snapshot \
ectdctl --data-dir=<new-backup-location> snapshot restore <file_path> \

2. Update Manifest at /etc/kubernetes/manifests/etcd.yaml by adding volume 
```
volumes:
  - hostPath:
      path: <new-backup-location>
      type: DirectoryOrCreate
    name: etcd-data


```

