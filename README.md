# 22-k8-learn-service-accounts

# Commands to apply
- kubectl apply -f namespace.yaml
- kubectl apply -f service-account.yaml
- kubectl apply -f role.yaml
- kubectl apply -f role-binding.yaml
- kubectl apply -f pod.yaml
- kubectl -n sa-exercise exec -it sa-test-pod -- sh
- export TOKEN=$(cat /var/run/secrets/kubernetes.io/serviceaccount/token)
- curl -k https://kubernetes.default.svc/api/v1/namespaces/sa-exercise/pods \
  --header "Authorization: Bearer $TOKEN"


# How to generate templates on the commandline
- kubectl run my-pod --image=nginx --dry-run=client -o yaml > pod-template.yaml
- kubectl create deployment my-deployment --image=nginx --dry-run=client -o yaml
- kubectl create rolebinding my-rolebinding --role=role-name \ --serviceaccount=default:my-serviceaccount --dry-run=client -o yaml
