# ZuriMarket

### Cloud-Native Marketplace with DevOps Automation

ZuriMarket is an online marketplace project designed to demonstrate modern DevOps practices, including containerization, cloud infrastructure provisioning, CI/CD automation, and monitoring.

## Technology Stack

| Technology | Purpose |
|---|---|
| React + Vite | Frontend application |
| Docker | Containerization |
| Terraform | Infrastructure provisioning |
| AWS EC2 | Cloud hosting |
| GitHub Actions | CI/CD automation |
| Prometheus | Metrics collection |
| Grafana | Monitoring dashboards |

## Project Structure

```text
capstone-project-04/
├── .github/
│   └── workflows/       # CI/CD workflows
├── frontend/            # React frontend
│   ├── Dockerfile
│   └── nginx.conf
├── scripts/
│   └── deploy.sh        # Deployment script
├── terraform/           # AWS infrastructure
├── monitoring/          # Monitoring configuration
├── docker-compose.yml   # Local services (if configured)
├── .gitignore
└── README.md
```

## Prerequisites

Install the following tools:

- Git
- Docker and Docker Compose
- Terraform
- AWS CLI
- Node.js and npm

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/dammy123-ai/capstone-project-04.git
cd capstone-project-04
```

### 2. Build the frontend Docker image

```bash
cd frontend
docker build -t zurimarket-frontend .
```

### 3. Run the application

```bash
docker run -d \
  --name zurimarket \
  -p 80:80 \
  zurimarket-frontend
```

Open the application:

```text
http://localhost
```

### 4. Provision AWS infrastructure

Navigate to the development Terraform environment:

```bash
cd terraform/environments/dev
```

Initialize Terraform:

```bash
terraform init
```

Validate the configuration:

```bash
terraform validate
```

Preview the infrastructure changes:

```bash
terraform plan -var-file=dev.tfvars
```

Provision the infrastructure:

```bash
terraform apply -var-file=dev.tfvars
```

Review the Terraform outputs:

```bash
terraform output
```

### 5. Deploy to AWS

The deployment script builds and runs the frontend Docker container on the EC2 instance.

```bash
bash scripts/deploy.sh
```

The EC2 instance must have Docker installed and the required deployment access configured.

## Monitoring

The project uses:

- **Prometheus:** Collects system and application metrics.
- **Grafana:** Displays monitoring dashboards.

Monitoring will be configured separately from the initial frontend deployment.

## Useful Docker Commands

Check running containers:

```bash
docker ps
```

View application logs:

```bash
docker logs zurimarket
```

Stop the application:

```bash
docker stop zurimarket
```

Remove the container:

```bash
docker rm zurimarket
```

## Terraform Cleanup

To preview resources scheduled for deletion:

```bash
terraform plan -destroy -var-file=dev.tfvars
```

To destroy Terraform-managed infrastructure:

```bash
terraform destroy -var-file=dev.tfvars
```

**Warning:** Terraform destroy can permanently remove cloud resources and associated data. Review the plan before proceeding.

## Repository

GitHub: https://github.com/dammy123-ai/capstone-project-04

---

**ZuriMarket — Demonstrating cloud infrastructure, Docker containerization, automation, and monitoring using modern DevOps tools.**
