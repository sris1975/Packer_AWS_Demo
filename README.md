# Packer_AWS_Demo
Creating AWS instance using Packer

Create AWS account and access key for remote API access:
1.	Create AWS account from Amazon.
2.	Go to AWS console 
    https://console.aws.amazon.com/iam/home#/users
3.	From Access Management, click on Users and create a new user.
4.	Select “Access Type” as Programmatic access.
5.	From “Set permissions” page, select “Attach existing policies directly” and select Administrator access.
6.	In the next tab, add tags and click on create user. You will now get Access key ID and Secret access key.
 
Launch instance from AWS console:
1.	Open Amazon EC2 console https://console.aws.amazon.com/ec2/
2.	From the navigation bar, select the Region in which to launch your instances. You can select any Region that's available to you, regardless of your location. 
3.	From the console dashboard, choose Launch Instance. 
4.	The next page lists all the AMI templates. Select the template for which you want to create an instance. Next to the template you can find AMI id which should be specified in the packer template (source_ami field). Click on Select.
5.	Select the type of instance. That will "instance_type" in the packer template. ("instance_type": "t2.micro")
6.	Click on “Review & Launch” and then Launch.
7.	This instance will be used to create the templates.

Run Packer template:
1. From command line, type "packer validate AWS_Instance.json".
2. This should result in a message saying "Template validated successfully".
3. Now run the command "packer build \
    -var 'aws_access_key=YOUR ACCESS KEY' \
    -var 'aws_secret_key=YOUR SECRET KEY' \
    AWS_Instance.json".
4. Once this is done, you should have an instance in the Amazon AWS.

