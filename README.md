# CLO835-Final-Project

### Add your aws credentials as repository secrets

### Automatically push images to Amazon ECR by making any change that doesn't affect the functionality

### Clone this repo and switch to manifest dir

### Create namespace
```kubectl create ns final```

### Create configmap
```kubectl apply -f configmap.yaml -n final```

### Create Secrets
```kubectl apply -f secrets.yaml -n final```

### Create PVC
```kubectl apply -f pvc.yaml -n final```

### Create serviceaccount
```kubectl apply -f serviceaccount.yaml -n final```

### Create clusterrole
```kubectl apply -f clusterrole.yaml```


### Create clusterrolebinding
```kubectl apply -f clusterrolebinding.yaml```


### Create application pod
```kubectl apply -f web-pod.yaml -n web```


### Create database deployment
```kubectl apply -f db-deployment.yaml -n final```

### Create cluster ip service for database deployment
```kubectl apply -f db-service.yaml -n final```

### Create application deployment
```kubectl apply -f app-deployment.yaml -n final```

### Create loadbalancer service for app deployment
```kubectl apply -f app-service.yaml -n final```

### Deploy metrics server
```kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.5.0/components.yaml```

### Set the cpu resource request for app deployment to 50m 
```kubectl set resources deploy app -n final --requests=cpu=50m```

### Deploy the HPA that will increase the no. of replicas upto 10 if cpu utiliztion increases by 50%
```kubectl autoscale deployment app --cpu-percent=50 --min=1 --max=10 -n final```

### Deploy the HPA that will scale the workload if cpu utiliztion increases by 50%
```kubectl autoscale deployment app --cpu-percent=50 --min=1 --max=10 -n final```
