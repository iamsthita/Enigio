# Enigio Interview Assignment: AWS CloudWatch Monitoring Setup

## Task:

In AWS, there is a possibility of setting up Dashboards, Metrics, and alarms using the CloudWatch Service. In this task, we would like to set up infrastructure in AWS using a CloudFormation script. The infrastructure that is to be created should follow these requirements.

- A simple EC2 instance that can be accessed and monitored by CloudWatch.
- A dashboard that can present statistics of at least these predefined metrics:
  - CPU Utilization in %
  - Check the status of the instance (StatusCheckFailed_System)
  - Check the overall status of the System (StatusCheckFailed)
  - Credit Usage of the EC2
- Optional: Alarm to monitor CPU utilization percentage reaching critical levels.

Proper security groups, security, load balancing, and other infrastructure are not part of this task. The focus is solely on the monitoring capabilities in CloudWatch using an EC2 as the main target to be monitored.

## Solution:

![Architecture Diagram](https://github.com/iamsthita/Enigio/assets/132139960/fafc044a-9b81-4de6-83d9-4850d92e099f)

This repository contains a CloudFormation script (`EnigioCloudWatchSetup.yaml`) to set up monitoring capabilities in AWS CloudWatch for an EC2 instance. The infrastructure created includes:

- An EC2 instance for monitoring.
- A CloudWatch alarm to monitor CPU utilization and send notifications if it exceeds 80%.
- A CloudWatch dashboard to visualize EC2 instance metrics, including CPU utilization, status check failures, and CPU credit balance.

## Prerequisites

Before deploying the CloudFormation stack, ensure you have:

1. Installed the AWS CLI.
2. Configured your AWS credentials using `aws configure`.

## Deployment

To deploy the CloudFormation stack, run the following command:

```bash
aws cloudformation create-stack --stack-name Enigio --template-body file://C:/Jena/Interview/Enigio/EnigioCloudWatchSetup.yaml
```

## Contents

- `EnigioCloudWatchSetup.yaml`: CloudFormation script to set up the infrastructure.
- `README.md` (this file): Instructions and overview of the solution.

## Resources Created

<img width="861" alt="image" src="https://github.com/iamsthita/Enigio/assets/132139960/4b3a1d53-5649-4279-a815-bf9654bc5cd3">

## Monitoring Setup Details

### EC2 Instance

- Type: `t2.micro`.
- Monitoring enabled.

### CloudWatch Alarm

- Monitors CPU utilization.
- Alarm triggered if CPU utilization exceeds 80%.
- Notifications sent via Amazon SNS to the specified email address.
<img width="896" alt="image" src="https://github.com/iamsthita/Enigio/assets/132139960/6092fc89-1e30-4654-9554-36930b588a42">


### CloudWatch Dashboard

- Visualizes the following metrics:
  - CPU Utilization (%)
  - Status Check Failed (System)
  - Status Check Failed
  - CPU Credit Balance
 
<img width="540" alt="image" src="https://github.com/iamsthita/Enigio/assets/132139960/5e1756be-e3ff-4203-86f1-0af96b7c1589">


## Outputs

After deployment, you can access the CloudWatch dashboard using the provided URL in the CloudFormation stack outputs.
<img width="584" alt="image" src="https://github.com/iamsthita/Enigio/assets/132139960/8fcccbf6-edca-4f05-8cd0-e0fac077da89">
