# CI/CD Pipeline for Docker Image Build and Push to Docker Hub

This repository contains the necessary files and configurations to demonstrate a basic Continuous Integration/Continuous Deployment (CI/CD) pipeline using Jenkins and Docker. The pipeline automates the process of building a Docker image for a sample application and pushing it to Docker Hub.

---

## Lab Objectives Achieved

This lab successfully addressed the following objectives:

1.  *Jenkins Setup*: Established a Jenkins instance (local or cloud-based) as the CI/CD orchestrator.
2.  *Sample Application Creation*: Developed a simple "Hello World" Node.js application, packaged with a Dockerfile, to serve as the subject for the CI/CD pipeline.
3.  **Jenkinsfile Implementation**: Created a declarative Jenkins Pipeline script (Jenkinsfile) that defines the stages for source code checkout, Docker image building, Docker Hub authentication, and image pushing.
4.  *Docker Integration*: Utilized Docker commands within the Jenkins pipeline to build a container image and push it to a remote registry (Docker Hub).
5.  *Automated Workflow*: Configured Jenkins to automatically trigger the pipeline upon changes in the source code repository, demonstrating a fundamental CI/CD workflow.

---

## Project Structure

The key files in this repository are:

* app.js: The main Node.js application file.
* package.json: Node.js project metadata and dependencies.
* Dockerfile: Instructions for building the Docker image of the Node.js application.
* .dockerignore: Specifies files and directories to exclude from the Docker build context.
* Jenkinsfile: The core Jenkins Pipeline script, defining the CI/CD stages.

---

## How it Works (Pipeline Stages)

The Jenkins pipeline is defined in the Jenkinsfile and executes the following stages:

1.  *Checkout Source Code*: Fetches the latest code from this Git repository.
2.  *Build Docker Image*: Uses the Dockerfile to build a Docker image of the Node.js application. The image is tagged with your Docker Hub username, repository name, and a version tag (e.g., latest).
3.  *Login to Docker Hub*: Authenticates with Docker Hub using credentials securely stored in Jenkins. This step is necessary before pushing the image.
4.  *Push Docker Image to Docker Hub*: Pushes the newly built and tagged Docker image to the specified Docker Hub repository.

---

## Setup and Prerequisites

To replicate this setup, you would need:

* *Jenkins*: An installed and running Jenkins instance.
* *Docker*: Docker daemon installed and accessible by the Jenkins agent.
* *Git*: A Git client installed.
* *Docker Hub Account*: An account on Docker Hub to host your images.
* *GitHub/GitLab/Bitbucket Account*: A repository to host this project's source code.

*Jenkins Configuration Steps:*

1.  *Credentials*: Create a "Username with password" credential in Jenkins (e.g., Manage Jenkins -> Manage Credentials) with your Docker Hub username and password. Ensure the ID matches dockerhub-credentials as used in the Jenkinsfile.
2.  *New Pipeline Job*: Create a new Jenkins Pipeline job.
3.  *SCM Configuration*: Configure the job to fetch the Jenkinsfile from this Git repository (specify the repository URL and credentials if private).
4.  *Build Triggers*: Configure a build trigger (e.g., GitHub hook trigger for GITScm polling or Poll SCM) to automate pipeline execution on code changes.

---

## Verification

Upon successful execution of the Jenkins pipeline, a new Docker image should be visible in your specified Docker Hub repository. You can verify this by checking your Docker Hub profile online.
