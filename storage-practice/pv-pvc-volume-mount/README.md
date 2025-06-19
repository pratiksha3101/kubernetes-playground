kubectl apply -f manual-pv-pvc.yaml
kubectl get pv,pvc
kubectl exec pv-pod -- tail -f /data/log.txt
# Delete pod and recreate to see data persistence
kubectl delete pod pv-pod
kubectl apply -f manual-pv-pvc.yaml
kubectl exec pv-pod -- cat /data/log.txt