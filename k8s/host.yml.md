```bash
apiVersion: v1
kind: Pod
metadata:
  name: demo
spec:
  containers:
  - image: centos
    name: sample
    command: ["/bin/bash", "-c", "sleep 15000"]
    volumeMounts:
    - mountPath: /tmp/hostpath
      name: sandisk
  volumes:
  - name: sandisk
    hostPath:
      path: /tmp/data
```
