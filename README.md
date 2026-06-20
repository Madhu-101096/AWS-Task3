# AWS S3, Lambda, CloudWatch, EC2 & Application Load Balancer Project

## Project Overview

This project demonstrates the implementation of AWS services including:

- Amazon S3
- AWS Lambda
- Amazon CloudWatch
- Amazon EC2
- Application Load Balancer (ALB)

The project consists of:

1. Creating a private S3 bucket.
2. Uploading files to the bucket.
3. Logging S3 upload events using AWS Lambda and CloudWatch Logs.
4. Launching two EC2 instances.
5. Hosting a web application on both instances.
6. Configuring an Application Load Balancer.
7. Routing traffic through the load balancer to the EC2 instances.

---

## Architecture

```text
S3 Bucket
    │
    ▼
S3 Event Notification
    │
    ▼
AWS Lambda
    │
    ▼
CloudWatch Logs


Internet
    │
    ▼
Application Load Balancer
    │
 ┌──┴──┐
 ▼     ▼
EC2-1 EC2-2
```

---

## Services Used

### Amazon S3

- Created a private S3 bucket.
- Blocked all public access.
- Uploaded files to the bucket.

### AWS Lambda

- Created a Lambda function using Python.
- Configured the function to trigger whenever a new object is uploaded to S3.

### Amazon CloudWatch

- Captured S3 upload events through Lambda execution logs.
- Verified successful uploads using CloudWatch Log Groups and Log Streams.

### Amazon EC2

- Launched two EC2 instances.
- Installed Apache HTTP Server.
- Configured custom web pages on each instance.

### Application Load Balancer

- Created a Target Group.
- Registered both EC2 instances.
- Created an Application Load Balancer.
- Verified traffic distribution between both instances.

---

## Implementation Steps

### Task 1: S3 Upload Logging

#### Step 1: Create S3 Bucket

- Created a private S3 bucket.
- Enabled Block Public Access.

#### Step 2: Create Lambda Function

- Runtime: Python
- Function Name: `s3-upload-logger`

#### Step 3: Configure S3 Trigger

Configured:

```text
Event Type:
ObjectCreated (All)
```

#### Step 4: Upload Files

Uploaded sample files to S3.

#### Step 5: Verify CloudWatch Logs

Verified uploaded file events in:

```text
CloudWatch
→ Log Groups
→ /aws/lambda/s3-upload-logger
```

---

### Task 2: EC2 and Application Load Balancer

#### Step 1: Launch EC2 Instances

Created:

```text
web-server-1
web-server-2
```

#### Step 2: Install Apache

Installed and started Apache Web Server on both instances.

Server 1:

```html
<h1>Server 1</h1>
```

Server 2:

```html
<h1>Server 2</h1>
```

#### Step 3: Create Target Group

Created a target group and registered:

```text
web-server-1
web-server-2
```

Verified both targets are healthy.

#### Step 4: Create Application Load Balancer

Configured:

```text
Type: Application Load Balancer
Scheme: Internet Facing
Protocol: HTTP
Port: 80
```

Attached the target group.

#### Step 5: Test Load Balancer

Accessed the ALB DNS name and verified traffic was successfully routed to both EC2 instances.

---

## Screenshots

The following screenshots are included in the repository:

```text
screenshots/
│
├── s3-bucket-created.png
├── s3-files-uploaded.png
├── lambda-function-created.png
├── s3-trigger-configured.png
├── cloudwatch-log-group.png
├── cloudwatch-upload-events.png
├── ec2-instances-running.png
├── apache-server1.png
├── apache-server2.png
├── target-group-healthy.png
├── alb-created.png
└── alb-output.png
```

---

## Result

Successfully implemented:

- Private Amazon S3 bucket
- File upload monitoring
- AWS Lambda integration
- CloudWatch logging
- Two EC2 web servers
- Application Load Balancer
- Load-balanced web application deployment

---
