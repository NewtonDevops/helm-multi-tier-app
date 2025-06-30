# 🛠️ Multi-Tier Kubernetes App with Helm

This project demonstrates how to deploy a multi-tier application using **Helm charts** on a local **Minikube** cluster. It includes a Python-based backend, an NGINX frontend, test pods for internal communication, and optional network policies and ingress.

---

## 📦 Project Structure

```bash
multi-tier-app/
├── Chart.yaml               # Root Helm chart
├── values.yaml              # Global default values
├── charts/                  # Subcharts for each component
│   ├── backend/             # Backend chart
│   ├── frontend/            # Frontend chart
│   ├── testbox-allow/       # Internal access pod (allowed)
│   └── testbox-deny/        # Internal access pod (denied)
```

#### Install Helm if not installed:

```bash
# macOS
brew install helm

# Ubuntu/Debian
sudo apt-get install helm
```

## 🔧 Deploy with Helm

Clone the project:

```bash
git clone https://github.com/NewtonDevops/helm-multi-tier-app.git
cd helm-multi-tier-app
```

## Cleanup

Confirm that the previous deployments exist

```bash
kubectl get all
```
The output should be similar to this

``` pgsql
NAME                                 READY   STATUS    RESTARTS   AGE
pod/backend-78b696fbd4-cxvnh         1/1     Running   0          20m
pod/frontend-79fd6696c-gh758         1/1     Running   0          17m
pod/testbox-allow-6f889c4dc6-hjnwr   1/1     Running   0          14m

NAME               TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)    AGE
service/backend    ClusterIP   10.97.240.7      <none>        8080/TCP   26m
service/frontend   ClusterIP   10.100.149.105   <none>        80/TCP     18m

NAME                            READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/backend         1/1     1            1           20m
deployment.apps/frontend        1/1     1            1           17m
deployment.apps/testbox-allow   1/1     1            1           14m

NAME                                       DESIRED   CURRENT   READY   AGE
replicaset.apps/backend-78b696fbd4         1         1         1       20m
replicaset.apps/frontend-79fd6696c         1         1         1       17m
replicaset.apps/testbox-allow-6f889c4dc6   1         1         1       14m

```

Delete all the deployments and services

```bash
  kubectl delete deployment backend frontend testbox-allow
  kubectl delete service backend frontend
```
Wait for a few seconds and reconfirm that you have deleted all the deployments and services

```bash
kubectl get all
```
Output should be similar to the below

```pgslq
No resources found in adv-net-lab namespace.
```

Install the chart:

```bash
helm install demo . 
```
Check deployed resources:

```bash
kubectl get all -n adv-net-lab

```

---

## 👨‍💻 Author

**Newton Bii**  
Engineering Manager | DevOps | Kubernetes Trainer | Cloud Engineer  
[GitHub: NewtonDevops](https://github.com/NewtonDevops)  
[LinkedIn](https://www.linkedin.com/in/newton-bii-engineer/)

---

## 📄 License

This project is licensed under the terms of the **MIT License**.

You are free to use, modify, and redistribute this software for educational, personal, or commercial purposes with proper attribution.

See the [LICENSE.md](./LICENSE.md) file for full license text.
