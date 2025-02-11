# Docker Stack Deployment Example
This repository explains how to deploy a Docker Stack using Docker Swarm. Docker Stack allows you to manage multiple services as a single deployment, making it easier to orchestrate complex applications.

### What is Docker Stack?
Docker Stack is a feature of Docker Swarm that allows you to deploy and manage multiple services (microservices) using a single command and a Docker Compose file. It’s primarily used for orchestrating applications in a cluster of Docker nodes. In simpler terms:
- Instead of managing individual services manually, you can manage an entire application (frontend, backend, database, etc.) as a single unit.
- Docker Stack works like docker-compose, but for production environments on a Swarm cluster.

### Key Concepts of Docker Stack 
1. Service
    A service is a definition of a running container in a distributed application.
    Example: A web service running multiple replicas of an Nginx container.
2. Task
    A task is a single running container managed by Swarm. Each service is composed of multiple tasks.
3. Overlay Network
   Used to connect services across multiple nodes. Docker automatically creates these networks for stack services.
4. Desired State
   Docker Swarm ensures services are always running in their desired state (e.g., replicas, configuration).

### How Docker Stack Works
1. Define your application stack in a docker-compose.yml file.
   Example: A stack with a web service and a Redis cache.
2. Deploy the stack using docker stack deploy.
3. Swarm schedules and distributes services across nodes in the cluster.
4. Monitor and manage the stack using docker stack and docker service commands.

### When to Use Docker Stack?
- Production environments for microservices-based applications.
- When high availability and fault tolerance are needed.
- To deploy complex applications with multiple interconnected services (frontend, backend, database, etc.).

### When NOT to Use Docker Stack?
- For local development: Use docker-compose instead.
- If you don’t need orchestration or scaling.
- In environments where Kubernetes is the standard for orchestration.

## Example Workflow 🌐
**Step-1** Create a docker-compose.yml and other required files in a separate directory

**Step-2** Deploy the stack:

```docker stack deploy --compose-file docker-compose.yml stackdemo```


**Step-3** Monitor services:
```docker stack services stackdemo```

**Step-4** Scale the web service:
```docker service scale stackdemo_web=5```

**Step-5** Remove the stack:
```docker stack rm stackdemo```
