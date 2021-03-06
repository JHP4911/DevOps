<div align="center">
  <h1> Service </h1>
</div>

![service](../images/service.gif)

### What is a Service in Kubernetes?

⚜ A Service enables network access to a set of Pods in Kubernetes. <br>
⚜ Services select Pods based on their labels. <br>
⚜ When a network request is made to the service, it selects all Pods in the cluster matching the service's selector, chooses one of them, and forwards the network request to it. <br>

**Official documentation** : https://kubernetes.io/docs/concepts/services-networking/service
