<div align="center">

<img src="https://img.shields.io/badge/Course-INT332-0ea5e9?style=for-the-badge&logoColor=white" />
<img src="https://img.shields.io/badge/Credits-3-7c3aed?style=for-the-badge" />
<img src="https://img.shields.io/badge/Session-2025--26-10b981?style=for-the-badge" />
<img src="https://img.shields.io/badge/L:2%20T:0%20P:2-Schedule-f59e0b?style=for-the-badge" />

# 🐳 DevOps Virtualization & Configuration Management

> **INT332** · A complete guide to containerization, CI/CD pipelines, and modern DevOps tooling — from Docker fundamentals to Jenkins automation.

</div>

---

## 📋 Course Outcomes

| # | Outcome |
|---|---------|
| `CO1` | Explain DevOps infrastructure concepts including containerization, runtimes, process isolation, namespaces, and resource management mechanisms |
| `CO2` | Apply Docker concepts to build, manage, and distribute container images using networking, storage, and registries |
| `CO3` | Construct microservices applications using Docker Compose with multi-container services and dependency configuration |
| `CO4` | Analyze and implement automated builds using Maven through lifecycle management, dependency control, plugins, and Docker integration |
| `CO5` | Apply Continuous Integration workflows using GitHub Actions for automated builds, testing, image creation, and deployment |
| `CO6` | Develop end-to-end CI/CD pipelines using Jenkins integrating source control, build tools, containers, and deployments |

---

## 📚 Syllabus

<details>
<summary><b>🔵 Unit I — Basics of DevOps Infrastructure</b></summary>

<br>

### 🧱 Containerization Concepts
- Origin of containers & emergence of modern containerization
- Integration of DevOps with containerization
- Container runtime & process isolation
- **Namespaces** — isolation of processes, networking, filesystem
- **Control Groups (cgroups)** — resource limits and management

### 🐳 Docker Fundamentals
- Introduction to Docker & Docker Architecture
- Docker Daemon, Docker CLI
- Docker Registry & Hub
- Container Images & Layers
- Image Registries & Distribution

### 📦 Docker Object Types
| Object | Description |
|--------|-------------|
| `container` | Running instance of an image |
| `image` | Read-only template for containers |
| `network` | Communication between containers |
| `volume` | Persistent data storage |
| `layer` | Incremental filesystem changes |

</details>

---

<details>
<summary><b>🟣 Unit II — Image Building & Container Management</b></summary>

<br>

### 📝 Dockerfile Core Instructions
```dockerfile
FROM        # Base image
RUN         # Execute commands during build
COPY / ADD  # Copy files into image
CMD         # Default command at runtime
ENTRYPOINT  # Fixed entrypoint command
WORKDIR     # Set working directory
ENV         # Environment variables
EXPOSE      # Document exposed ports
VOLUME      # Mount point declaration
```

### 🔍 Image Creation & Inspection
- Build context & `.dockerignore`
- Image layering & writing efficient Dockerfiles
- Tagging & Versioning images
- Inspecting images: `history`, `layers`

### 🌐 Docker Networking
| Type | Use Case |
|------|----------|
| **Bridge** | Default container-to-container |
| **Host** | Share host network stack |
| **Overlay** | Multi-host networking |

- DNS inside Docker
- Linking containers
- Port mapping between host and container

### 💾 Storage & Registries
- **Volumes** vs **Bind Mounts** — backing data on host
- Copy-on-write mechanism
- Registries: Docker Hub · **GHCR** · Private Registries
- Authentication & Access Tokens

</details>

---

<details>
<summary><b>🟢 Unit III — Microservices with Docker Compose</b></summary>

<br>

### 🏗️ Microservices Architecture
- Monolithic vs Microservices — scalability, isolation, agility
- API Gateway pattern
- Advantages: independent deployment, fault isolation, tech diversity

### 🔧 Docker Compose
```yaml
version: "3.9"
services:
  app:
    build: .
    environment:
      - NODE_ENV=production
    depends_on:
      - db
  db:
    image: postgres:15
    volumes:
      - db_data:/var/lib/postgresql/data
volumes:
  db_data:
```

Key concepts:
- YAML structure: `version`, `services`, `volumes`, `networks`
- Environment variables, Secrets & Configs
- Build vs image fields in YAML
- Service dependency ordering (`depends_on`)

