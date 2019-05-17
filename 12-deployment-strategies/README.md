# Deployment Strategies

## Rolling Deployment

1. `cat rolling-deployment/nginx.yaml`
2. `kubectl apply -f rolling-deployment/nginx.yaml`
4. `kubectl run -i -t busybox --image=busybox --restart=Never --rm -- sh -c 'watch -n 1 wget -O - nginx'`
5. `kubectl edit deploy nginx`
6. `kubectl run -i -t busybox --image=busybox --restart=Never --rm -- sh -c 'watch -n 1 wget -O - nginx'`
7. `kubectl delete -f rolling-deployment/nginx.yaml`

## Canary Deployment

1. `cat canary-deployment/nginx.yaml`
2. `kubectl apply -f canary-deployment/nginx.yaml`
3. `kubectl get deploy,po,svc -o wide --show-labels`
4. `kubectl run -i -t busybox --image=busybox --restart=Never --rm -- sh -c 'watch -n 1 wget -O - nginx'`
5. `kubectl delete -f canary-deployment/nginx.yaml`

## Blue-Green Deployment

1. `cat blue-green-deployment/nginx.yaml`
2. `kubectl apply -f blue-green-deployment/nginx.yaml`
3. `kubectl get deploy,po,svc -o wide --show-labels`
4. `kubectl run -i -t busybox --image=busybox --restart=Never --rm -- sh -c 'watch -n 1 wget -O - nginx'`
5. `kubectl edit svc nginx`
5. `kubectl delete -f blue-green-deployment/nginx.yaml`
