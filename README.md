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

## How it works

This deployment uses 4 containers:
1. SyncupV2 - the backend and main application
2. ImageManagementService - a utility service to handle user image uploads
3. PostgreSQL database - database for both SyncupV2 and the ImageManagementService
4. Nginx - nginx as a proxy to redirect all requests correctly

## Usage

Once all three containers are up and running, you can access the deployment through Nginx, which will be accessible on port 80.  
the Endpoints which are available: 
 - `/api/**` any calls are being redirected to the SyncUpV2 container <br>
 example:  `http://localhost:80/api/v1/auth/user/` will be redirected to `http://backend:8080/v1/auth/user`
 - `/images/**` any calls are being redirected to static resources inside the `./persistent_data/uploaded_images/` directory <br>
 example: 
 `http://localhost:80/images/originals/image1.webp` will be mapped to the file: `./persistent_data/uploaded_images/originals/image1.webp`