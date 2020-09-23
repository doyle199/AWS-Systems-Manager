# AWS-Systems-Manager
AWS Systems Manager

Systems Manager can be used to execute simple automation workflows. First, we must configure access to Systems Manager. Navigate to the IAM console and click on groups in the left menu. Then click on the Create New Group button then create a name for the group and click on Next Step.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/group1.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/group2.png)

Type SSM in the filter and check the box next to AmazonSSMFullAccess. Then click Next Step, review the selections, and click Create Group.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/full.png)

Choose users in the left menu of the IAM console and click on Add user.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/user.png)

Give the user a name and check the boxes next to the appropriate access. Then create a custom password. In this case we will uncheck the require password reset box. Then click on Next: Permissions.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/access.png)

With the Add user to group box selected, check the box for the P4SystemsManager group and click Next: Tags. Then click on Next: Review and Create user.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/tag2.png)

Take note of the Access Key ID and Secret access key.

Click on Roles in the left menu and then click the Create role button. With AWS service selected, choose EC2 and then click on Next: Permissions.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/roles.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/roles2.png)

Type AmazonSSMManagedInstanceCore into the filter. Then check the box for it and click Next: Tags then Next: Review.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/core.png)

Give it a name and click on Create role.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/role5.png)

To launch and instance that uses the Systems Manager profile navigate to the EC2 console and click on Launch Instance. From there, select an appropriate AMI and Instance Type. Click on Next: Configure Instance Details. 

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/instance1.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/instance2.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/instance3.png)

Select the IAM role that was created before in the IAM role dropdown. Then click Review and Launch and then Launch. You will need to select a key pair and then click Launch Instances. 

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/role6.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/role7.png)

To run an automation workflow as the current authenticated user, navigate to Systems Manager. Click on Automation in the left menu and then the Execute automation button.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/auto.png)

Choose a document you want to run and click next.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/doc.png)

Make sure simple execution is selected and click execute.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/exe1.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/exe2.png)

To run an automation workflow using an IAM service role complete all the same steps as above but past the Role ARN of the IAM service role created earlier into the Automation Assume Role box. Then click execute. 

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/exe3.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/exe4.png)

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/exe5.png)

To automatically update an SSM agent with CLI, download and install AWS CLI on your workstation. Then run the command “aws configure” on your workstation then fill in the details with the IAM credentials from before.

Add a tag to the instance you want to work on if you haven’t already.

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/tag3.png)

Run the following command but replace the “TagKey” and “TagValue” with your information: aws ssm create-association --targets Key=tag:TagKey,Values=TagValue --name AWS-UpdateSSMAgent --schedule-expression "cron(0 2 ? * SUN *)"

![alt text](https://github.com/doyle199/AWS-Systems-Manager/blob/master/associ.png)

Systems Manager is a strong service for automating and managing groups of resources. It can be used in combination with Trusted Advisor to have a full view of the cloud infrastructure.

