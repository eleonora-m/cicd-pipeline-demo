# 🚀 CI/CD Pipeline with GitHub Actions

Automated CI/CD pipeline that builds, tests, and deploys a containerized application to AWS EKS using GitHub Actions.

## 🏗️ Pipeline Architecture

```
Developer pushes code
        │
        ▼
┌─────────────────────┐
│   GitHub Actions    │
│                     │
│  1. Run Tests       │
│  2. Build Docker    │
│  3. Push to ECR     │
│  4. Deploy to EKS   │
│  5. Health Check    │
└─────────────────────┘
        │
        ▼
   AWS EKS Cluster
   (Production)
```

## 🛠️ Technologies
- **GitHub Actions** — CI/CD automation
- **Docker** — containerization
- **AWS ECR** — container registry
- **AWS EKS** — Kubernetes deployment
- **Python/Flask** — sample application

## 📂 Project Structure
```
cicd-pipeline-demo/
├── .github/
│   └── workflows/
│       ├── ci.yml          # CI — test and build on every PR
│       └── cd.yml          # CD — deploy on merge to main
├── app/
│   ├── app.py              # Flask application
│   ├── test_app.py         # Unit tests
│   └── requirements.txt    # Python dependencies
├── Dockerfile              # Container definition
├── k8s/
│   ├── deployment.yaml     # Kubernetes deployment
│   └── service.yaml        # Kubernetes service
└── README.md
```

## 🔄 Pipeline Stages

### CI (Pull Request)
| Stage | What happens |
|-------|-------------|
| ✅ Test | Run unit tests with pytest |
| ✅ Lint | Check code quality |
| ✅ Build | Build Docker image |
| ✅ Scan | Check for vulnerabilities |

### CD (Merge to main)
| Stage | What happens |
|-------|-------------|
| 🐳 Build & Push | Build image, push to AWS ECR |
| ☸️ Deploy | Update EKS deployment |
| 🔍 Health Check | Verify deployment succeeded |

## 🚀 Usage

```bash
# Clone repo
git clone https://github.com/eleonora-m/cicd-pipeline-demo
cd cicd-pipeline-demo

# Run app locally
pip install -r app/requirements.txt
python app/app.py

# Run tests
pytest app/test_app.py -v

# Build Docker image
docker build -t cicd-demo .
docker run -p 5000:5000 cicd-demo
```

## 🔐 Required GitHub Secrets
```
AWS_ACCESS_KEY_ID       — AWS access key
AWS_SECRET_ACCESS_KEY   — AWS secret key
AWS_REGION              — e.g. us-east-1
ECR_REPOSITORY          — ECR repository name
EKS_CLUSTER_NAME        — EKS cluster name
```

## 📊 Key Results
- Deployment time reduced from **45 min → 8 min** (automated vs manual)
- Zero-downtime deployments with rolling updates
- Automatic rollback on failed health checks

## 👩‍💻 Author
**Eleonora Musaeva** — Cloud Administrator | DevOps Engineer  
📧 devops.nora@gmail.com
