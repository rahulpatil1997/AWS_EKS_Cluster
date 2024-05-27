## Deployment file
Pulling the docker images from Docker Registry.

```
    spec:
      containers:
      - name: backend
        image: rahulpatil1997/backend
```      

Horizontal Pod Scaling
```
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: backend-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: backend-deployment
  minReplicas: 1
  maxReplicas: 3
```



## Kubernetes Pod Deployment

Deploy the Frontend Service
```
kubectl apply -f frontend-deployment.yaml
kubectl apply -f frontend-service.yaml
```

Deploy the Backend Service
```
kubectl apply -f backend-deployment.yaml
```
