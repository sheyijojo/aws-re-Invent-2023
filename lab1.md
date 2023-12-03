## Lab 1 - Infrastructure Monitoring

Amazon CloudWatch is an infrastructure monitoring and management platform that lets you observe and monitor resources and applications on AWS, on premises, and on other clouds.

Amazon CloudWatch provides visibility into the entire AWS domain including networking, compute, application, database and storage.

It provides native integration with AWS services, such as, Amazon CloudFront, Amazon EC2, Amazon S3 and AWS Lambda etc.

In addition, you can also install the CloudWatch agent on the Amazon EC2 or On-premise servers to collect system-level metrics as well as custom metrics and logs to gain visibility into your environment.

![infra](https://raw.githubusercontent.com/sheyijojo/aws-re-Invent-2023/main/images/lab1_infra.JPG)

## Benefits

- Monitor application performance
- Perform root cause analysis
- Optimize resources proactively
- Test website impacts and end-user experience

By leveraging Amazon CloudWatch empowers you to continuously monitor and diagnose performance issues, enabling you to proactively address bottlenecks and optimize the performance of your infrastructure and applications.

## 1.1 - The Problem

In this lab, you are the administrator of a 3-tier application. The application is currently experiencing reported performance issues.

### The Goal

As a system administrator, your mission is to pinpoint areas of performance degradation and identify the root causes using Amazon CloudWatch.

### How the lab is structured

As described in the Environment overview, this lab consists of one frontend and two backend services running on EC2 instances, using the Application ELB as the service endpoint for each service and DynamoDB Table as the database.

In terms of development language, all applications are written in Python, but that does not mean you need to be familiar with Python to run this lab.
