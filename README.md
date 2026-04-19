# 📊 CBDS Project

## 🎥 Project Demo Video

Click below to watch the full demonstration of the project:

[![Watch Demo](https://img.youtube.com/vi/hvX6EIT-Dcg/0.jpg)](https://youtu.be/hvX6EIT-Dcg)

---

## 📌 Title
Create an IAM User Who Should Have EC2 Access Through Policy and S3 Through Group – Role-Based Access Control Using AWS IAM for EC2 Management

---

## 🎯 Objective
To implement Role-Based Access Control (RBAC) in Amazon Web Services using AWS Identity and Access Management, by creating an IAM user who gets:

- EC2 access through a directly attached IAM policy  
- S3 access through an IAM group  

This demonstrates how AWS permissions can be assigned using both:

- User-based policy assignment  
- Group-based access control  

AWS states that IAM users start with no permissions by default, and access is granted by attaching policies to users or groups.

---

## 📖 Project Description
This project shows how to securely manage AWS resource access by separating permissions:

- EC2 permissions → assigned directly to the IAM user  
- S3 permissions → assigned indirectly through a group  

This is a practical example of RBAC (Role-Based Access Control) where access is based on role/group membership.

---

## 🛠️ Tools / Services Used
- Amazon Web Services (AWS) Console  
- AWS Identity and Access Management (IAM)  
- Amazon EC2  
- Amazon S3  

---

## 🏗️ Architecture / Access Design

### 👤 User Access Plan
- **IAM User:** ec2-s3-user  
- **EC2 Access:** Direct policy attached to user  
- **S3 Access:** Through group membership  
- **Group Name:** S3AccessGroup  

---

## ⚙️ Implementation Steps

### 🔹 Step 1: Sign in to AWS Console
- Open AWS Management Console  
- Search for IAM  
- Open IAM Dashboard  

---

### 🔹 Step 2: Create IAM User
- Go to Users → Create user  
- Enter username: **ec2-s3-user**  
- Click Next  

✅ **Result:** User created with no permissions  

---

### 🔹 Step 3: Attach EC2 Access to User
- Go to Permissions  
- Click Attach policies directly  
- Select: **AmazonEC2FullAccess**  

💡 *This gives EC2 access directly to the user*

---

### 🔹 Step 4: Create IAM Group for S3
- Go to User groups → Create group  
- Name: **S3AccessGroup**  
- Attach policy: **AmazonS3FullAccess**  

💡 *This implements RBAC using groups*

---

### 🔹 Step 5: Add User to Group
- Open S3AccessGroup  
- Click Add users  
- Select **ec2-s3-user**  

✅ **Result:** User gets S3 access via group  

---

### 🔹 Step 6: Verify Permissions
Check user permissions:

- Direct: AmazonEC2FullAccess  
- Via Group: AmazonS3FullAccess  

---

### 🔹 Step 7: Create Login Access (Optional)
- Enable console login  
- Set username & password  

---

### 🔹 Step 8: Test Access

#### 🔸 EC2 Test
- View instances  
- Launch instance  
- Start/Stop instances  

#### 🔸 S3 Test
- View buckets  
- Upload/download files  
- Create bucket  

---

## ✅ Expected Output
The user should be able to access:

- EC2 → via direct policy  
- S3 → via group  

---

## 🎉 Outcome
Successfully implemented Role-Based Access Control (RBAC) in AWS IAM:

- ✔️ User-specific permission → EC2  
- ✔️ Group-based permission → S3  

This project demonstrates secure and structured access management in AWS.
