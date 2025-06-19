```bash
kubectl apply -f empty-dir-pod.yaml
kubectl logs shared-volume-pod -c reader -f
kubectl apply -f hostpath-pod.yaml
kubectl exec hostpath-pod -- ls -la /var/log/nginx
```