
# expene -project with volume and statefull set

1>.....Create expense Namespace

```

apiVersion: v1
kind: Namespace
metadata:
  name: expense
  labels:
    project: expense
    environment: dev
    ```

2>.... Install EBS Driver

```

3>.... Create EBS storage class

