```sh
#Description
#Your enterprise's agility, customer satisfaction, and business growth depends on setting up great observability.

# In order to build high performing and reliable applications, AWS provides a variety of turn-key AWS-native observability services and solutions.

# In this workshop, you will learn how to monitor AWS services with Amazon CloudWatch and AWS X-Ray, get hands-on experience with the most common use cases, and learn about and implement the newest features available

```

https://catalog.workshops.aws/native-cloudwatch-experience/en-US

ReInvent 2023 - Workshop Session - COP306 - Hands-on experience with Amazon CloudWatch and AWS X-Ray

## Infrastucture Monitoring

While troubleshooting, we will start investigating with built-in Amazon Application Load Balancer metrics. Then will use other powerful tools, such as near-real time log inspection with CloudWatch LiveTail, creating custom metrics from logs by using metric filters in CloudWatch LogGroups.

In this lab, you are the administrator of a 3-tier application. The application is currently experiencing reported performance issues.

## The Goal

As a system administrator, your mission is to pinpoint areas of performance degradation and identify the root causes using Amazon CloudWatch.

## How the lab is structured

As described in the Environment overview, this lab consists of one frontend and two backend services running on EC2 instances, using the Application ELB as the service endpoint for each service and DynamoDB Table as the database.

In terms of development language, all applications are written in Python, but that does not mean you need to be familiar with Python to run this lab.

It appears that the /dog service may have performance bottlenecks. So far, there are several clues we found.

The average response time of /dog backend is much slower than the /cat.

The database operation trend shows around 1-digit millisecond.
In some cases, requests with /dog URL take more than 3 second.

"Requests using the /dog URI intermittently take more than 3 seconds." If this is true, adding percentile statistics(e.g. p90, p95, p99) of response time graph may help to see the trends of 3 second requests. Then we can add relevant alarms.

## workshop 2

You can surface insights from best practices, security, fault tolerance, and performance using Amazon Inspector, AWS Config, Service Quotas, AWS Health, AWS Well-Architected Tool, and AWS Trusted Advisor. Join this workshop to learn how to automate these insights intelligently using AWS DevOps and machine learning tools. Also, learn how to use Amazon CloudWatch, AWS Lambda, and AWS ML services. You must bring your laptop to participate.

## URL LInk

```sh
https://catalog.workshops.aws/intelligently-automating-cloud-operations/en-US

```

dev instance id - i-0b23c254366b67189
prod instance id(webserver) - 0i-030c52e8eeb4b0d64

Our Goals
Last week the following situation arose:

“One of our developers deployed a new software version on our development instance that accidentally allowed malicious users to utilize it as a source in a denial of service attack.”

For this first scenario we are tasked with the following goals:

Monitor for specific AWS Health Events.
Identify the resources involved in the Event.
Differentiate between Production and Development resources.
Isolate development resources from sending/receiving traffic.
Send a notification to a team responsible for investigating the event.
Validate that our solution works as expected.
You can proceed to the next section by clicking Next at the bottom of this page.

Topic ARN

arn:aws:sns:us-east-1:069198715347:aws_health_abuse_report_sns_reinvent

aws_health_dos_lambda_policy

## Containerize a windows app

ENT304 - Containerize a Windows application and go serverless with AWS Fargate

Description
Organizations are looking for ways to migrate their Windows-based applications on premises to an optimized architecture on AWS. In this workshop, learn about key concepts, such as images, containers, and Dockerfiles. Use the AWS App2Container tool to containerize and migrate Windows applications to AWS. Build an image with EC2 Image Builder, store it on Amazon ECR, and then run it Serverless on AWS Fargate.

javy@amazon.com
workshop@aws

iis-default-web-site-e771d544
app id

C:\Windows\system32\config\systemprofile\AppData\Local\app2container\iis-default-web-site-e771d544\analysis.json

$APP_ID='iis-default-web-site-e771d544'
$REGISTRY_URI='707169060320.dkr.ecr.us-west-2.amazonaws.com/my-net-app:1.0-linux'
$TAG='a2c-windowsservercore-ltsc2019'
aws ecr get-login-password | docker login --username AWS --password-stdin $REGISTRY_URI

send an email to have access to this resources

#script to deploy
#Deploy initial microservicesHeader anchor link
#We've provided some prebuilt Docker images for you to deploy as microservices within Amazon EKS. These microservices will act as HTTP APIs for a retail application that we will be interacting with through the command line.

#We need to deploy these containers into Amazon EKS. We have provided a script to simplify this for you. Feel free to review the contents of the script.

# Launch the script that will deploy the containers to EKS:

```sh
!/bin/sh

set -x

echo "Launching script " $(basename "${BASH_SOURCE}")
. ./lab_env.sh
printvars

export REDIS_PRIMARY_HOST=$(kubectl get cluster/$CLUSTER_NAME --template={{.status.clusterEndpoint.address}})

read -r -d '' SERVICE1_MANIFEST <<EOF
apiVersion: v1
kind: Service
metadata:
  name: inventory-service
spec:
  selector:
    app: inventoryapi
  ports:
    - protocol: TCP
      port: 8000
      targetPort: 8000
EOF
echo "${SERVICE1_MANIFEST}" > service_inventory.yaml
kubectl apply -f service_inventory.yaml

read -r -d '' SERVICE2_MANIFEST <<EOF
apiVersion: v1
kind: Service
metadata:
  name: order-service
spec:
  selector:
    app: orderapi
  ports:
    - protocol: TCP
      port: 8001
      targetPort: 8001
EOF
echo "${SERVICE2_MANIFEST}" > service_order.yaml
kubectl apply -f service_order.yaml
sleep 20

```

