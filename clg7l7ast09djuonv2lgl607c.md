---
title: "What is API Gateway?"
datePublished: Sat Apr 08 2023 06:20:39 GMT+0000 (Coordinated Universal Time)
cuid: clg7l7ast09djuonv2lgl607c
slug: what-is-api-gateway
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678814310371/2b6bbe94-b85b-444e-a67e-d042b48a1943.png
tags: aws, azure, gcp, api-gateway, load-balancing

---

API Gateway is a service that allows developers to create, deploy, and manage APIs (Application Programming Interfaces) that provide secure access to backend services and applications.

API Gateway acts as a "front door" to your backend services, providing a central point of control for managing and monitoring your APIs. It enables you to define and manage your APIs, enforce security policies, throttle traffic, and monitor API usage.

API Gateway provides several key features:

1. **API creation and management**: API Gateway provides a graphical interface for creating and managing APIs. This allows developers to define the structure and behaviour of their APIs and control how they are accessed.
    
2. **Security**: API Gateway provides various security mechanisms to secure your APIs, including authentication and authorization, SSL/TLS encryption, and API keys.
    
3. **Traffic management**: API Gateway provides traffic management capabilities such as rate limiting, caching, and request/response transformation, which can help optimize API performance and reduce backend load.
    
4. **Monitoring and analytics**: API Gateway provides real-time monitoring and analytics, allowing you to track API usage, monitor performance, and identify issues.
    

API Gateway is commonly used in microservices architectures, where multiple services are composed into a larger application. It provides a single entry point for accessing these services, simplifying application development and management.

### Cloud managed offerings

There are several cloud-managed offerings for API Gateway available in the market. Here are some examples:

1. [**Amazon API Gateway**](https://aws.amazon.com/api-gateway/): Amazon API Gateway is a fully managed service provided by Amazon Web Services (AWS) that allows developers to create, deploy, and manage APIs at any scale.
    
2. [**GCP's API Gateway**](https://cloud.google.com/api-gateway): It is a distributed API management system that provides hosting, logging, monitoring and other features to help you create, share, maintain and secure your APIs. It is natively integrated with GCP and handles tasks such as traffic management, authorization and monitoring
    
3. [**Microsoft Azure API Management**](https://azure.microsoft.com/en-us/products/api-management/?azure-portal=true)
    
4. [**IBM API Connect**](https://www.ibm.com/products/api-connect)
    
5. [**Oracle API Gateway**](https://docs.oracle.com/en-us/iaas/Content/APIGateway/Concepts/apigatewayoverview.htm)
    

These cloud-managed offerings provide common features of API Gateway, including API creation and management, security, traffic management, and monitoring and analytics. They differ in pricing, ease of use, and integration with other cloud services, so it's important to evaluate each offering based on your specific needs and requirements.

### Reference architecture diagram (AWS)

![                API Gateway architecture diagram](https://docs.aws.amazon.com/images/apigateway/latest/developerguide/images/Product-Page-Diagram_Amazon-API-Gateway-How-Works.png align="left")

##### [Source link](https://docs.aws.amazon.com/apigateway/latest/developerguide/welcome.html)