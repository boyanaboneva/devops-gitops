# devops-gitops

This is the GitOps repo, which relates to DevOps-service repo.

## Kubernetes deployment

Deployments files are in another repo: https://github.com/boyanaboneva/devops-gitops

Create another namespace, e.g. 'application':
```shell
kubectl create namespace application
```

To create a config map with environment variables navigate to the file in the gitops repo via terminal:
```shell
kubectl apply -f env_fastapi_configmap.yml
```

Using terminal navigate to the kubernetes deployment folder in the gitops repo. Apply the 'deployment.yml' file in the
newly created namespace, e.g. 'application':
```shell
kubectl apply -f deployment.yml -n application
```
The response should look like this:
```shell
deployment.apps/fast-api-deployment created
```

To check everything is applied, get the pods of this namespace:
```shell
kubectl get pods -n application
```
The response should look like this:
```shell
NAME                                   READY   STATUS    RESTARTS   AGE
fast-api-deployment-66ff55bb64-cmkbl   1/1     Running   0          22s
```

Using terminal navigate to the kubernetes deployment folder in the gitops repo. Apply the 'service.yml' file in the
newly created namespace, e.g. 'application':
```shell
kubectl apply -f service.yml -n application
```
The response should look like this:
```shell
service/fastapi-service configured
```
