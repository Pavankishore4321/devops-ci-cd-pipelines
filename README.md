# devops-ci-cd-pipelines

CI/CD pipeline templates built from real production deployments at **Incresol Software Services**.
These pipelines were used to deploy Angular frontends, Java Spring Boot backends, and
Docker-based applications across AWS and Azure environments.

---

## What's Inside

| File | Tool | Used For |
|---|---|---|
| `jenkins/Jenkinsfile-angular-ansible` | Jenkins + Angular CLI + Ansible | Angular frontend build and deploy to Nginx via Ansible |
| `jenkins/Jenkinsfile-springboot-tomcat` | Jenkins + Maven + Tomcat | Java Spring Boot build and Tomcat 9 deployment |
| `jenkins/Jenkinsfile-docker-deploy` | Jenkins + Docker + Trivy | Docker image build, Trivy security scan, container deploy |
| `azure-devops/azure-pipeline.yml` | Azure DevOps | Angular app build and deploy to Azure App Service |
| `github-actions/deploy-on-push.yml` | GitHub Actions | Angular CI + Docker build/push on merge to main |

---

## Pipeline Flow

### Angular + Ansible Pipeline
```
Git Checkout → npm install → SonarQube Scan → Quality Gate → ng build → Ansible Deploy (Nginx) → Health Check
```

### Spring Boot + Tomcat Pipeline
```
Git Checkout → Maven Build → SonarQube Scan → Archive JAR → Tomcat Deploy → Smoke Test → Auto Rollback on Failure
```

### Docker Pipeline
```
Git Checkout → Docker Build → Aqua Trivy Scan → Push to Registry → Deploy Container → Health Check → Prune Old Images
```

---

## Tools & Versions

- **Jenkins** — 2.x (LTS)
- **Angular CLI** — 15.x / 16.x
- **Node.js** — 18.x (required to run Angular CLI)
- **Maven** — 3.8.x
- **Java** — 8 (Spring Boot)
- **Docker** — 24.x
- **Ansible** — 2.14+
- **Nginx** — 1.24+
- **SonarQube** — Community Edition
- **Aqua Trivy** — v0.48+
- **Azure DevOps** — Pipelines v2

---

## Jenkins Setup Required

Before using Jenkins files, configure these in Jenkins → Manage Jenkins → Credentials:

| Credential ID | Type | Purpose |
|---|---|---|
| `GitHub-credentials` | Username/Password | GitHub repo access |
| `Docker hub-credentials` | Username/Password | Docker Hub push |
| `SonarQube-Server` | Secret Text | SonarQube connection |

---

## Real Projects These Pipelines Supported

- **AspTax** — Tax management platform (Angular + Spring Boot + AWS + Jenkins + SonarQube + Nginx)
- **P-Collab** — Collaboration tool (Angular + Azure DevOps + Azure App Service + MongoDB)
- **Java Spring Boot** — Multi-client deployments (Jenkins + Tomcat 9 + PostgreSQL/MySQL)
- **Node App** — High availability setup (Docker + Nginx + MongoDB Replica Set)

---

## Author

**Pavan Kishore Nakka**
DevOps & Cloud Engineer | 3+ Years
AWS Certified Solutions Architect – Associate | AWS Cloud Practitioner

[LinkedIn](https://www.linkedin.com/in/nakka-pavan-kishore-103226221/)
