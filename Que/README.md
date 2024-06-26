If i have

```
apiVersion: batch/v1beta1
kind: CronJob
```

it will get convert into batch/v1

```
apiVersion: batch/v1
kind: CronJob
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"batch/v1beta1","kind":"CronJob","metadata":{"annotations":{},"labels":{"app.kubernetes.io/instance":"my-app"},"name":"hello","namespace":"default"},"spec":{"jobTemplate":{"spec":{"template":{"spec":{"containers":[{"command":["/bin/sh","-c","date; echo Hello from the Kubernetes cluster"],"image":"busybox:1.28","imagePullPolicy":"IfNotPresent","name":"hello"}],"restartPolicy":"OnFailure"}}}},"schedule":"* * * * *"}}
  creationTimestamp: "2024-06-26T03:40:56Z"
  generation: 1
  ```

  Que: Who does it? And Kubent says that if I apply same chart/manifest agaist k8s v>1.25 that will fail right?