# AWS Cloud Security Lab: Secure Account Setup, IAM MFA, and Core Services Exploration

## Objective

This lab/project aims to develop foundational skills in cloud computing and security by building and securing an AWS environment using industry best practices. In this lab, I focused on implementing essential security measures to protect a cloud account from unauthorized access and unexpected costs. Using the AWS Free Tier, I created and configured an AWS account, set up a cost budget with alert notifications, and enabled Multi-Factor Authentication (MFA) on the root account. I then applied Identity and Access Management (IAM) principles by creating an administrative IAM user with appropriate permissions and transitioning away from using the root account for daily operations. I also secured the IAM user with MFA, reinforcing layered security within the environment. Additionally, I explored core AWS services, including IAM, EC2, S3, and VPC, and created an S3 bucket to simulate cloud storage usage while observing how resources differ across regions. The lab concluded with an understanding of the AWS Shared Responsibility Model, highlighting the division between AWS-managed and customer-managed security. This project demonstrates secure cloud account configuration, cost management, identity control, and foundational cloud service knowledge relevant to cybersecurity and cloud roles. Quick disclaimer that this week's project didn't have too much technical work/advanced configurations, more so exploring the cloud environment and getting familiar with the main concepts and tools. 

### Skills Learned

This project has provided hands-on experience with the following cloud and security skills:

- Secure AWS account configuration and initial cloud environment setup
- Implementation of billing controls using AWS Budgets and cost alert notifications
- Identity and Access Management (IAM) user creation and permission assignment (AdministratorAccess)
- Exploration of core AWS services, including IAM, EC2, S3, and VPC
- Understanding AWS regions and resource isolation across geographic locations
- Basic navigation and management of the AWS Management Console

### Tools Used

- Amazon Web Services (AWS Free Tier)
- AWS Management Console (Web-Based Interface)
- Web Browser (Chrome)

## Current Lab Environment Architecture/Setup

Below are screenshots of my lab Architecture before and after this week's lab/project (IM1&2). There were no new hardware or VM additions to the environment, but I worked with AWS this week, including creating a Free Tier account and working with some of the main tools within AWS. 

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/33e950cc-6a67-4983-898d-c784807fdd76" />
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/3e51f5f0-e857-45ab-bb87-e2d4fb84428f" />

IM1&2: Current Lab Environment/Architecture Before and After this Week's Lab/Project

## Steps/Procedure

### Part 1: Creating an AWS Free Tier Account

This week's lab/project is the start of my work with the cloud, and I chose to work with AWS. The first thing I needed to do was create an account so I could get started. The account I was creating was the Free Tier version, meaning I could use the resources provided with that kind of account for six months or until I use up the free credits provided with the account. To start, I headed to the website "https://aws.amazon.com/free/" and chose the "Create a Free Account" option (IM3). Then I went through the sign-up process. This included providing my email, password, and an AWS account name. I then needed to add a payment method. Even though I was making a free-tier account, I needed to have a payment method, as I would be charged for the free credits I have whenever using cloud resources. I completed that and then verified my ID using my phone, and then chose the basic support plan that was free. I then logged in with the credentials that I created, and I was redirected to the main page of AWS, the Management Console (IM4). Currently, I am logged in as the root user.  

<img width="1627" height="641" alt="image" src="https://github.com/user-attachments/assets/accde420-15c3-4084-8d2a-734520c35d2f" />

IM3: Creating a Free Tier AWS Account

<img width="1901" height="901" alt="Screenshot 2026-06-01 093925" src="https://github.com/user-attachments/assets/19308fc3-a744-4f25-9046-2619067d11e6" />

IM4: AWS Management Console

### Part 2: Setting up Billing Alerts

My first task within AWS was to set up billing alerts. This is important for my labs/projects and for real enterprise environments as well, because if you don't set a threshold for how much to spend, a company could waste thousands of dollars of resources they don't currently need without even knowing. This is because the cloud is a "pay as you go" kind of system where the resources you use on a day-to-day or week-to-week basis can change, so you don't want to spend more than what you actually need. To set up my billing alert, I clicked my account name in the top right corner and selected "Billing & Cost Management." Then, on the menu on the left side, I selected Budgets, then Create Budget. I can now configure my budget. I chose the "Monthly cost budget" option, and then set the amount to five dollars, as well as who to notify when this threshold was exceeded (IM5). I then needed to set up an alert so I would know if this budget was exceeded. Again, I would be alerted whenever the amount spent on resources exceeded the budget (IM6). To confirm, I went back to my budgets, and the one I just created was there (IM7). 

