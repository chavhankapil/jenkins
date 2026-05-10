# jenkins
jenkins repo
# Jenkins CI Demo

A simple Jenkins project demonstrating a pipeline for building, testing, and deploying a Python application with Docker.

## Project Overview

This repository contains:
- `Jenkinsfile` — Jenkins pipeline definition
- `helloworld.py` — example Python script
- `dockerfile` — Docker image build instructions
- `README.md` — project documentation

## Features

- Build and run a Python script
- Build a Docker image
- Push the Docker image to Docker Hub
- Deploy a container from the image
- Use Jenkins credentials for secure Docker login

## Prerequisites

- Jenkins installed and configured
- Docker installed on the Jenkins agent
- A Docker Hub account
- Jenkins credentials stored for Docker Hub access

## Jenkins Credentials

Create a Jenkins credential of type `Username with password` with the ID:

- `dockerhub-credentials`

This credential is used in the pipeline to log in to Docker Hub securely.

## Pipeline Stages

The Jenkins pipeline includes the following stages:

1. `Hello` — verify Jenkins is connected
2. `Check Python Version` — print the Python version
3. `Run Python Script` — execute `helloworld.py`
4. `Build Docker Image` — build the Docker image
5. `Push Docker Image` — log in to Docker Hub and push the image
6. `Container Deployment` — run a container from the pushed image

## Usage

1. Add this repository to your Jenkins job.
2. Ensure the Jenkins agent has Docker and Python available.
3. Add the `dockerhub-credentials` credential in Jenkins.
4. Run the pipeline.

## Notes

- Update the Docker image name in `Jenkinsfile` if you use a different Docker Hub repository.
- Keep credentials secure and do not store them in plaintext.
