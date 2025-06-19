```bash
kubectl apply -f app-config.yaml
kubectl exec configmap-pod -- cat /etc/config/database.properties
kubectl exec configmap-pod -- cat /etc/database

kubectl apply -f secret-volume.yaml
kubectl exec secret-pod -- ls -la /etc/secrets
kubectl exec secret-pod -- cat /etc/secrets/username
```