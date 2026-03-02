# Learn Terraform Docker Container

This project is a hands-on learning repository for Infrastructure as Code (IaC) using Terraform to manage Docker-based environments. It demonstrates how to pull a Docker image and deploy a containerized Nginx web server.

## Project Overview

- **Purpose:** Automate the deployment of a simple Dockerized web server.
- **Core Technologies:**
  - [Terraform](https://www.terraform.io/) (v1.x recommended)
  - [Docker](https://www.docker.com/) (Local Docker Desktop or Engine)
  - [kreuzwerker/docker](https://registry.terraform.io/providers/kreuzwerker/docker/latest) provider (v3.x)
- **Architecture:**
  - The project pulls the latest `nginx` image from Docker Hub.
  - It deploys a single Docker container that maps internal port `80` to external port `8080`.

## Building and Running

Ensure you have Terraform and Docker installed and running on your machine.

### Key Commands

1.  **Initialize Project:**
    ```bash
    terraform init
    ```
    Downloads the necessary Docker provider plugins.

2.  **Plan Infrastructure:**
    ```bash
    terraform plan
    ```
    Previews the actions Terraform will take to create the image and container.

3.  **Apply Changes:**
    ```bash
    terraform apply
    ```
    Executes the plan to pull the image and start the container. (Use `-auto-approve` to skip the confirmation prompt).

4.  **Destroy Resources:**
    ```bash
    terraform destroy
    ```
    Stops the container and removes the managed infrastructure.

### Verification
Once applied, you can access the Nginx welcome page at `http://localhost:8080`.

## Development Conventions

- **File Structure:**
  - `main.tf`: Contains the provider configuration and resource definitions.
  - `variables.tf`: Defines input variables for customization (e.g., `container_name`).
- **State Management:**
  - The `terraform.tfstate` and `terraform.tfstate.backup` files track the current state of your infrastructure. Do not modify these manually.
- **Coding Style:**
  - Always run `terraform fmt` before committing to maintain consistent HCL formatting.
  - Use descriptive names for resources and variables.
- **Variable Customization:**
  - You can override the default container name by creating a `terraform.tfvars` file or passing it via CLI:
    ```bash
    terraform apply -var="container_name=MyNginxServer"
    ```
