# 🚗 Vehicle Data Prediction – End-to-End MLOps Pipeline

## 📖 Overview

This project is a complete, production-ready Machine Learning Operations (MLOps) pipeline designed to ingest, process, train, and deploy models utilizing vehicle data. Built with scalability and automation in mind, it features custom logging, a modular object-oriented architecture, seamless MongoDB integration, and a fully automated CI/CD deployment cycle using GitHub Actions, Docker, and AWS.

## ✨ Key Features & Capabilities

* **Modular Pipeline Architecture:** Distinct, decoupled components for Data Ingestion, Validation, Transformation, Model Training, Evaluation, and Pushing.
* **Robust Data Management:** Live data ingestion directly from a remote MongoDB Atlas cluster.
* **Cloud-Native Model Registry:** Automated pushing and pulling of production-ready models to and from AWS S3 buckets.
* **Enterprise-Grade Tracking:** Custom python logger and exception handling components integrated across the entire lifecycle.
* **Automated CI/CD:** Continuous integration and continuous deployment pipelines utilizing GitHub Actions with a self-hosted runner.
* **Containerized Deployment:** Application containerization using Docker, stored securely in AWS ECR, and served via an AWS EC2 Ubuntu instance.
* **Web Interface:** An interactive web application built to serve model predictions securely over port 5080.

## 🛠️ Technology Stack

| Category | Tools & Services |
| --- | --- |
| **Programming Language** | Python 3.10 |
| **Database** | MongoDB Atlas |
| **Cloud Infrastructure** | AWS (S3, ECR, EC2, IAM) |
| **Containerization** | Docker |
| **CI/CD Automation** | GitHub Actions |
| **Packaging** | `setup.py`, `pyproject.toml` |

## 🔐 Environment Variables Configuration

To run this project locally or via CI/CD, the following environment variables and secrets must be configured:

| Variable Name | Purpose |
| --- | --- |
| `MONGODB_URL` | Connection string for MongoDB Atlas |
| `AWS_ACCESS_KEY_ID` | IAM User access key for S3/ECR |
| `AWS_SECRET_ACCESS_KEY` | IAM User secret key for S3/ECR |
| `AWS_DEFAULT_REGION` | AWS Region (e.g., `us-east-1`) |
| `ECR_REPO` | URI for the AWS Elastic Container Registry |

## 💻 Local Setup & Installation

**1. Clone the repository and navigate to the project directory:**

```bash
git clone <your-repo-link>
cd <project-directory>

```

**2. Create and activate a Conda virtual environment:**

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle

```

**3. Install required dependencies and local packages:**

```bash
pip install -r requirements.txt
pip list

```

**4. Export your MongoDB Connection URL:**

```bash
# For Bash/Linux/Mac
export MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/..."

# For PowerShell/Windows
$env:MONGODB_URL="mongodb+srv://<username>:<password>@cluster.mongodb.net/..."

```

**5. Execute the pipeline:**

```bash
python demo.py
# Or launch the web application
python app.py

```

## ☁️ Cloud Deployment Workflow (AWS & Docker)

This project is configured for automated deployment. Pushing code to the main branch triggers the following GitHub Actions workflow:

1. Code is checked out and linted.
2. A new Docker image is built using the provided `Dockerfile`.
3. The image is authenticated and pushed to the AWS Elastic Container Registry (ECR).
4. The self-hosted GitHub runner on the AWS EC2 instance pulls the latest image.
5. The application container is launched and exposed on port `5080`.

## 👨‍💻 Author

**Shivang Shahi**