---
title: "Serverless Series | AWS Fargate 101"
datePublished: Sun Feb 26 2023 05:59:39 GMT+0000 (Coordinated Universal Time)
cuid: clekzed8j00v1d2nvhhnpb4zo
slug: serverless-series-aws-fargate-101
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1675748753155/046b6526-3243-4aa7-8230-d2c562686c7e.png
tags: aws, kubernetes, fargate, aws-fargate, serverless-containers

---

### Intro

AWS Fargate is a serverless compute engine for containers that runs containers natively on Amazon Web Services (AWS) without the need to manage the underlying instances. It allows you to focus on building and running your applications, without the need to manage infrastructure. With Fargate, you specify the CPU and memory requirements of your tasks, and the AWS platform manages the underlying infrastructure for you, eliminating the need to manage and scale EC2 instances.

### Comparisons with AWS EKS & ECS

AWS Fargate can be compared to other AWS services that provide container management, such as Amazon Elastic Container Service (ECS) and Amazon Elastic Kubernetes Service (EKS).

Compared to ECS, Fargate is a more simplified option as it eliminates the need to manage the underlying instances and reduces the operational overhead of running containers. With Fargate, you only need to focus on building and deploying your applications, while the underlying infrastructure is managed by AWS.

Compared to EKS, Fargate provides a serverless option for running containers in Kubernetes. With EKS, you still need to manage the underlying EC2 instances, whereas, with Fargate, you do not. Fargate can be used as the compute engine for pods in EKS clusters, providing a serverless option for running containers in Kubernetes.

Here's a comparison table between AWS Fargate, ECS, and EKS:

| **Feature** | **AWS Fargate** | **Amazon ECS** | **Amazon EKS** |
| --- | --- | --- | --- |
| Simplicity | High | Moderate | Low |
| Serverless | Yes | No | No |
| Management of underlying infrastructure | AWS manages | User manages | User manages |
| Operations overhead | Low | Moderate | High |
| Scalability | AWS manages | User manages | User manages |
| Network connectivity | Moderate | High | High |

### Conclusion

Like most tools in software development, there is no silver bullet. AWS Fargate, Amazon ECS, and Amazon EKS are all services that provide container management on AWS. Fargate provides a simplified and serverless option for running containers, where the underlying infrastructure is managed by AWS, whereas ECS and EKS require the user to manage the underlying infrastructure. The choice between these services depends on the specific requirements, such as operational overhead, scalability, network connectivity, and management of the underlying infrastructure. Fargate can be a good option for users who want a simple and serverless solution, while ECS and EKS can be suitable for users who need more control and flexibility in their container management.

### Reference Links

%[https://aws.amazon.com/fargate/] 

%[https://www.cloudzero.com/blog/ecs-vs-eks]