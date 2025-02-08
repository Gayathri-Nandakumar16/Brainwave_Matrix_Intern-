**Deploying a Web Application using AWS EC2 and S3**
**Overview**
This guide provides a step-by-step process to deploy a web application on an AWS EC2 instance using an S3 bucket for storage.
**Prerequisites**
•	An AWS account
•	AWS CLI installed
•	EC2 instance (Amazon Linux)
•	S3 bucket
•	Web application files to deploy
**Step 1:** Create and Connect to an EC2 Instance
1.	Log in to the AWS Management Console.
2.	Navigate to EC2 and click Launch Instance.
3.	Choose an Amazon Linux AMI (Free Tier Eligible).
4.	Select an instance type (e.g., t2.micro for Free Tier).
5.	Configure security groups to allow HTTP (port 80) and SSH (port 22).
6.	Launch the instance and connect via SSH:
ssh -i your-key.pem ec2-user@your-ec2-instance-ip

**Step 2:** Install and Configure Apache
1.	Switch to the root user:
sudo su -
2.	Update the system:
yum update -y
3.	Install Apache:
yum install -y httpd
4.	Enable and start the Apache service:
5.	systemctl enable httpd
systemctl start httpd

**Step 3:** Create an S3 Bucket and Upload Files
1.	Navigate to S3 in the AWS Console.
2.	Click Create bucket.
3.	Enter a unique bucket name.
4.	Uncheck Block all public access if you want public access.
5.	Click Create.
6.	Open the newly created bucket and click Upload.
7.	Upload the web application files.

**Step 4:** Configure AWS CLI and Transfer Files from S3
1.	Obtain AWS credentials:
o	Go to IAM in the AWS Console.
o	Click on your username, then Security Credentials.
o	Create an Access Key and Secret Access Key.
o	Save these credentials securely.
2.	Install AWS CLI on the EC2 instance:
yum install aws-cli -y
3.	Configure AWS CLI:
aws configure
o	Enter Access Key and Secret Access Key.
o	Set Default region to your preferred AWS region.
o	Set Output format to json.
4.	Copy files from S3 to EC2:
aws s3 cp s3://your-bucket-name/ /var/www/html/ --recursive

**Step 5:** Set Permissions and Restart Apache
1.	Adjust ownership and permissions:
2.	sudo chown -R apache /var/www/html
sudo chmod -R 755 /var/www/html
3.	Restart and enable Apache:
4.	sudo systemctl restart httpd
sudo systemctl enable httpd
5.	Move files to the correct directory if needed:
6.	sudo mv "/var/www/html/aws demo/finexo-html/"* /var/www/html/
sudo systemctl restart httpd

**Conclusion**
Your web application is now deployed on AWS EC2 using files stored in an S3 bucket. You can access it via the Public IP of your EC2 instance.

[vedio]:https://github.com/Gayathri-Nandakumar16/Brainwave_Matrix_Intern-/raw/refs/heads/main/task%201/InShot_20250208_183421964.mp4
