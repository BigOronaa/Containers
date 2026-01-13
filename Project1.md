
# Research Questions on Containers and Containerization

## 1. What is the difference between a container and a virtual machine (VM)?

### Underlying Technology
- **Virtual Machines (VMs)** run on a hypervisor and include a full guest operating system with its own kernel.
- **Containers** share the host OS kernel and package only the application and its dependencies.

### Performance Considerations
- VMs consume more resources due to full OS overhead.
- Containers are lightweight, start faster, and allow higher density.

### Use Cases
- **VMs**: Legacy applications, strong isolation, multiple OS support.
- **Containers**: Microservices, CI/CD pipelines, cloud-native applications.

---

## 2. How does Docker ensure isolation between containers?

Docker uses Linux kernel features to provide isolation:

- **Namespaces**: PID, NET, MNT, UTS, USER
- **Control Groups (cgroups)**: Resource limits for CPU, memory, I/O
- **Union File Systems**: OverlayFS for layered images
- **Docker Daemon**: Manages lifecycle and enforces isolation

---

## 3. What are common container security risks and mitigations?

### Risks
- Running containers as root
- Vulnerable base images
- Exposed secrets
- Insecure networking

### Mitigations
- Use minimal base images
- Run containers as non-root
- Scan images using **Docker Scan**, **Trivy**, or **Clair**
- Apply least-privilege principles
- Use secrets managers

---

## 4. How do orchestration tools like Kubernetes complement Docker?

Kubernetes handles:
- Container scheduling
- Auto-scaling
- Self-healing
- Load balancing
- Rolling updates

Docker builds containers, while Kubernetes manages them at scale in production.

---

## 5. Advantages of multistage Docker builds

- Separate build and runtime environments
- Smaller image sizes
- Reduced attack surface
- Faster deployments

**Example**:
- Without multistage: ~700MB
- With multistage: ~100MB

---

## 6. How does Docker Compose manage networking?

- Creates a default bridge network
- Services communicate using service names
- Isolated networks per project

**Example**: `web` connects to `db:5432`

---

## 7. Differences between container registries

| Registry | Features | Security | Pricing |
|--------|--------|--------|--------|
| Docker Hub | Public/private images | Basic scanning | Free & paid |
| AWS ECR | AWS-native | IAM, encryption | Pay-as-you-go |
| GCP Artifact Registry | GCP-native | IAM, encryption | Usage-based |

---

## 8. Docker caching and build optimization

### How Caching Works
- Each instruction creates a layer
- Unchanged layers are reused
- Changes invalidate subsequent layers

### Best Practices
- Order instructions strategically
- Copy dependency files first
- Use `.dockerignore`
- Leverage multistage builds
- Pin image versions

---

## Conclusion

Containers enable efficient, scalable application deployment. Docker simplifies container creation, Kubernetes enables orchestration, and best practices ensure security and performance.
