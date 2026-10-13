# Kubernetes RBAC and Service Accounts

Konfiguracja Service Account, Role, RoleBinding, ClusterRole i ClusterRoleBinding w Kubernetes.

## Wykorzystane narzędzia
- Visual Studio Code
- Docker Desktop
- Kubernetes
- kubectl

## Struktura manifestów
- `namespace.yaml` – namespace app-dev
- `service-account.yaml` – konto cicd-bot
- `role.yaml `– uprawnienia do Deploymentów, ReplicaSetów i Podów
- `role-binding.yaml `– przypisanie roli do cicd-bot
- `cluster-role.yaml` – odczyt zasobów Nodes
- `cluster-role-binding.yaml` – przypisanie ClusterRole użytkownikowi developer

## Wdrożenie
```bash
kubectl apply -f manifests/namespace.yaml
kubectl apply -f manifests/service-account.yaml
kubectl apply -f manifests/role.yaml
kubectl apply -f manifests/role-binding.yaml
kubectl apply -f manifests/cluster-role.yaml
kubectl apply -f manifests/cluster-role-binding.yaml
```

## Weryfikacja
```bash
kubectl get serviceaccount -n app-dev
kubectl get role,rolebinding -n app-dev
kubectl get clusterrole node-reader
kubectl get clusterrolebinding node-reader-binding
```

## Rezultat
Przygotowano manifesty YAML definiujące uprawnienia lokalne w namespace app-dev oraz uprawnienia do odczytu węzłów w skali klastra.