### 🚀 Multi-Container Use Cases
| Stack | Components |
|-------|-----------|
| **WordPress** | WordPress + MySQL |
| **Node.js App** | Node.js + MongoDB |
| **Java App** | Spring Boot + PostgreSQL |
| **Full Stack** | Docker + Backend + Frontend |

</details>

---

<details>
<summary><b>🟡 Unit IV — Maven Build Automation</b></summary>

<br>

### 📐 Maven Fundamentals
- Why build tools exist — problems solved by automated builds
- **Project Object Model (POM)** & directory structure
- Parent POM — inheriting configurations
- Dependency scope & transitive dependencies
- Version conflicts & resolution

### 🔄 Build Lifecycle Phases
```
validate → compile → test → package → verify → install → deploy
```

### 🔌 Key Plugins
| Plugin | Purpose |
|--------|---------|
| `maven-compiler-plugin` | Compile Java source |
| `maven-surefire-plugin` | Run unit tests |
| `maven-shade-plugin` | Create uber/fat JAR |
| `maven-wrapper (mvnw)` | Consistent Maven version |

### 🐳 Maven & Docker Integration
- Dockerfile-maven-plugin
- Building Docker images via Maven
- Pushing artifacts to registries

</details>

---

<details>
<summary><b>🔴 Unit V — Continuous Integration with GitHub Actions</b></summary>

<br>

### ⚙️ Workflow Architecture
```
.github/
└── workflows/
    └── ci.yml
```

Key components: **Events → Triggers → Jobs → Steps → Actions**

### 🔔 Workflow Triggers
```yaml
on:
  push:
    branches: [main]
  pull_request:
  schedule:
    - cron: '0 0 * * *'
  workflow_dispatch:   # manual trigger
```

### 🧩 Jobs & Strategies
- Jobs, steps, actions, runners
- **Matrix strategies** for multi-version testing
- Shell commands & marketplace actions
- Language-specific actions

### 🏃 Runners
| Type | Description |
|------|-------------|
| **GitHub-hosted** | Managed by GitHub (ubuntu, windows, macos) |
| **Self-hosted** | Your own infrastructure |

- Runner security & management
- Jobs & matrix strategies

### 🐳 Docker & CI Deployments
```yaml
- name: Build & Push Docker Image
  uses: docker/build-push-action@v5
  with:
    push: true
    tags: ghcr.io/${{ github.repository }}:latest
```

- Build Docker images in CI
- Caching for faster builds
- Multi-job workflows
- Push to **Docker Hub** / **GHCR**
- Deploy to servers/cloud using Actions

</details>

---

<details>
<summary><b>🟥 Unit VI — CI/CD with Jenkins</b></summary>

<br>

### 🏛️ Jenkins Foundations
- **Architecture**: Master/Agent model
- Installation & UI Overview
- Plugins management
- Security: users, roles, permissions

### 🛠️ Jenkins Pipelines
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker push myapp:latest'
            }
        }
    }
}
```

- **Freestyle** vs **Pipeline** jobs
- Declarative & Scripted pipeline syntax
- Jenkinsfile structure, Parameters, Environment variables
- Multi-branch pipelines

### 📊 Pipeline Stages
`Checkout` → `Build` → `Test` → `Package` → `Manage Artifacts` → `Post Actions`

### 🐳 Docker & Maven Integration
- Building Docker images using Jenkins
- Docker inside Jenkins agents
- Using Docker plugins
- Publishing images to **Docker Hub / GHCR**
- Jenkins & Maven builds — global tool configuration
- Running Maven builds in pipelines

### 🚀 Advanced CI/CD
- Code coverage & test reports
- Backup & restore
- Pipeline best practices
- **Deployment Flows**: `pollSCM`, `webhook`
- Pipeline libraries
- Jenkins agents: SSH · SFTP · Container-based
- Deployments to servers/cloud

</details>

---

## 🛠️ Tools & Technologies

<div align="center">

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=flat-square&logo=apachemaven&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![GHCR](https://img.shields.io/badge/GHCR-181717?style=flat-square&logo=github&logoColor=white)

</div>

---

<div align="center">
<sub>INT332 · DevOps Virtualization & Configuration Management · Session 2025-26</sub>
</div>
