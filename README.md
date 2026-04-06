# cbds-project
Title
Create an IAM User Who Should Have EC2 Access Through Policy and S3 Through Group – Role-Based Access Control Using AWS IAM for EC2 Management
Objective

To implement Role-Based Access Control (RBAC) in Amazon Web Services using AWS Identity and Access Management, by creating an IAM user who gets:

EC2 access through a directly attached IAM policy
S3 access through an IAM group

This demonstrates how AWS permissions can be assigned using both:

User-based policy assignment
Group-based access control

AWS states that IAM users start with no permissions by default, and access is granted by attaching policies to users or to groups the user belongs to. IAM groups are used to manage permissions for multiple users more easily.

Project Description

This project shows how to securely manage AWS resource access by separating permissions:

EC2 permissions → assigned directly to the IAM user
S3 permissions → assigned indirectly through a group

This is a practical example of RBAC (Role-Based Access Control) because access is based on the user’s role/group membership rather than giving all permissions directly to the user. AWS recommends using policies and groups to control what users can do in your account.

Tools / Services Used
Amazon Web Services Console
AWS Identity and Access Management
Amazon EC2
Amazon S3
Architecture / Access Design
User Access Plan
IAM User: ec2-s3-user
EC2 Access: Granted via policy attached directly to user
S3 Access: Granted via group membership
Group Name: S3AccessGroup
Implementation Steps
Step 1: Sign in to AWS Console
Open the AWS Management Console
Search for IAM
Open the IAM Dashboard
Step 2: Create IAM User
In IAM, click Users
Click Create user
Enter user name: ec2-s3-user
Click Next
Expected Result

A new IAM user is created with no permissions initially. AWS confirms that new IAM users have no permissions unless policies are attached.

Step 3: Attach EC2 Access Directly to User
While creating the user (or after user creation), go to Permissions
Choose Attach policies directly
Search for:
AmazonEC2FullAccess
(or use a custom EC2-only policy if your faculty/project requires least privilege)
Select the policy
Continue and finish user creation
Why This Step?

This gives the IAM user access to EC2 resources directly through a user policy.

Expected Result

The user can:

View EC2 dashboard
Launch EC2 instances
Start/stop/reboot instances
Manage EC2-related operations (depending on policy)

AWS explains that EC2 actions require explicit IAM permissions and are controlled using identity-based policies.

Step 4: Create IAM Group for S3 Access
In IAM, click User groups
Click Create group
Enter group name: S3AccessGroup
In permissions, search for:
AmazonS3FullAccess
(or AmazonS3ReadOnlyAccess if only viewing is needed)
Select the policy
Click Create group
Why This Step?

Instead of giving S3 access directly to the user, access is given through a group, which is the RBAC concept.

AWS documents that groups let you assign permissions to multiple users and manage access more easily.

Step 5: Add IAM User to S3 Group
Open User groups
Select S3AccessGroup
Click Add users
Select ec2-s3-user
Click Add users
Expected Result

Now the user inherits:

S3 access from the group
EC2 access from the direct policy

This is the main RBAC implementation part of the project.

Step 6: Verify User Permissions

Open the user ec2-s3-user and check:

Directly Attached Permissions
AmazonEC2FullAccess
Permissions via Group
AmazonS3FullAccess (or ReadOnly, depending on your selection)
Expected Result

The user should now have:

EC2 access through policy
S3 access through group
Step 7: Create Login Access (Optional but Recommended for Demo)

If you want to log in using the created IAM user:

Open the IAM user ec2-s3-user
Go to Security credentials
Enable Console access
Set:
Username
Password
Save the credentials
Expected Result

The user can log in separately and test only the permissions assigned.

AWS notes that IAM users can be given console access or programmatic access depending on use case.

Step 8: Test Access

Login with the created IAM user and test:

EC2 Test
Open EC2 Dashboard
Check whether the user can:
View instances
Launch an instance
Start/stop instance
S3 Test
Open S3 Dashboard
Check whether the user can:
View buckets
Upload/download objects
Create buckets (if FullAccess is used)
Expected Output

The user should be able to access:

EC2 because of direct policy
S3 because of group membership
Outcome

Successfully implemented RBAC in AWS IAM where:

User-specific permission → EC2
Group-based permission → S3

This proves that AWS IAM can be used to manage access in a structured and secure way.
