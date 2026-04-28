# Docker on Red Hat Developer
## Build
```
docker build -t spring-boot-axon .
```
## Run with environment variable
```
docker run -p 8080:8080 spring-boot-axon
```
## Tag and push to Docker Hub
```
docker tag spring-boot-axon chriswongatcuhk/spring-boot-axon
docker push chriswongatcuhk/spring-boot-axon
```
## The Fix: Multi-Platform Build
```
docker build --platform linux/amd64 -t chriswongatcuhk/spring-boot-axon .
docker push chriswongatcuhk/spring-boot-axon
```

## Logs
Logs 標籤頁也就不會再消失了
```
oc get ksvc
oc patch ksvc spring-boot-axon --type merge -p '{"spec":{"template":{"metadata":{"annotations":{"autoscaling.knative.dev/minScale":"1"}}}}}'
```