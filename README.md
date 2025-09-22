# HW1 – EC2 Webserver Setup

This README provides step-by-step instructions for creating and tearing down a basic EC2 webserver on AWS.

---

## Prerequisites

* An AWS account with Free Tier access
* Basic familiarity with the AWS Management Console
* A web browser

---

## Step 1: Create a Security Group

1. Navigate to **EC2 Service** → **Security Groups** → **Create Security Group**
2. Enter the following details:

   * Name: `basic_webserver`
   * Description: `basic_webserver`
   * VPC: Default VPC
3. Add inbound rule:

   * Type: HTTP
   * Source: Anywhere (IPv4)
   * Description: `http`
4. Add tags:

   * `Name = basic_webserver`
   * `Env = Dev`

---

## Step 2: Launch an EC2 Instance

1. Navigate to **EC2 Service** → **Instances** → **Launch Instances**
2. Enter details:

   * Name: `basic_webserver`
   * AMI: Amazon Linux AMI (default)
   * Instance Type: `t2.micro`
3. Key Pair:

   * Create new if none exists → `class7_keypair` in `.pem` format
   * Or select an existing key pair
4. Network Settings: Keep defaults and select the HTTP security group created earlier
5. Advanced Details: Paste startup script into the User Data section
6. Click **Launch Instance**

---

## Step 3: Access the Webserver

1. Wait until the instance state is **Running**
2. Copy the **Public DNS** from the instance details
3. Open a browser and enter the Public DNS url starting with http://

---

## Step 4: Terminate the Instance

1. Navigate to **EC2 → Instances**
2. Select the running instance
3. From the **Instance State** menu, choose **Terminate**
4. Confirm termination

---

## Summary

* Security group created for HTTP access
* EC2 instance launched with Amazon Linux AMI
* Webserver accessed via Public DNS
* Instance terminated to avoid ongoing charges

