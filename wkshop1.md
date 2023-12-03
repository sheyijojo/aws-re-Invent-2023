# Hands-on experience with Amazon CloudWatch and AWS X-Ray

# Environment Overview

- Lab 1
- Lab 2
- Lab 3
- Lab 4

This page explains how each workshop works as we used multiple AWS services to build the workshop environment. More details on how to use the applications will be provided in the labs.

## Lab 1

In this lab, we will troubleshoot performance issues with a three-tier sample application written in Python. Please check out below diagram for more detail structures of the sample application.

In this workshop I learnt how to monitor AWS services with Amazon CloudWatch and AWS X-Ray.

In order to build high performing and reliable applications, AWS provides a variety of turn-key AWS-native observability services and solutions.

![Cloudwatch](https://raw.githubusercontent.com/sheyijojo/aws-re-Invent-2023/main/images/wksh1.0.jpg)

### Problem

While troubleshooting, we will start investigating with built-in Amazon Application Load Balancer metrics.

Then will use other powerful tools, such as near-real time log inspection with CloudWatch LiveTail, creating custom metrics from logs by using metric filters in CloudWatch LogGroups.

### Resources

- AWS Cloud
- AWS VPC with cidr block - `10.0.0.06`
- Public Subnet - `10.0.1.0/24`
- Private Subnet - `10.0.3.0/24`
- Private Subnet - `10.0.4.0/24`
- Public ALB
- Internal ALB
- Cat-service.mydomain.int
- dog-service.mydomain.int
- Backend Cats
- Backend Dogs
- Public Asset Repository

The frontend application is accessed by users through a public load balancer routed acrross two Public Subnets in different Azs.

## Lab 2

In this lab, we will use a sample application, which uses Amazon API Gateway, AWS Lambda, and Amazon DynamoDB.

The application is a simple RESTful API that allows you to list, get, update, and delete. In addition, this application uses a single Lambda function to perform all the CRUD operations.

![api-gateway](https://raw.githubusercontent.com/sheyijojo/aws-re-Invent-2023/main/lab2.0.JPG)

Logs and metrics are enabled by default, but we will enable X-Ray tracing and instrument the application to capture traces, in addition,

we will enable Lambda Insights and explore the PowerTools to send custom metrics and logs to CloudWatch.

## Lab 3

In this lab, we leverage the PetAdoption website, which is deployed as part of the `https://catalog.workshops.aws/observability/en-US`

However, we don't need to change anything related to the backend as this workshop monitor the application from outside-in.

See below the screenshot of the PetSite application.

![api-gateway](https://raw.githubusercontent.com/sheyijojo/aws-re-Invent-2023/main/lab2.1play.gif)
