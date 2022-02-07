# On-Premises Microservice ARCHITECTURE #

*DMZ Zone:*

This layer consists of consumers such as mobile apps, web applications and third-party services, as it is a hosted on-premises all DMZ zone traffic will be routed through web application firewall (f5).

*Data Center:*

First layer of this architecture mainly has components to route requests to specific consumers, load balance them and cache the response. 
Static data (such as images, text files etc.) and service response will be cached for optimal performance. Redis or Memcached provide in-memory caching.
API Gateway and middleware (Laravel, Django, Flask) is for the client to access microservices. All cross-cutting functionalities like security, load balancing, governance, protocol transformation, analytics, performance management, payload communicates through the gateway.

*Security:*

DMZ firewall (not mandatory, can be eliminated to reduce cost) to inspect malicious traffic and have more control over network traffic. 
Authentication service, authorization service and in the OAuth 2.0 model, we will have time-based tokens (JWT/OpenID Connect) for secured resource access to the VMware infra.

*VMWare Infra:*

This VMWare Infra will be container ecosystem. Container images are the preferred deployment units of microservices. The container eco-system mainly provides a container orchestrator (such as Kubernetes) which manages the lifecycle of containers.

The cluster management module is responsible for managing various container clusters such as blue/ green clusters. Also, a local Image repository (not mandatory but good to have) for the users will be integrated. Also Based on the container’s availability, traffic volume and health status, the load balancer evenly distributes the load to various containers.

*DevOps:*

The DevOps module includes components for release management, automated deployments, continuous build, deployment pipeline, source control management and provisioning.

*Monitoring:*

The monitoring and notification infrastructure includes components for configuring SLA thresholds (CPU, memory, response times etc.), health check monitoring (monitoring system and service availability, performance), threshold-based alerting and notification, monitoring dashboard, availability reports and others.


