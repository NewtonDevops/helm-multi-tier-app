# 🛠️ Multi-Tier Kubernetes App with Helm

This project demonstrates how to deploy a multi-tier application using **Helm charts** on a local **Minikube** cluster. It includes a Python-based backend, an NGINX frontend, test pods for internal communication, and optional network policies and ingress.

---

## 📦 Project Structure

```bash
multi-tier-app/
├── Chart.yaml                # Root Helm chart
├── values.yaml              # Global default values
├── charts/                  # Subcharts for each component
│   ├── backend/             # Backend chart
│   ├── frontend/            # Frontend chart
│   ├── testbox-allow/       # Internal access pod (allowed)
│   └── testbox-deny/        # Internal access pod (denied)
├── templates/
│   ├── ingress.yaml         # Ingress routing
│   └── networkpolicy.yaml   # NetworkPolicy (optional)
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
```

Install the chart:

```bash
helm install multi-tier ./multi-tier-app -n adv-net-lab --create-namespace
```
Check deployed resources:

```bash
kubectl get all -n adv-net-lab

```
