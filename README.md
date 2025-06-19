# 📘 Kubernetes `kind` Cheatsheet

In Kubernetes manifest files, the `kind` field defines the **type of object** you're creating. Below is a categorized reference with brief explanations and usage.

---

## 🔹 Core Resources (`apiVersion: v1`)

| Kind                  | Purpose                                                        |
|-----------------------|----------------------------------------------------------------|
| `Pod`                | Smallest unit in K8s. Runs one or more containers.              |
| `Service`            | Exposes Pods over the network with a stable endpoint.           |
| `ConfigMap`          | Injects non-sensitive configuration data into containers.       |
| `Secret`             | Injects sensitive info (e.g., API keys, passwords).             |
| `PersistentVolume`   | Represents a piece of cluster storage.                          |
| `PersistentVolumeClaim` | Requests storage from a PV.                                 |
| `Namespace`          | Isolates groups of resources in the cluster.                    |

---

## ⚙️ Workload Controllers (`apiVersion: apps/v1`)

| Kind           | Purpose                                                            |
|----------------|--------------------------------------------------------------------|
| `Deployment`   | Manages Pods and ReplicaSets. Handles scaling and rolling updates. |
| `ReplicaSet`   | Ensures a specified number of Pod replicas are running.            |
| `StatefulSet`  | Like Deployment but with **stable IDs** and **persistent storage**.|
| `DaemonSet`    | Runs one Pod per node. Useful for log agents, monitoring.          |
| `Job`          | Runs Pods until successful completion. For batch jobs.             |
| `CronJob`      | Runs Jobs on a cron-like schedule.                                 |

---

## 🌐 Networking (`apiVersion: networking.k8s.io/v1`)

| Kind              | Purpose                                                          |
|-------------------|------------------------------------------------------------------|
| `Ingress`         | Routes HTTP(S) traffic to Services using rules.                  |
| `NetworkPolicy`   | Controls allowed network traffic to/from Pods.                   |

---

## 🔐 RBAC & Security (`apiVersion: rbac.authorization.k8s.io/v1`)

| Kind                  | Purpose                                                    |
|-----------------------|------------------------------------------------------------|
| `ServiceAccount`      | Associates an identity for Pods to access API resources.   |
| `Role` / `ClusterRole`| Defines permissions for resources (namespaced/global).     |
| `RoleBinding` / `ClusterRoleBinding` | Grants Roles to users or service accounts. |

---

## 🧰 Other Useful Types

| Kind             | Purpose                                         |
|------------------|-------------------------------------------------|
| `ResourceQuota`  | Limits resource usage per namespace.            |
| `LimitRange`     | Sets default CPU/memory limits for Pods.        |
| `HorizontalPodAutoscaler` | Auto-scales Pods based on metrics.   |

---

## 💡 Example Structure

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
    - name: my-container
      image: nginx
```
# Enable ingress
#  minikube addons enable ingress

# Deploy everything
#  kubectl apply -f .

# Add to hosts file
#  echo "$(minikube ip) k8s-playground.local" | sudo tee -a /etc/hosts

# Or use port-forward for quick access
#  kubectl port-forward service/web-service 8080:80 -n playground