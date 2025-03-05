Collecting workspace informationFiltering to most relevant information# DevSecOps Automation Pipelines

This repository demonstrates a comprehensive DevSecOps automation setup using Jenkins pipelines. The pipelines cover various stages of software development, including code validation, building Docker images, continuous deployment, and infrastructure provisioning with Terraform. Below is an overview of the key pipelines and their functionalities.

## Pipelines Overview

### 1. Full Pipeline

**File:** Full_Pipeline.groovy

This pipeline orchestrates the entire CI/CD process, including security scans and artifact publishing. Key stages include:

- **Git Clone:** Clones the repository.
- **Build Docker Image:** Builds the Docker image.
- **Push Docker Image:** Pushes the Docker image to a repository.
- **Security Tests:** Runs various security scans (Docker Scout, Xray, SonarQube, GitGuardian, GitLeaks).
- **Artifactory Publish Build Info:** Publishes build information to Artifactory.
- **Artifactory Configuration:** Configures Artifactory for artifact management.

### 2. Terraform Build Pipeline

**File:** Pipeline_Build_Terraform.groovy

This pipeline handles the provisioning of infrastructure using Terraform. Key stages include:

- **Git Clone:** Clones the repository.
- **Terraform Init:** Initializes the Terraform configuration.
- **Terraform Plan:** Creates an execution plan.
- **Terraform Apply:** Applies the Terraform plan.
- **Terraform Destroy:** Destroys the Terraform-managed infrastructure.
- **Backup Terraform State File:** Backs up the Terraform state file.

### 3. Continuous Deployment Pipeline

**File:** Pipeline_Build_Continuous_Deployment.groovy

This pipeline focuses on continuous deployment using Kubernetes and ArgoCD. Key stages include:

- **Git Clone:** Clones the repository.
- **Kubernetes:** Deploys the application to Kubernetes using Kustomize.
- **ArgoCD:** Configures and deploys the application using ArgoCD.

### 4. Git Code Validation Pipeline

**File:** Pipeline_Git_Code_Validation.groovy

This pipeline performs code validation and linting for various file types. Key stages include:

- **Git Clone:** Clones the repository.
- **Linting Python:** Lints Python code using `autopep8`.
- **Linting Go:** Lints Go code using `golangci-lint`.
- **Linting YAML:** Lints YAML files using `yamllint`.
- **Linting XML:** Lints XML files using pre-commit hooks.
- **Linting JSON:** Lints JSON files using pre-commit hooks.
- **Linting Markdown:** Lints Markdown files using `mdl`.
- **Code Spelling:** Checks code spelling using pre-commit hooks.
- **Search AWS Credentials:** Searches for AWS credentials using pre-commit hooks.
- **Search Passwords:** Searches for passwords using `gitleaks`.

### 5. Docker Build Pipeline

**File:** Pipeline_Build_Docker.groovy

This pipeline handles the building, testing, and pushing of Docker images. Key stages include:

- **Git Clone:** Clones the repository.
- **Build Docker Image:** Builds the Docker image.
- **UniTest Docker Image:** Runs unit tests on the Docker image.
- **Push Docker Image:** Pushes the Docker image to a repository.
- **Docker Scout CVE:** Scans the Docker image for vulnerabilities using Docker Scout.
- **Xray Scan:** Scans the Docker image using Xray.
- **SonarQube Analysis:** Analyzes the Docker image using SonarQube.
- **GitGuardian Scan:** Scans for secrets using GitGuardian.
- **GitLeaks Scan:** Scans for secrets using GitLeaks.

### Using Catch Error 'catchErrorHandling' in Pipelines

- **catchErrorHandling** catch errors and fix issues as the pipeline is still running

```json
catch (Exception ERROR) {
    echo "\033[41m\033[97m\033[1mStep ${env.STAGE_NAME} Failed: ${ERROR}\033[0m"
    currentBuild.result = 'FAILURE'
    def catchErrorHandling = "${ERROR}"
    if (catchErrorHandling.contains("exit code 1")) {
        sh ("echo \033[41m\033[97m\033[1mGot Error: ${catchErrorHandling}\033[0m")
        sh ("echo \033[41m\033[97m\033[1mSending Email to Admin\033[0m")
    }
    if (catchErrorHandling.contains("exit code 127")) {
        sh ("echo \033[41m\033[97m\033[1mGot Error: ${catchErrorHandling}\033[0m")
        sh ("echo \033[41m\033[97m\033[1mTrying to install autopep8 with pip \033[0m")
        sh ("pip install autopep8")
    }
}
```

### Using Docker Container to Execute Code

- Running CI/CD jobs inside containers minimizes exposure to host system vulnerabilities
- Dockerized CI/CD can be easily scaled across different machines or cloud environments.
- Parallel execution of tests and builds can be easily managed with containerized workflows

```bash
docker run --rm -i -v /home/root/k6-load-testing:/tmp/ --memory=128m --cpus="0.5" grafana/k6:latest-with-browser run --vus 10 --duration 4s /tmp/script.js
```

```bash
docker run --rm -v $(pwd):/tmp/ --memory=128m --cpus="0.5" zaproxy/zap-stable zap.sh -daemon /tmp/zap-baseline.py -t https://www.example.com
```

## Conclusion

This repository showcases a robust DevSecOps automation setup using Jenkins pipelines. It covers various aspects of CI/CD, security scanning, and infrastructure provisioning, making it an excellent example of modern DevSecOps practices.
