kubectl apply -f complex-volumes.yaml
kubectl get pods,pvc
kubectl logs multi-volume-pod -c log-processor
kubectl logs multi-volume-pod -c content-updater
kubectl port-forward multi-volume-pod 8080:80
# Visit http://localhost:8080 to see the updated content