<img width="950" height="675" alt="image" src="https://github.com/user-attachments/assets/b134a048-3a25-42ba-9aba-c1d51861291d" />

IM5: Creating a Budget in AWS 

<img width="950" height="675" alt="image" src="https://github.com/user-attachments/assets/d9d347bb-66e1-43b0-a48a-ae3b3bb498f2" />

IM6: Creating an Alert for the Budget

<img width="1625" height="165" alt="image" src="https://github.com/user-attachments/assets/4e53688b-d224-4de3-89ee-d4fd43d01bdd" />

IM7: Confirming that the Budget was Created

### Part 3: Securing Root Account with MFA

The next part in configuring my AWS account was securing the root account with Multi-Factor Authentication. This is important because it adds an extra layer of security to my account whenever I log in. To configure this, I clicked my account name in the top right and selected "Security Credentials." I then scrolled down until I saw MFA. I saw that it hadn't been assigned yet (IM8). I then went through the process of configuring MFA. For the type of authentication, I chose the Authenticator app and set that up (IM9). I then went on my phone and typed in the code twice to confirm authentication, and it worked. I then went back to the Security Credentials page and confirmed that MFA was set up (IM10).

<img width="1599" height="586" alt="Screenshot 2026-06-01 095228" src="https://github.com/user-attachments/assets/fe5e5517-0b57-498e-b1b8-42a08fe79f6b" />

IM8: Security Credentials Page with MFA not yet configured

<img width="700" height="575" alt="Screenshot 2026-06-01 095446" src="https://github.com/user-attachments/assets/08b16746-5283-44c6-922a-936848161295" />

IM9: Setting up Authenticator App for MFA

<img width="1570" height="157" alt="Screenshot 2026-06-01 095532" src="https://github.com/user-attachments/assets/a235988e-a080-49e7-91b9-19f3a4e5d516" />

IM10: MFA Configured for Root Account

### Part 4: Creating IAM Admin User

Although I was currently logged in as the Root account, it is typically not advised to use the root account as it has complete control over all configurations without being able to be restricted. However, if I create an admin account, it will still have all the administrative access the Root account does, but is able to be restricted and monitored like any other user account. Essentially, the Admin account will be used for day-to-day admin tasks, and the root account will be used to deal with billing and other tasks like that. Here is how I created the admin user.

1. **CREATING ADMIN USER.** To create the admin user, I first went to the search bar and typed "IAM" and clicked on it. I currently have no users created, so I clicked "Create User" in the top right (IM11). I then filled out the information for the user, like the username (Admin-User), giving the user access to the AWS Management Console, and setting a secure password for the user (IM12).
2. **SETTING PERMISSIONS.** Next up was setting permissions for the admin user. I chose the option "Attach policies directly," which means that those permissions will apply directly to that user. I then chose the permission policy "AdministratorAccess," which gave the admin user typical administrator privileges like the root account.
3. **CONFIRMING ACCOUNT AND SAVING LOGIN-INFO.** After configuring everything, I created the user. I then needed to save the login information because, from now on, unless I was logging in as the Root account, I needed a separate link to log in as the Admin-User account. I securely saved the login info so I could log in to the admin account whenever (IM14).

<img width="1916" height="367" alt="Screenshot 2026-06-01 095715" src="https://github.com/user-attachments/assets/d9093e9e-64fb-4135-b0a3-668d2ac061ac" />

IM11: IAM Users with no current users

<img width="1344" height="681" alt="image" src="https://github.com/user-attachments/assets/607a8fa6-978f-45dd-a57e-b52cb86dff58" />

IM12: Configuring Admin-User Account

<img width="891" height="389" alt="Screenshot 2026-06-01 095901" src="https://github.com/user-attachments/assets/6b133c05-c622-4fbc-8f09-d24c8c5e0dc9" />

IM13: Configuring Permissions for Admin Account

<img width="1335" height="245" alt="Screenshot 2026-06-01 100101" src="https://github.com/user-attachments/assets/d46a88c7-3780-40df-88db-09eaea3ae035" />

