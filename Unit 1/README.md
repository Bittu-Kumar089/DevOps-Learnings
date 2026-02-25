1️⃣ DevOps & Need of Docker

DevOps = Development + Operations collaboration.

Goal: faster deployment, automation, scalability.

Docker helps standardize application deployment.

👉 Docker simplifies software delivery and improves workflow. 

🏢 2️⃣ Virtualization vs Containerization
Virtualization

One physical server → many VMs.

Each VM has its own OS.

Heavy resource usage.

Containerization

Containers share host OS kernel.

Lightweight, fast startup.

Better portability.

👉 Containers evolved because VMs had overhead and slow performance. 

⚙️ 3️⃣ Need for Containers

Faster deployment

Less memory usage

Easy scalability

Supports microservices architecture

Runs many apps on same machine

Containers only include required dependencies, not full OS. 

🔧 4️⃣ Container Runtime

Container runtime = software that runs containers.

Examples:

Docker Engine

containerd

CRI-O

Functions:
✔ Create container
✔ Start/stop container
✔ Manage lifecycle 

🔐 5️⃣ Namespaces (Isolation)

Namespaces isolate containers.

Types:

PID → process isolation

Network → own IP & ports

Mount → filesystem isolation

UTS → hostname isolation

User → security mapping

👉 Containers appear like separate systems. 

⚡ 6️⃣ cgroups (Resource Control)

cgroups limit:

CPU

Memory

Disk I/O

Rule:

Namespaces = Isolation
cgroups = Resource Control

Prevents one container from crashing others. 

📦 7️⃣ Docker Images & Layers

Image = read-only blueprint.

Contains base OS + app + libraries.

Built using Dockerfile.

Each instruction = image layer.

Benefits:
✔ Faster builds
✔ Reusable layers
✔ Smaller storage 

🌐 8️⃣ Image Registry (Docker Hub / GHCR)

Registry = storage for images.

Naming format:

<registry>/<namespace>/<image>:<tag>

Importance:

Share images

Version control

CI/CD integration

👉 GHCR is a private registry example. 

🔄 9️⃣ Docker Workflow (Lifecycle)

Docker life cycle:

Build → Ship → Run

Build image

Push to registry

Pull & run container 

🐳 🔟 Docker Architecture

Main components:

Docker Client

Docker Daemon

Images

Containers

Registry

Docker daemon manages images & containers internally.
