# Django with PostgreSQL Container in Amazon Elastic Container Registry (ECR)
[Amazon's ECR](https://aws.amazon.com/ecr/) is a container registry designed for storing, managing, and deploying docker
containers.

> **Warning:** It is not recommended to host production databases in ECR.

Disadvantages compared to Cloud Database:
1. Persistence: If not correctly configured, you risk losing your database every time the container restarts.
2. Performance and Scalability: Requires careful configuration for performance and scalability.
3. Management Overhead: You would need to handle backups, scaling, updates, and security patches manually.

## Step 1: Prepare Your Django Application
1. Dockerize Django & PostgreSQL
2. Build `docker-compose.yml` to define services for Django App & PostgreSQL Database
3. Static and Media Files - AWS S3 is a common cloud solution

## Step 2: Create an ECR Repository
Go to the Amazon ECR console and
[create a new repository](https://docs.aws.amazon.com/AmazonECR/latest/userguide/repository-create.html) for your Django Docker image.

## Step 3: Authenticate Docker Client with AWS
Follow the [instructions](https://docs.aws.amazon.com/AmazonECR/latest/userguide/registry_auth.html) provided by AWS to 
authenticate your Docker client to your ECR registry and push your Docker image.

Authenticating with AWS CLI:
```bash
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.<region>.amazonaws.com
```

Replace <region> with your AWS region (e.g., us-east-1) and <aws_account_id> with your AWS account ID.

## Step 4: Tag Docker Image
Tag the Docker image with the repository URI from the created AWS Repository:
```bash
docker tag <image>:<tag> <aws_account_id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:<tag>
```

## Step 5: Push image to ECR
```bash
docker push <aws_account_id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:<tag>
```
Replace the placeholders with your AWS account ID, region, repository name, and image tag as appropriate.

## Step 6: Verify Image in ECR
It's always necessary to verify something completed successfully.

You can list the images in the repository using this command:
```bash
aws ecr list-images --repository-name <repository-name>
```