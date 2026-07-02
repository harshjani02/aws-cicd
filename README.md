# 🚀 AWS CI/CD Pipeline for a Python Flask Application

This project demonstrates how to build a **CI/CD pipeline on AWS** for a simple Python Flask application. The pipeline automatically installs dependencies, builds a Docker image, and pushes the image to a Docker registry using **AWS CodeBuild**.

The project is intended for learning and practicing AWS DevOps services such as **CodeBuild**, **Systems Manager Parameter Store**, **Docker**, and **GitHub** integration.

---

## 📌 Project Overview

The application is a simple Flask web server that returns:

```
Hello, world!
```

Although the application itself is minimal, the primary goal of this repository is to understand how an automated CI/CD pipeline works in AWS.

---

# 🏗️ Architecture

```text
                +----------------+
                |     GitHub     |
                +--------+-------+
                         |
                         | Source Code
                         |
                +--------v-------+
                | AWS CodeBuild  |
                +--------+-------+
                         |
      Install Dependencies & Build Docker Image
                         |
                +--------v-------+
                |    Docker      |
                +--------+-------+
                         |
              Push Docker Image
                         |
                +--------v-------+
                | Docker Hub/ECR |
                +----------------+
```

---

# 🔄 CI/CD Workflow

1. Developer pushes code to GitHub.
2. AWS CodeBuild fetches the latest source code.
3. Dependencies are installed.
4. Docker image is built.
5. CodeBuild logs in to Docker Hub using credentials stored securely in AWS Systems Manager Parameter Store.
6. Docker image is pushed to the Docker registry.
7. Build artifacts are generated.

---

# 📁 Project Structure

```text
aws-cicd/
│
├── app.py                # Flask application
├── Dockerfile            # Docker image definition
├── buildspec.yaml        # AWS CodeBuild pipeline configuration
├── requirements.txt      # Python dependencies
└── README.md
```

---

# ⚙️ Technologies Used

* Python 3
* Flask
* Docker
* AWS CodeBuild
* AWS Systems Manager Parameter Store
* GitHub

---

# ☁️ AWS Services Used

| Service                             | Purpose                                             |
| ----------------------------------- | --------------------------------------------------- |
| AWS CodeBuild                       | Builds the application and executes the CI pipeline |
| AWS Systems Manager Parameter Store | Securely stores Docker Hub credentials              |
| IAM                                 | Grants CodeBuild the required permissions           |
| GitHub                              | Source code repository                              |

---

# 📦 Build Process

The build process is defined in `buildspec.yaml`.

### Install Phase

* Configure Python runtime
* Prepare the build environment

### Pre-Build Phase

* Install Python dependencies
* Authenticate with Docker Hub

### Build Phase

* Build Docker image
* Push image to Docker Hub

### Post-Build Phase

* Complete the build
* Upload build artifacts

---

# 🐳 Docker

The application is containerized using Docker.

Build the image locally:

```bash
docker build -t flask-app .
```

Run the container:

```bash
docker run -p 5000:5000 flask-app
```

Visit:

```
http://localhost:5000
```

Output:

```
Hello, world!
```

---

# ▶️ Run Locally

### Clone Repository

```bash
git clone https://github.com/harshjani02/aws-cicd.git
```

```bash
cd aws-cicd
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run Application

```bash
python app.py
```

---

# 🔐 Secure Credential Management

Docker Hub credentials are **not hardcoded**.

Instead, they are stored securely using **AWS Systems Manager Parameter Store** and accessed during the CodeBuild execution.

This follows AWS security best practices.

---

# 📚 Learning Objectives

This project helped me understand:

* Building CI pipelines using AWS CodeBuild
* Writing a `buildspec.yaml` file
* Creating Docker images
* Authenticating with Docker Hub
* Secure secret management using AWS Systems Manager Parameter Store
* Integrating GitHub with AWS services
* Basic Docker-based application deployment workflow

---

# 🚀 Future Improvements

* Integrate AWS CodePipeline for end-to-end automation
* Push Docker images to Amazon ECR
* Deploy automatically to Amazon ECS or EKS
* Add automated testing before image build
* Add application health checks
* Configure CloudWatch logs and monitoring
* Implement Infrastructure as Code using CloudFormation or Terraform



# 👨‍💻 Author

**Harsh Jani**

GitHub: https://github.com/harshjani02

---

# ⭐ If you found this project useful, consider giving it a star.
