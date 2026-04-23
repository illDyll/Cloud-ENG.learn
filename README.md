[README.md](https://github.com/user-attachments/files/26998155/README.md)
# Cloud Engineering Learning Path

A structured self-study roadmap for IT professionals transitioning into cloud engineering, with a focus on Terraform, containerization, and AWS. Built for people who already have hands-on experience with Linux, Windows, and corporate IT environments.

---

## End Goal

Land a role as a **Cloud Engineer**, **DevOps Engineer**, or **Platform Engineer** with demonstrable skills in:

- Infrastructure as Code with Terraform
- Container orchestration with Docker and Kubernetes
- AWS architecture and core services
- CI/CD pipeline automation
- Python and Bash scripting for cloud administration

---

## Prerequisites

This path assumes you already have:

- Comfortable Linux CLI usage
- Experience with Windows and Linux in corporate environments
- General systems administration knowledge
- Familiarity with networking fundamentals (DNS, TCP/IP, VLANs)

---

## The Roadmap

### Phase 1 — Scripting Foundations `Weeks 1–6`

Before touching cloud infrastructure, build the scripting skills that underpin everything else.

**Bash**
- Variables, conditionals, loops, functions
- Text processing — `grep`, `awk`, `sed`, `cut`, `sort`, `uniq`
- Pipeline chaining and log parsing
- Process management — `ps`, `kill`, `pgrep`, `nohup`
- System health scripts, log rotation, cron automation

**Python**
- Core syntax, data types, file I/O
- JSON and YAML handling (critical for cloud configs)
- `boto3` — AWS SDK: EC2, S3, CloudWatch automation
- `argparse` — building proper CLI tools
- HTTP requests and API calls

**Phase 1 projects to build:**
- [ ] AWS resource inventory script (boto3, JSON output, multi-region)
- [ ] S3 bucket audit script (size, age, public access flags)
- [ ] Server health reporter (disk, memory, CPU, services, cron-ready)
- [ ] Log analyzer (error counts, top IPs, per-hour breakdown, JSON output)

---

### Phase 2 — AWS Core + Cloud Practitioner Cert `Weeks 4–8`

> Overlap with Phase 1 — study AWS while continuing to build scripts.

- AWS Free Tier setup — touch every service you study
- AWS CLI fluency — do everything in CLI before the console
- Core services: EC2, S3, VPC, IAM, RDS, Lambda, CloudWatch
- **Cert:** AWS Cloud Practitioner (CLF-C02)

**Resources:**
- [Adrian Cantrill AWS courses](https://learn.cantrill.io)
- [Tutorials Dojo practice exams](https://tutorialsdojo.com)

---

### Phase 3 — Terraform `Weeks 7–14`

> Start before finishing SAA — it reinforces cloud concepts deeply.

**Learning order:**
1. HCL syntax, `init` / `plan` / `apply` / `destroy`, state files
2. Variables, outputs, locals, data sources
3. Remote state — S3 backend + DynamoDB locking
4. Modules — write your own VPC module
5. `for_each`, `count`, `depends_on`, `lifecycle` blocks
6. Workspaces for environment separation
7. Terragrunt (DRY config management)

**Rule:** Every piece of infrastructure you build from this point forward gets written in Terraform first. No console clicking.

**Terraform projects to build:**
- [ ] VPC from scratch — public/private subnets, IGW, NAT gateway
- [ ] EC2 behind an ALB with target groups and security groups
- [ ] RDS instance in a private subnet
- [ ] S3 + CloudFront static site
- [ ] IAM roles, policies, and instance profiles
- [ ] Full remote state backend with S3 + DynamoDB

---

### Phase 4 — AWS Solutions Architect Associate `Weeks 10–18`

The cert that gets resumes noticed. Study every service hands-on and rebuild each architecture in Terraform.

**Key domains:**
- VPC networking — subnets, routing, NACLs vs security groups, Transit Gateway
- IAM — roles, trust relationships, cross-account access
- High availability — multi-AZ, auto scaling, load balancers
- Storage — S3 storage classes, lifecycle, encryption, replication
- Serverless — Lambda, API Gateway, DynamoDB

**Cert:** AWS Solutions Architect Associate (SAA-C03)

---

### Phase 5 — Containerization `Weeks 16–26`

**Docker (Weeks 1–2)**
- Dockerfile syntax, image layers, multi-stage builds
- `docker build`, `run`, `exec`, `logs`, `ps`, volumes, networking
- Docker Compose for multi-container applications

**Kubernetes fundamentals (Weeks 3–4)**
- Local cluster with K3s on Proxmox or bare metal
- Core objects: Pods, Deployments, Services, ConfigMaps, Secrets
- `kubectl` fluency — get, describe, logs, exec, apply, rollout

**Kubernetes deeper (Weeks 5–8)**
- Ingress controllers, Persistent Volumes, resource limits
- Horizontal Pod Autoscaler
- RBAC — roles and service accounts
- Helm — packaging and deploying apps

**Kubernetes on AWS (Weeks 9–10)**
- EKS cluster provisioned with Terraform
- AWS Load Balancer Controller
- IAM Roles for Service Accounts (IRSA)

**Cert target:** CKA (Certified Kubernetes Administrator)

---

### Phase 6 — CI/CD and Full Pipeline `Weeks 24–32`

Bring everything together into a single end-to-end project:

```
Code push → GitHub Actions → Tests → Docker build
→ Push to ECR → Deploy to EKS → CloudWatch monitoring
```

All infrastructure provisioned by Terraform. All deployments via Helm or kubectl.

**Tools:**
- GitHub Actions for pipeline automation
- Amazon ECR for container registry
- Amazon EKS for Kubernetes hosting
- Prometheus + Grafana or CloudWatch for monitoring

---

### Phase 7 — Portfolio and Job Hunting `Weeks 28–36`

**Repository structure:**
```
/terraform-modules        # reusable modules you've written
/aws-projects             # each project in its own folder with README
/k8s-manifests            # Kubernetes configs and Helm charts
/scripts                  # bash and python utility scripts
/homelab                  # lab setup documentation and diagrams
```

Each project should include:
- Architecture diagram
- What problem it solves
- How to deploy it (Terraform commands, prerequisites)
- Any design decisions or lessons learned

**Target job titles:**
- Junior Cloud Engineer
- Cloud Infrastructure Engineer
- DevOps Engineer (Associate)
- Cloud Systems Engineer
- Platform Engineer

---

## Home Lab Setup

**Physical**
- Spare PC or old server running [Proxmox](https://www.proxmox.com) (free hypervisor)
- Managed switch for VLAN practice
- Raspberry Pi cluster for cheap Kubernetes experimentation

**Virtual / Cloud**
- AWS Free Tier for core labs
- [LocalStack](https://localstack.cloud) — run AWS services locally without cost
- K3s on Proxmox VMs for local Kubernetes

---

## Toolchain

| Tool | Purpose | Priority |
|---|---|---|
| Terraform | Infrastructure as Code | Critical |
| Docker | Containerization | Critical |
| Kubernetes / K3s | Container orchestration | Critical |
| AWS CLI | Cloud administration | Critical |
| Python + boto3 | Cloud automation scripting | Critical |
| Bash | System scripting and automation | Critical |
| Git / GitHub | Version control, portfolio | Critical |
| Helm | Kubernetes package management | High |
| Ansible | Configuration management | Medium |
| Terragrunt | Terraform DRY wrapper | Medium |
| Prometheus + Grafana | Monitoring and observability | Medium |

---

## Certification Timeline

| Cert | Target | Purpose |
|---|---|---|
| AWS Cloud Practitioner | Month 2 | Foundation vocabulary |
| AWS Solutions Architect Associate | Month 5 | The resume opener |
| CKA (Kubernetes) | Month 8–9 | Containerization credibility |
| AWS DevOps Professional or AWS Security Specialty | Month 12+ | Specialization |

---

## Timeline Summary

| Phase | Focus | Weeks |
|---|---|---|
| 1 | Bash + Python scripting | 1–6 |
| 2 | AWS basics + Cloud Practitioner | 4–8 |
| 3 | Terraform core to advanced | 7–14 |
| 4 | AWS SAA cert | 10–18 |
| 5 | Docker + Kubernetes + EKS | 16–26 |
| 6 | CI/CD end-to-end pipeline | 24–32 |
| 7 | Portfolio + job applications | 28–36 |

---

## The One Rule

**Build everything.** Read nothing passively. Every concept gets turned into a working script, config, or deployed resource within 24 hours of learning it. That gap between people who get hired and people who collected certs is entirely made up of this habit.

---

*Background: IT professional with Linux, Windows, and corporate systems experience transitioning into cloud engineering.*
