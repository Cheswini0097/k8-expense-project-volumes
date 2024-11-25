HPA>>> Horizantal pod auto scaleing


two condtions to attach the HPA for the deployemnet

```
#condtion1
we should have installed the metrics in the server
```

#Installation
Metrics Server can be installed either directly from YAML manifest or via the official Helm chart. To install the latest Metrics Server release from the components.yaml manifest, run the following command.
```
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```


conditition2:
should mention the resource section in the  pod

```
spec:
      containers:
      - name: frontend
        image: joindevops/frontend:v1
        resources:
          requests:
            cpu: 100m
            memory: 128Mi
          limits:
            cpu: 100m
            memory: 128Mi
        ports:
        - containerPort: 80

```
 then can attach the Hpa for the deployemnet

 ```
 apiVersion: autoscaling/v1
kind: HorizontalPodAutoscaler
metadata:
 name: backend
 namespace: expense
spec:
 scaleTargetRef:
   apiVersion: apps/v1
   kind: Deployment
   name: backend
 minReplicas: 1
 maxReplicas: 10
 targetCPUUtilizationPercentage: 15 
 ```


 