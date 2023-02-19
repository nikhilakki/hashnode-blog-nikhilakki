# Container Orchestration - Kubernetes 101

### What is Container management?

Container management is the process of organizing, deploying, and maintaining containers that run applications. Containers are a lightweight and portable way to package an application and its dependencies into a single unit that can run consistently across different environments. Container management involves tasks such as provisioning and configuring containers, scaling containers up or down, monitoring and logging the behaviour of containers, and ensuring the availability and performance of containers.

In the context of Kubernetes, container management refers to the process of using Kubernetes to automate and simplify the deployment, scaling, and management of containers in a cluster. This includes tasks such as defining and updating the desired state of an application and its containers, ensuring the availability and performance of containers, and rolling out updates to containers in a controlled and predictable way. By automating these tasks, Kubernetes allows organizations to focus on building and delivering their applications, rather than managing the underlying infrastructure.

### Intro to K8s

Kubernetes (often abbreviated as "k8s") is an open-source platform for automating deployment, scaling, and management of containerized applications. It provides a way to orchestrate containers, which are a way to package software applications, so they run consistently across different environments and provide high availability, resilience and scaling. Kubernetes provides features such as self-healing, automatic rollouts and rollbacks, and service discovery and load balancing, making it a popular choice for deploying applications in production environments.

### How does it work?

Kubernetes works by dividing an application into smaller, independently deployable components called "pods." These pods contain one or more containers, which run the actual application code. The pods are managed by higher-level constructs in Kubernetes, such as "replication controllers," which ensure that a specified number of replicas of the pods are running at all times.

Kubernetes also manages network communication between the pods, providing a unique IP address for each pod and allowing pods to communicate with each other using a private, internal network. Services can be defined to group a set of pods and provide load balancing and discovery, making it easy to access the components of your application.

In addition, Kubernetes allows you to declaratively manage the desired state of your application, using manifests that describe how your application should be deployed, what resources it requires, and how it should respond to failures. The Kubernetes control plane then continuously compares the actual state of the application with the desired state and makes changes to bring the two in line with each other.

Overall, Kubernetes provides a unified platform for managing and scaling containerized applications, making it easier to deploy and maintain complex, multi-tier applications in production.

### A simpler explanation -

Kubernetes is a tool that helps people run their computer programs smoothly.

Think of computer programs like cars that have a job to do. For example, one car might have to deliver packages, and another car might have to show pictures. When you have many cars, it can be difficult to make sure they all work together and have everything they need to do their job. That's where Kubernetes comes in.

Kubernetes helps all the cars work together smoothly and makes sure they have enough fuel and a good map. It also helps fix any problems that come up, so the cars can keep delivering packages and showing pictures without any trouble. In other words, Kubernetes helps people run their computer programs smoothly, just like a helper would.

### How to interact with K8s?

To configure and deploy applications in Kubernetes, you need to write a manifest file that describes the desired state of your application. The manifest file includes information about the containers that make up your application, the resources they need, and how they should be organized.

Once you have written your manifest file, you can use the `kubectl` command-line tool to deploy your application to a Kubernetes cluster. The `kubectl apply` command is used to deploy the manifest file to the cluster and create the resources described in the file. For example:

```bash
kubectl apply -f path/to/your/manifest.yml
```

The cluster will then make sure that the specified resources are created and maintained in the desired state. If anything changes, such as a container going down or a resource running low on memory, the cluster will automatically take action to fix the issue and restore the desired state.

You can also use `kubectl get` to view the status of your deployed resources, and `kubectl delete` to delete resources when you no longer need them.

This is a high-level overview of deploying applications in Kubernetes. There is much more to learn about configuring and deploying applications in a production environment, including concepts like scaling, rolling updates, and self-healing.

### K8s manifest YAML example

Here's a simple manifest for deploying a web application in Kubernetes:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-web-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-web-app
  template:
    metadata:
      labels:
        app: my-web-app
    spec:
      containers:
      - name: my-web-app
        image: myregistry/my-web-app:latest
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: my-web-app
spec:
  selector:
    app: my-web-app
  ports:
  - name: http
    port: 80
    targetPort: 80
  type: ClusterIP
```

This manifest deploys a `Deployment` with 3 replicas of a container running the latest version of `my-web-app` image. The replicas are selected using the label `app: my-web-app`. The manifest also creates a `Service` that makes the deployment accessible from within the cluster using a ClusterIP. The service listens on port 80 and maps it to the container's port 80.

### Closing thoughts

Kubernetes is a powerful and flexible platform for managing containerized applications at scale. It enables organizations to automate the deployment, scaling, and management of their applications, which saves time and reduces the risk of errors. The platform's growing popularity and ecosystem of tools and services have made it an essential part of modern application development and infrastructure.

However, like any complex platform, Kubernetes requires a steep learning curve and can be challenging to set up and maintain in a production environment. It's important to carefully consider your organization's needs and choose the right set of tools and services for your specific use case.

In conclusion, Kubernetes is a valuable tool for organizations that want to streamline the management of their containerized applications and take advantage of the benefits of cloud-native computing. Whether you're a developer, DevOps engineer, or infrastructure administrator, understanding how to use Kubernetes is an important part of modern application development and operations.