IM14: Login-Info for Admin User Account

### Part 5: Logging In as IAM Admin User

Now that I created the admin user, I wanted to confirm that the account was working, and I could log in as the admin user instead of the Root account. To do this, I simply logged out of the Root account, used the link for the admin account I saved, and then entered my credentials for the admin user (IM15). When I logged in, I could see the admin account username at the top right with the AWS Management Console open, confirming that the admin user account was configured correctly (IM16). 

<img width="1289" height="472" alt="image" src="https://github.com/user-attachments/assets/62fe08a9-c23a-45b5-9ccc-06aa555aaa34" />

IM15: Logging in to Admin User Account Instead of Root Account

<img width="1602" height="855" alt="image" src="https://github.com/user-attachments/assets/300f10ff-73e0-4e64-8c05-76c0a0522e37" />

IM16: Logged in as Admin User Account with AWS Management Console

### Part 6: Enabling MFA on Admin Account

I also wanted to enable MFA on the Admin Account as well. I did the same process as I did with the Root account, and MFA was successfully enabled on the admin account (IM17). 

<img width="1595" height="365" alt="Screenshot 2026-06-01 112847" src="https://github.com/user-attachments/assets/2ece8df1-24e7-44b4-8dca-9f5039dcf19f" />

IM17: MFA Enabled on Admin Account

### Part 7: Exploring Core AWS Services

Now that my accounts are set up and ready to go, and since I'm new to the cloud, I want to explore the core cloud services that run in AWS. These services include

