# Web_application_with_aws_serverless_services

# 🌐 AWS Contact Form Project

This project demonstrates a **serverless web application** built using **AWS Lambda**, **API Gateway**, and **DynamoDB**.  
It allows users to submit a contact form, and their details are stored securely in a DynamoDB table.  
After submission, users are redirected to a thank-you page.

---

## 🚀 Features
- Static **Contact Form (HTML, CSS, JS)** hosted via AWS Lambda or S3  
- **DynamoDB Integration** for storing form submissions  
- **AWS API Gateway** to connect the frontend and backend  
- **Serverless Backend** using AWS Lambda (Python)  
- Responsive, animated, and beginner-friendly frontend  

---

## 🧩 Project Structure
AWS_Contact_Project/
│
├── contactus.html # Main contact form
├── success.html # Success/thank-you page
├── lambda_function.py # AWS Lambda backend code
└── README.md # Project documentation


---

## 🛠️ Prerequisites
Before you start, make sure you have:
- An **AWS Account**
- **AWS CLI** installed and configured  
  (Run `aws configure` to set up access key and region)
- **Python 3.9+** installed on your system
- Basic knowledge of AWS Lambda and API Gateway

---

## ⚙️ Step-by-Step Setup Guide

### **1️⃣ Create a DynamoDB Table**
1. Go to the AWS Management Console → DynamoDB  
2. Click **Create table**
3. Table name: `cktable`
4. Partition key: `fname` (String)  
5. Click **Create table**

---

### **2️⃣ Create a Lambda Function**
1. Go to **AWS Lambda → Create function**  
2. Choose:
   - Name: `contactFormHandler`
   - Runtime: `Python 3.9` (or newer)
   - Permissions: Create a new role with basic Lambda + DynamoDB access  
3. After creation, open the function → click **Upload from → .zip file**  
4. Zip the following files and upload:
   contactus.html
   success.html
   lambda_function.py
5. In the **Code** section, ensure your handler is set to: Handler: lambda_function.lambda_handler
6. Deploy the function.

---

### **3️⃣ Create an API Gateway**
1. Go to **Amazon API Gateway → Create API → REST API**
2. Create a new resource, e.g. `/dev`
3. Under `/dev`, add two methods:
- **GET** → Integration type: Lambda Function → choose your function  
- **POST** → Integration type: Lambda Function → choose the same function  
4. Deploy the API (Actions → Deploy API → New Stage → Name: `prod`)
5. Copy the **Invoke URL** (e.g. `https://abc123.execute-api.us-east-1.amazonaws.com/prod/dev`)

---

### **4️⃣ Update the Form Action**

In your `contactus.html`, set the form's `action` to your Invoke URL:

```html
<form action="https://your-api-gateway-url/prod/dev" method="post">


