![Alt input](5._Host_a_Dynamic_Web_App_on_AWS_with_Kubernetes_and_Amazon_EKS (1).png)

```markdown
# Dynamic Application Deployment on AWS EKS

## Overview
This project showcases the deployment of a dynamic application on AWS using the Elastic Kubernetes Service (EKS). The architecture ensures high availability and fault tolerance by spanning multiple availability zones and incorporates essential AWS services for optimal security and performance.

## Architecture
The system architecture spans multiple AWS services:
- **Amazon EKS**: Manages Kubernetes pods for the application.
- **Amazon RDS**: Provides a resilient, multi-AZ relational database.
- **AWS VPC**: Isolates the environment with public and private subnets.
- **AWS IAM**: Secures access to AWS resources.
- **Amazon Route 53**: Manages DNS and traffic flow.
- **Amazon ECR**: Stores and manages Docker container images.
- **Network Load Balancer**: Balances incoming user traffic across the deployed services.


## Prerequisites
- AWS Account
- Configured AWS CLI
- Docker installed on your local machine
- kubectl configured to interact with your Kubernetes cluster
- An existing EKS cluster

## Deployment Instructions

1. **Create an EKS Cluster**: If you haven't done so already, create your EKS cluster.
   ```sh
   eksctl create cluster --name your-cluster-name --region your-region
   ```

2. **Configure kubectl**: Ensure kubectl is configured to communicate with your EKS cluster.
   ```sh
   aws eks update-kubeconfig --name your-cluster-name
   ```

3. **Deploy the Kubernetes Resources**: Apply the Kubernetes manifests to establish your pods, services, and ingress.
   ```sh
   kubectl apply -f k8s/
   ```

4. **Verify Deployment**: Confirm that all resources are up and running.
   ```sh
   kubectl get all
   ```

5. **Access the Application**: Use the DNS name provided by the Network Load Balancer to access the application.

## Repository Structure

```
/root
│
├── k8s/ - Kubernetes manifest files
├── src/ - Source code for the dynamic application
└── README.md
```

## Security

AWS IAM roles and policies are configured to adhere to the principle of least privilege, ensuring secure access management.

## Monitoring

CloudWatch has been integrated to monitor the application's performance and health.

## Contributing

If you're interested in contributing, please fork the repository and use a feature branch. Pull requests are welcome.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

