# Get secrets
kubectl get secrets
kubectl get secret <secret_name>
kubectl get secret <secret_name> -o yaml
kubectl describe secret <secret_name>


# Create secrets
k create secret generic db-secret --from-literal=key1=value1 --from-literal=key2=value2
kubectl create secret generic -from-file=<file_path>

# Inject Env in Pod from secret
envFrom:
- secretRef:
    name: db-secret
    