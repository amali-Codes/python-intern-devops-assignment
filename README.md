DevOps Infra + CI/CD + Monitoring

## 📌 Overview
This repository contains the technical assignment for **8byte – Python Intern (AI Solutions)**. It demonstrates end-to-end ownership of:
- Infrastructure provisioning with **Terraform (AWS)**
- Deployment automation with **GitHub Actions CI/CD**
- Monitoring & Logging with **Prometheus + Grafana**
- Documentation of architecture, security, and cost optimizations

---

**Components:**
- **AWS VPC** with public and private subnets
- **EC2 Instance** running Flask App (Dockerized)
- **Application Load Balancer (ALB)** in public subnet
- **RDS PostgreSQL Database** in private subnet
- **Monitoring** via Prometheus & Grafana
- **CI/CD** using GitHub Actions

---

## 🚀 Setup Instructions
### 1. Infrastructure (Terraform)
```bash
cd terraform
terraform init
terraform apply
```
This provisions VPC, EC2, RDS, and ALB.

### 2. Run Application
```bash
cd app
docker build -t flask-app .
docker run -p 5000:5000 flask-app
```
Access app at: `http://<EC2_PUBLIC_IP>:5000`

### 3. CI/CD Pipeline
- On Pull Request → Runs tests
- On Merge to `main` → Builds Docker image, deploys to staging
- Manual Approval → Deploys to production

Config: [`.github/workflows/ci-cd.yml`](.github/workflows/ci-cd.yml)

### 4. Monitoring
- **Prometheus** scrapes app + infra metrics
- **Grafana** dashboards for:
  - Infra metrics (CPU, Memory, Disk)
  - Application metrics (Request rate, Error rate, Latency)

Run Prometheus:
```bash
cd monitoring
prometheus --config.file=prometheus.yml
```

---

## 🔐 Security Considerations
- IAM roles with least privilege
- Secrets stored in **AWS Secrets Manager** (recommended)
- Security groups restrict DB access to app subnet only

---

## 💰 Cost Optimization
- **t2.micro** (Free Tier) for demo
- Enable **Auto Scaling Groups** in production
- RDS storage auto-scaling
- Use **spot instances** for non-critical workloads

---

## 📄 Additional Documentation
- [APPROACH.md](APPROACH.md) → Detailed decisions & approach
- [CHALLENGES.md](CHALLENGES.md) → Challenges faced & resolutions

---

## ✅ Deliverables
- Terraform code for AWS infra
- Flask app + Dockerfile
- GitHub Actions CI/CD workflow
- Prometheus + Grafana monitoring setup
- Documentation (README, APPROACH, CHALLENGES)

---

👨‍💻 Author: Amali Akshaya
