# Docker on Red Hat Developer
## Build
```
docker build -t spring-boot-example .
```
## Run with environment variable
```
docker run -p 8080:8080 spring-boot-example
```
## Tag and push to Docker Hub
```
docker tag spring-boot-example chriswongatcuhk/spring-boot-example
docker push chriswongatcuhk/spring-boot-example
```
## The Fix: Multi-Platform Build
```
docker build --platform linux/amd64 -t chriswongatcuhk/spring-boot-example .
docker push chriswongatcuhk/spring-boot-example
```

## Logs
Logs 標籤頁也就不會再消失了
```
oc get ksvc
oc patch ksvc spring-boot-example --type merge -p '{"spec":{"template":{"metadata":{"annotations":{"autoscaling.knative.dev/minScale":"1"}}}}}'
```