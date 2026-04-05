<div align="center">

# tekton-catalog-20240828215145954

[![GitHub stars](https://img.shields.io/github/stars/StarlightRetail/tekton-catalog-20240828215145954?style=for-the-badge&logo=github&colorB=blue)](https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/StarlightRetail/tekton-catalog-20240828215145954?style=for-the-badge&logo=github&colorB=cyan)](https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954/network/members)
[![GitHub issues](https://img.shields.io/github/issues/StarlightRetail/tekton-catalog-20240828215145954?style=for-the-badge&logo=github&colorB=yellow)](https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954/issues)
[![License](https://img.shields.io/github/license/StarlightRetail/tekton-catalog-20240828215145954?style=for-the-badge&colorB=green)](https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954/blob/main/LICENSE)
[![Last Commit](https://img.shields.io/github/last-commit/StarlightRetail/tekton-catalog-20240828215145954?style=for-the-badge&logo=git&colorB=purple)](https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954/commits)
[![Shell](https://img.shields.io/badge/Shell-89E051?style=for-the-badge&logo=shell&logoColor=white)](#)

<p align="center">
<a href="https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954"><img src="https://img.shields.io/badge/View_on_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="View on GitHub" /></a>
<a href="https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954/issues/new"><img src="https://img.shields.io/badge/Report_Bug-FF0000?style=for-the-badge&logo=github&logoColor=white" alt="Report Bug" /></a>
<a href="https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954/issues/new?labels=enhancement"><img src="https://img.shields.io/badge/Request_Feature-0080FF?style=for-the-badge&logo=github&logoColor=white" alt="Request Feature" /></a>
</p>

<br/>

*Part of the [StarlightRetail](https://github.com/StarlightRetail) organization*

---

</div>

# STARLIGHTRETAIL/tekton-catalog-20240828215145954  
*A curated collection of Tekton tasks for Continuous Delivery pipelines*

## Overview  

The `tekton-catalog-20240828215145954` repository, developed by **StarlightRetail**, serves as a centralized catalog for reusable [Tekton Tasks](https://tekton.dev/docs/pipelines/tasks/#overview). These tasks are specifically designed to facilitate the implementation of robust, scalable Continuous Delivery pipelines within IBM Cloud and other environments.  

This catalog offers a comprehensive toolkit to handle critical CI/CD operations, including application deployment, Docker image management, vulnerability analysis, and more. With predefined tasks tailored for Cloud Foundry applications and IBM Cloud Container Registry, development teams can streamline their DevOps processes without needing to define everything from scratch.  

Whether you're building cloud-native applications or deploying containerized workloads, this repository empowers developers to accelerate their software delivery lifecycle through reliable and reusable Tekton assets.  

## Key Features  

- **Cloud Foundry Application Deployment**: Automate application deployment using `ibmcloud cf` commands.  
- **Containerization Support**: Build and push Docker images to the IBM Cloud Container Registry using [BuildKit](https://github.com/moby/buildkit).  
- **Docker-in-Docker (DinD) Execution**: Execute Docker commands in isolated DinD environments, including cluster-based setups.  
- **Vulnerability Analysis**: Validate the security of container images using IBM Cloud Vulnerability Advisor scans.  
- **Prebuilt Tekton Task Catalog**: Multiple Tekton pipeline resources for common CI/CD scenarios.  

## Tech Stack  

| Technology               | Description                                                     |  
|--------------------------|-----------------------------------------------------------------|  
| **Shell**                | Primary language for all scripts and task definitions          |  
| **Tekton Pipelines**     | Kubernetes-based CI/CD pipelines framework                     |  
| **IBM Cloud CLI Tools**  | Command-line tools for IBM Cloud resource management           |  
| **Docker/DinD**          | Docker and Docker-in-Docker instances for container tasks      |  

## Getting Started  

Follow these steps to set up and get started with the `tekton-catalog-20240828215145954` repository:  

### Prerequisites  

1. **Tekton Pipelines**: Ensure Tekton is installed on your Kubernetes cluster. Follow [Tekton installation instructions](https://tekton.dev/docs/getting-started/).  
2. **IBM Cloud CLI**: Install the IBM Cloud CLI along with any required plugins (e.g., `cf`, `cr`).  
   ```bash  
   curl -fsSL https://clis.cloud.ibm.com/install/linux | sh  
   ibmcloud plugin install cf  
   ibmcloud plugin install container-registry  
   ```  
3. **Kubernetes Cluster**: Access to a Kubernetes environment with sufficient permissions.  

### Installation  

1. Clone the repository:  
   ```bash  
   git clone https://github.com/STARLIGHTRETAIL/tekton-catalog-20240828215145954.git  
   cd tekton-catalog-20240828215145954  
   ```  

2. Set up the Tekton tasks in your Kubernetes cluster:  
   ```bash  
   kubectl apply -f .ci/ci-pipeline.yaml  
   kubectl apply -f .ci/pr-pipeline.yaml  
   kubectl apply -f container-registry/task-containerize.yaml  
   ```  

### Basic Usage  

Run a sample Tekton pipeline for deploying a Cloud Foundry application:  

1. Apply task-specific YAML:  
   ```bash  
   kubectl apply -f cloudfoundry/task-deploy-app.yaml  
   ```  

2. Trigger deployment pipeline:  
   ```bash  
   kubectl create -f cloudfoundry/sample-cf-app/pipeline-cf-app.yaml  
   ```  

3. Monitor the pipeline execution:  
   ```bash  
   kubectl get pipelineruns --watch  
   ```  

## Project Structure  

The repository is organized as follows:  

```
├── .ci/                     # CI/CD configuration files  
├── cloudfoundry/            # Tasks and templates related to Cloud Foundry deployment  
├── container-registry/      # Tasks for IBM Cloud Container Registry and Docker integration  
├── cra/                     # Tasks for Continuous Retrospective Analysis (CRA)  
├── LICENSE                  # Apache License 2.0  
├── README.md                # Project documentation  
```  

### Key Directories  

- **`.ci/`**: Contains YAML definitions for CI and PR pipelines, listeners, and triggers.  
- **`cloudfoundry/`**: Enables deployment scenarios for Cloud Foundry applications.  
- **`container-registry/`**: Supports tasks like image building, vulnerability scanning, and Docker-in-Docker execution.  
- **`cra/`**: Includes resources for maintaining continuous analysis workflows.  

## Usage  

Below is an example of running the `icr-containerize` task to build and push an image to IBM Cloud Container Registry:  

1. Configure Docker authentication and IBM Cloud credentials in your Kubernetes cluster using secrets.  
2. Apply the task:  
   ```bash  
   kubectl apply -f container-registry/task-containerize.yaml  
   ```  
3. Use the task in a pipeline:  
   ```yaml  
   apiVersion: tekton.dev/v1beta1  
   kind: Pipeline  
   metadata:  
     name: containerize-example  
   spec:  
     tasks:  
       - name: icr-containerize  
         taskRef:  
           name: containerize  
         params:  
           - name: image  
             value: "us.icr.io/my-namespace/my-image:latest"  
   ```  

Execute the pipeline:  
```bash  
kubectl apply -f container-registry/sample/pipeline-buildkit-no-image-url.yaml  
```  

## Contributing  

We welcome contributions to improve the repository and its tasks. To contribute to the `tekton-catalog-20240828215145954` repository, please:  

1. Fork the repository within your GitHub account.  
2. Create a feature or bug fix branch.  
3. Submit a pull request with a detailed description of your changes.  

Contributions must comply with **StarlightRetail**'s coding standards and should ensure backward compatibility wherever possible.  

For larger changes or proposals, please open an issue with your ideas before submitting code.  

## License  

The `tekton-catalog-20240828215145954` repository is licensed under the [Apache License 2.0](LICENSE).  



---

<div align="center">

**[StarlightRetail](https://github.com/StarlightRetail)** — Building the future of retail technology

Made with :purple_heart: by the StarlightRetail team

</div>