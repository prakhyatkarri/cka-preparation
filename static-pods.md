## Static pods usually have prefixed their pods name with Node name

## Default location for Static pod manifest files
/etc/kubernetes/manifests/

#### How to deploy a pod as static
Create a Yml manifest file to create pod and move it to /etc/kubernetes/manifests/

#### How to identify Static pod path
ssh to node where static pod is running
open file at /var/lib/kubelet/config.yaml
Look for field "staticPodPath:" 