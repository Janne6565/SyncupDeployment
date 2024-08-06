# Syncup Deployment

This repository contains the necessary files for deploying the Syncup project, which consists of two Spring Boot applications: SyncUpV2 (the main application) and ImageManagementService (a utility service for handling image uploads).

## Prerequisites

Before deploying the Syncup project, ensure that you have the following:

- Docker installed on your local machine
- Docker Compose installed on your local machine
- Locally build both images (as they arent available on Dockerhub yet)

## Getting Started

To get started with the deployment, follow these steps:

1. Clone this repository to your local machine:

    ```shell
    git clone https://github.com/janne6565/SyncupDeployment.git
    ```

2. Navigate to the project directory:

    ```shell
    cd SyncupDeployment
    ```

5. Start the containers:

    ```shell
    docker-compose up -d
    ```

    This will start the SyncUpV2 and ImageManagementService containers in the background.

6. Verify that the containers are running:

    ```shell
    docker ps
    ```

    You should see the SyncUpV2 and ImageManagementService containers listed.

## Configuration

The deployment configuration for the Syncup project can be found in the `docker-compose.yml` file. You can modify this file to customize the deployment according to your needs.

## Usage

Once the containers are up and running, you can access the SyncUpV2 application at `http://localhost:8080` and the ImageManagementService at `http://localhost:8081`.