```sh

http POST ${INVENTORY_API}/products name="Soda" price=1.99 quantity=100
http GET ${INVENTORY_API}/products


http POST ${ORDER_API}/orders quantity=1 id=01HGC3H5DF49650ZE0D4Y2TK38


HTTP/1.1 200 OK
content-length: 237
content-type: application/json
date: Tue, 28 Nov 2023 23:18:57 GMT
server: uvicorn
x-process-time: 0.006155967712402344

[
    {
        "id": "01HGC3H5DF49650ZE0D4Y2TK38",
        "name": "Soda",
        "price": 1.99,
        "quantity": 100
    },
    {
        "id": "01HGC3GRX9GATFK4A504T2MX6T",
        "name": "Donut",
        "price": 19.99,
        "quantity": 10
    },
    {
        "id": "01HGC3ENJ6902DBP5JAJ1TJE3A",
        "name": "Pizza",
        "price": 28.99,
        "quantity": 10
    }
]
```

```

```

{
"fee": 0.398,
"pk": "01HGC3VW6DW8QWRCYXS31V3T8P",
"price": 1.99,
"product_id": "01HGC3H5DF49650ZE0D4Y2TK38",
"quantity": 1,
"status": "pending",
"total": 2.388
}

```py
#order-worker.py

import time
from decouple import config
from main import Order, redis_order
from redis.cluster import RedisCluster as Redis

stream_refunds = f"events:refunds"
consumer_group = f"order:group"
consumer_name = f"{consumer_group}:1"

try:
    redis_order.xgroup_create(
        name=stream_refunds,
        groupname=consumer_group,
        mkstream=True
    )
    print(f"Consumer Group {consumer_group} created!")
except:
    print(f"Consumer Group {consumer_group} already exists!")

while True:
    try:
        results = redis_order.xreadgroup(
            groupname=consumer_group,
            consumername=consumer_name,
            streams={stream_refunds: '>'},
            count=1,
            block=1000,
            noack=False
        )
        if results != []:
            for result in results:
                obj = result[1][0][1]
                try:
                    order = Order.get(obj['pk'])
                    order.status = 'refunded'
                    order.save()
                    # Send an email that the order is refunded
                except Exception as e:
                    print(str(e))
    except Exception as e:
        print(str(e))
    time.sleep(10)


'''
Sample payload

['refund_order', [('1652889846896-0', {'pk': '01G3BYJVVHJFVJ0EEX7YRR53S1', 'product_id': '01G3BYDWW5HXK8GHCZ9NPKDZAC', 'price': '28.99', 'fee': '5.798','total': '69.576', 'quantity': '2', 'status': 'completed'})]]
'''
```

mcgehee@amazon.com

sudo mount -t nfs svm-01b5b0c0c92d43399.fs-083325cf59d1f9ed8.fsx.us-west-1.amazonaws.com:/vol1 /mnt/ontap

L00M5-ATV2I-C2I4E-9E6V7-EDVN1

Containerize a windows app

ENT304 - Containerize a Windows application and go serverless with AWS Fargate

Description
Organizations are looking for ways to migrate their Windows-based applications on premises to an optimized architecture on AWS. In this workshop, learn about key concepts, such as images, containers, and Dockerfiles. Use the AWS App2Container tool to containerize and migrate Windows applications to AWS. Build an image with EC2 Image Builder, store it on Amazon ECR, and then run it Serverless on AWS Fargate.

javy@amazon.com
workshop@aws

iis-default-web-site-e771d544
app id

C:\Windows\system32\config\systemprofile\AppData\Local\app2container\iis-default-web-site-e771d544\analysis.json

$APP_ID='iis-default-web-site-e771d544'
$REGISTRY_URI='707169060320.dkr.ecr.us-west-2.amazonaws.com/my-net-app:1.0-linux'
$TAG='a2c-windowsservercore-ltsc2019'
aws ecr get-login-password | docker login --username AWS --password-stdin $REGISTRY_URI

send an email to have access to this resources

#script to deploy
#Deploy initial microservicesHeader anchor link
#We've provided some prebuilt Docker images for you to deploy as microservices within Amazon EKS. These microservices will act as HTTP APIs for a retail application that we will be interacting with through the command line.

#We need to deploy these containers into Amazon EKS. We have provided a script to simplify this for you. Feel free to review the contents of the script.

#Launch the script that will deploy the containers to EKS:
`sh`
!/bin/sh

set -x

echo "Launching script " $(basename "${BASH_SOURCE}")
. ./lab_env.sh
printvars

export REDIS_PRIMARY_HOST=$(kubectl get cluster/$CLUSTER_NAME --template={{.status.clusterEndpoint.address}})

read -r -d '' SERVICE1_MANIFEST <<EOF
apiVersion: v1
kind: Service
metadata:
name: inventory-service
spec:
selector:
app: inventoryapi
ports: - protocol: TCP
port: 8000
targetPort: 8000
EOF
echo "${SERVICE1_MANIFEST}" > service_inventory.yaml
kubectl apply -f service_inventory.yaml

read -r -d '' SERVICE2_MANIFEST <<EOF
apiVersion: v1
kind: Service
metadata:
name: order-service
spec:
selector:
app: orderapi
ports: - protocol: TCP
port: 8001
targetPort: 8001
EOF
echo "${SERVICE2_MANIFEST}" > service_order.yaml
kubectl apply -f service_order.yaml
sleep 20
