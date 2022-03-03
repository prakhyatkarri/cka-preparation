# Get Configmaps
kubectl get cm

# Describe Configmaps
kubectl describe cm <configmap_name>

# Create Configmap
kubectl create cm <configmap_name> --from-literal=key=value
kubectl create cm <configmap_name> --from-file=<file_path>

# Set env in pod from ConfigMap key
env:
- name: my_environment_variable
  valueFrom:
   configMapKeyRef:
    name: config_map_name
    key: key_name


