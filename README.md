# DevOps Project README

## Terraform Setup

1. **Initialize Terraform:** `terraform init`
2. **Validate Configuration:** `terraform validate`
3. **Plan Infrastructure Changes:** `terraform plan -out tfplan`
4. **Apply Changes:** `terraform apply tfplan`

## Kubernetes Setup

1. **Update kubeconfig for EKS:**
   ```bash
   aws eks update-kubeconfig --region us-east-1 --name ascode-cluster
    ```
2. Verify Nodes:
   ```bash
   kubectl get nodes
   ```
3. Deploy Test Pod:
  ```bash
    kubectl run testpod --image=nginx
  ```
4. Monitor Pods:
```bash
   kubectl get pods --watch
  ```

## Docker Image Building and Pushing

Build Frontend Image:

```bash

sudo docker build -t frontend-image -f /home/ubuntu/code/flask-react-todo/Frontend-Dockerfile .
```
Build Backend Image:

```bash

sudo docker build -t backend-image -f /home/ubuntu/code/flask-react-todo/Backend-Dockerfile .
```
Login to Docker Hub: 

```
docker login -u rahulpatil1997
```

Push Frontend Image:
```bash
docker tag frontend-image rahulpatil1997/frontend
docker push rahulpatil1997/frontend
```


Push Backend Image:
```bash
docker tag backend-image rahulpatil1997/backend
docker push rahulpatil1997/backend
```

## Deploying the application
```bash
kubectl apply -f frontend-deployment.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f frontend-service.yaml
```
