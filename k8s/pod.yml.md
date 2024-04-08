```bash
apiVersion: v1
kind: Pod
metadata:
  name: flipkart
spec:
  containers:
  - name: c00
    image: centos
    command: ["/bin/bash", "-c", "sleep 15000"]
    volumeMounts:
      - name: sandisk
        mountPath: "/tmp/qspider"
  - name: c01
    image: centos
    command: ["/bin/bash", "-c", "sleep 10000"]
    volumeMounts:
      - name: sandisk
        mountPath: "/tmp/jspider"
  volumes:
  - name: sandisk
    emptyDir: {}
```