1. **IAM (IDENTIY & ACCESS MANAGMENT).** I already went through this service a little in the previous parts, but I wanted to explore a little bit more. Some of the main sections in IAM include Users (Like the admin one I created earlier) (IM18), IAM User Groups (similar to OUs and Security Groups in AD, I hadn't created any yet) (IM19), and Policies (basically permissions) (IM20).
2. **EC2 (ELASTIC COMPUTE CLOUD).** This service is responsible for running instances (virtual machines) within the cloud. Some of the main sections within the service I looked at were the instance types (the types of VMs you could run based on things like CPU and price per hour) (IM22) and Security Groups (Similar to Security Groups in AD, put in based on permissions) (IM23)
3. **S3 (STORAGE).** This service manages storage for cloud resources, similar to Google Drive (IM24). You can store anything, like files and documents, in here with what are called "buckets". I created a sample bucket for this project and named it "amir-test-bucket-5813 (IM25&26)."
4. **VPC (VIRTUAL PRIVATE CLOUD).** This service manages all things networking within the cloud. This is mainly your private cloud within AWS (IM27). Some of the areas I looked at were my default VPC (IM28), subnets (default) (IM29), and route tables (also default) (IM30).

<img width="1609" height="218" alt="Screenshot 2026-06-01 113033" src="https://github.com/user-attachments/assets/acf40f27-add7-4bb8-ab27-4794964920ae" />

IM18: IAM Users Within IAM Service

<img width="1603" height="171" alt="Screenshot 2026-06-01 113048" src="https://github.com/user-attachments/assets/d355e3ad-c83d-4a9e-aaa7-3427f97463a2" />

IM19: IAM User Groups Within IAM Service (None Created Yet)

<img width="1602" height="774" alt="Screenshot 2026-06-01 113107" src="https://github.com/user-attachments/assets/40a4b17a-61ee-4767-8809-5882b66046af" />
<img width="1596" height="777" alt="Screenshot 2026-06-01 113130" src="https://github.com/user-attachments/assets/98b02998-3fe0-4efd-920f-8c67569d97e4" />

IM20&21: Policies Within IAM Service (Also Specifically AdministratorAccess)

<img width="1660" height="386" alt="Screenshot 2026-06-01 113307" src="https://github.com/user-attachments/assets/8bb21636-c538-4e0e-86f0-eb1a0a945aba" />

IM22: Instance Types Within EC2 Service

<img width="1667" height="158" alt="Screenshot 2026-06-01 113342" src="https://github.com/user-attachments/assets/bd6f14a0-11d4-4f67-a355-6b17ff27bdf4" />

IM23: Security Groups within EC2 Service

<img width="1271" height="246" alt="Screenshot 2026-06-01 113428" src="https://github.com/user-attachments/assets/019d2e90-577e-49c5-9968-8386902f196d" />

IM24: AWS S3 Service

<img width="1635" height="630" alt="Screenshot 2026-06-01 113534" src="https://github.com/user-attachments/assets/6e2294e1-53cb-469f-85f2-8450520c80ab" />
<img width="1641" height="401" alt="Screenshot 2026-06-01 113653" src="https://github.com/user-attachments/assets/caa0157c-3180-4903-be44-85123d37eaa4" />

IM25&26: Configuring and Creating a Test Bucket Within S3

<img width="1902" height="862" alt="Screenshot 2026-06-01 113838" src="https://github.com/user-attachments/assets/8ca411ad-ea15-4044-a8e5-e09098267ec2" />

IM27: VPC Service Dashboard

<img width="1659" height="246" alt="Screenshot 2026-06-01 113850" src="https://github.com/user-attachments/assets/c3cb2b14-e3d5-4513-badc-083e65608f65" />

IM28: Default VPC within VPC Service

<img width="1651" height="297" alt="Screenshot 2026-06-01 113913" src="https://github.com/user-attachments/assets/e0005d72-346c-40c1-9807-8862d341b3b4" />

IM29: Default Subnets Within VPC Service

<img width="1666" height="165" alt="Screenshot 2026-06-01 113924" src="https://github.com/user-attachments/assets/9bea1af9-e3d4-4b2f-b152-015e2449dd20" />

IM30: Default Route Table within VPC Service

### Part 8: Understanding Regions in AWS

The last part of this project was to understand the different regions within AWS. Like any online service, whether that is online gaming or e-commerce, regions play a vital role in operations. Here are some of the things I explored

1. **EXPLORING REGIONS.** I first looked at different regions that AWS had available. By pressing the region name in the top right corner, I could see the different regions based on continent. Each continent had multiple locations in it (IM31).
2. **CHANGING REGIONS TO SEE DIFFERENCES IN RESOURCES.** One cool thing about the cloud, and specifically AWS, is that changing the region could have an impact on what resources are available and the amount available. To test this, I changed from my current region to us-west-2, which is Oregon. When doing this, I didn't notice anything different in resources in S3 or EC2, but in VPC, I noticed that fewer subnets were available in us-west-2 compared to my region, us-east-1 (six compared to four). (IM32).

<img width="397" height="860" alt="Screenshot 2026-06-01 114129" src="https://github.com/user-attachments/assets/3c75c691-4684-42d3-bd48-edce17cfc405" />

IM31: Different Regions Within AWS

<img width="1663" height="232" alt="Screenshot 2026-06-01 114245" src="https://github.com/user-attachments/assets/d8bb4af7-4b36-43e6-99e3-2ffe26034001" />

IM32: Fewer subnets within a region that is not my own. 

## Conclusion

This lab was successful in demonstrating the foundational concepts of cloud computing and cloud security through the use of Amazon Web Services (AWS). Throughout the project, key security practices were implemented in a practical cloud environment, including secure account configuration, billing and cost management, Multi-Factor Authentication (MFA) deployment, and Identity and Access Management (IAM) administration. The creation of an IAM administrative user and the transition away from the root account reinforced industry best practices surrounding account security and access control.

In addition to securing the AWS environment, this project provided hands-on exposure to several core AWS services, including IAM, EC2, S3, and VPC. Exploring these services helped develop an understanding of how cloud resources are organized and managed, while the creation of an S3 bucket introduced the fundamentals of cloud-based storage. Switching between AWS regions further demonstrated how resources are isolated geographically and highlighted an important aspect of cloud infrastructure design.

Throughout the lab, emphasis was placed on security-first principles such as least privilege, layered authentication, and cost monitoring. Learning about the AWS Shared Responsibility Model reinforced the distinction between AWS-managed security and customer-managed security, emphasizing the role organizations play in protecting their own data, identities, and configurations within the cloud.

Overall, this project strengthened the connection between cloud security theory and real-world implementation. It provided practical experience with securing AWS accounts, managing user access, controlling costs, and navigating cloud services commonly used in enterprise environments. Potential areas for future expansion include launching and securing EC2 instances, implementing more granular IAM roles and policies, configuring monitoring and logging services such as CloudTrail and CloudWatch, and exploring advanced networking and security controls within AWS.











































