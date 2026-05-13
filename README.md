# Unit 5 – Continuous Integration with GitHub Actions ⚙️🚀🐳

This branch contains the practical work, notes, screenshots, and documentation related to **Unit 5: Continuous Integration (CI) with GitHub Actions**.

The focus of this unit is to understand **workflow automation**, **CI/CD pipelines**, and integration of **Docker with GitHub Actions** to automate application builds and deployments.

This unit helps build practical knowledge required for **modern DevOps automation workflows**.

---

# 🔍 Topics Covered in Unit 5

## ⚙️ Continuous Integration with GitHub Actions

- Introduction to Continuous Integration (CI)  
- Understanding workflow automation  
- Events and triggers  
- Workflow directory structure  

### Key Components of GitHub Actions

- Workflows  
- Jobs  
- Steps  
- Actions  
- Runners  

---

## 🔔 Workflow Triggers

Different types of triggers used in workflows:

- push trigger  
- pull request trigger  
- schedule trigger  
- manual workflow trigger  

Understanding how workflows automatically run based on events.

---

## 🧩 Jobs and Steps

- Understanding jobs in workflows  
- Running multiple steps inside jobs  
- Using shell commands in steps  
- Matrix strategies for multiple environments  
- Running parallel jobs  
- Multi-job workflows  

---

## 🛒 Using Marketplace Actions

- Using pre-built actions from GitHub Marketplace  
- Using language-specific actions  
- Implementing caching for faster builds  

Examples include:

- Python setup actions  
- Java setup actions  
- Node.js setup actions  

---

## 🖥️ Runners in GitHub Actions

Understanding runner environments:

- GitHub-hosted runners  
- Self-hosted runners  

Runner security and management concepts.

---

## 🐳 Docker & GitHub Actions

- Building Docker images inside CI pipelines  
- Running Docker commands in workflows  

Docker operations include:

- Building Docker images  
- Pushing images to Docker Hub  
- Pushing images to GitHub Container Registry (GHCR)  

---

## ☁️ Deployments Using GitHub Actions

Deploying applications to:

- Servers  
- Cloud platforms  

Understanding automated deployment workflows.

---

# 📂 Content Organization

This branch is organized in a **day-wise / interval-wise format** based on lab sessions.

Each folder may include:

- 📄 Task descriptions and notes  
- 📸 Screenshots of workflow execution  
- 📝 Observations and outputs  
- 📁 Documentation files  
- 📌 Workflow YAML files  
- 🐳 Docker-related files  

---

# 📁 Folder Naming Pattern

Folders may follow patterns like:

- Day-1  
- Day-2  
- Day-3  

or

- Week-1  
- Week-2  


---

# 🧪 Practical Work Included

## ⚙️ Creating GitHub Workflows

- Creating `.github/workflows` directory  
- Writing basic workflow YAML files  
- Running workflows using push triggers  
- Understanding workflow logs  

---

## 🔔 Working with Workflow Triggers

Example trigger:

```yaml
on:
  push:
  pull_request:
  schedule:
```
---

## ☁️ Deployment Workflows

Deploying applications automatically using workflows.

Deployment targets include:

- Remote servers  
- Cloud platforms  

---

## 🔄 Update Pattern

Content is added after completing practical sessions.

Updates may be:

- Day-wise  
- Week-wise  
- Task-based  

Each commit represents:

- ✅ Completed workflow  
- ✅ Successful execution  
- ✅ Verified automation  

Screenshots are included as proof of successful workflow execution.

---

## 📌 Learning Outcomes

After completing Unit 5, the following skills are developed:

- ✔ Understanding Continuous Integration (CI)  
- ✔ Creating GitHub Actions workflows  
- ✔ Automating project builds  
- ✔ Using workflow triggers  
- ✔ Running multi-job workflows  
- ✔ Using marketplace actions  
- ✔ Implementing caching  
- ✔ Working with runners  
- ✔ Integrating Docker into CI pipelines  
- ✔ Deploying applications automatically  

These skills are important for:

- ⚙️ DevOps Automation  
- ☁️ Cloud Deployment  
- 🚀 CI/CD Pipelines  
- 🧑‍💻 Modern Software Development  

---

## 📎 Tools & Technologies Used

- Git  
- GitHub  
- GitHub Actions  
- Docker  
- Docker Hub  
- GitHub Container Registry (GHCR)  
- YAML Workflow Files  
- VS Code / IntelliJ IDEA  
- Command Line Interface (CLI)  

---

## 📌 Branch Status

🚧 **Active Development**

This branch will be continuously updated with:

- Workflow files  
- Docker configurations  
- Screenshots  
- Commands  
- Documentation  

as **Unit 5 progresses**.

---
