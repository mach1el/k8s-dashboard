# k8s-dashboard
Deploy kubernetes dashboard

## Deploy the dashboard
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```

## Deploy rbac
```
kubectl apply -f rbac.yaml
```

## Deploy sa
```
kubectl apply -f sa.yaml
```

## Get token
```
kubectl -n kubernetes-dashboard get secret $(kubectl -n kubernetes-dashboard get sa/admin-user -o jsonpath="{.secrets[0].name}") -o go-template="{{.data.token | base64decode}}"
```
