# CICD-Demo-Azure
CI/CD demo repository using Azure Pipelines and AWS Beanstalk

# Create React App Sample running on a Docker container with CI/CD

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

This is a simple react app made to work with docker, configured to automatically deploy to AWS on 'dev' branch commit.

For the CI, the chosen tool was Azure Pipelines.

For the CD, it uses AWS Elastic Beanstalk.

The app is not currently running on AWS to prevent cost generation.

## Tools

In the project, the following tools were used:

### `Docker`

The app is dockerized to be used in a container. The `Dockerfile` is included in the root folder.

Note that a `Dockerfile.dev` exists in the root folder as well. That is used to build an image for testing purposes by Azure Pipelines.

### `Azure Pipelines`

Azure Pipelines is a cloud-based solution by Microsoft that automatically builds and tests code projects. It supports all major languages and project types. Azure Pipelines combines continuous integration (CI) and continuous delivery (CD) to test, build, and deliver code to any destination.

It was chosen for simplicity and for being free at this scale.

We configure Azure' integration to GitHub through its web console, by granting it access to your GitHub account and allowing it to read the chosen repositories. 

The CI and CD are configured in the `.pipeline.yml`, where we tell Azure what language and which version of the compiler to use to build the image, instruct a brief test, and configure the integration with AWS Elastic Beanstalk and AWS S3 for CD.

### `AWS Elastic Beanstalk`

AWS Elastic Beanstalk is an orchestration service offered by Amazon Web Services for deploying applications, which orchestrates various AWS services, including EC2, S3, Simple Notification Service, CloudWatch, autoscaling, and Elastic Load Balancers.

It was chosen for simplicity and the small scale of the project.

For this project, EB creates a small ec2 instance running Linux and Docker and uses its Application functionality to pull images from s3 and deploy to the instance (more about the infrastructure on [terraform](https://github.com/BrunoNdeSousa/demo-terraform-beanstalk)