# AWS Cloud Security Lab Secure Account Setup, IAM MFA, and Core Services Exploration

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

This week's lab/project is the start of my work with the cloud, and I chose to work with AWS. The first thing I needed to do was create an account so I could get started. The account I was creating was the Free Tier version, meaning I could use the resources provided with that kind of account for six months or until I use up the free credits provided with the account. To start, I headed to the website "https://aws.amazon.com/free/" and chose the "Create a Free Account" option (IM3). Then I went through the sign-up process. This included providing my email, password, and an AWS account name. I then needed to add a payment method. Even though I was making a free-tier account, I needed to have a payment method, as I would be charged for the free credits I have whenever using cloud resources. I completed that and then verified my ID using my phone, and then chose the basic support plan that was free. I then logged in with the credentials that I created, and I was redirected to the main page of AWS, the Management Console (IM4). Currently, I was logged in as the root user.  

<img width="1627" height="641" alt="image" src="https://github.com/user-attachments/assets/accde420-15c3-4084-8d2a-734520c35d2f" />

IM3: Creating a Free Tier AWS Account

<img width="1901" height="901" alt="Screenshot 2026-06-01 093925" src="https://github.com/user-attachments/assets/19308fc3-a744-4f25-9046-2619067d11e6" />

IM4: AWS Management Console

### Part 2: Setting up Billing Alerts

My first task within AWS was to set up billing alerts. This is important for my labs/projects and for real enterprise environments as well because if you don't set a threshold for how much to spend, a company could waste thousands of dollars of resources they don't currently need without even knowing. This is because the cloud is a "pay as you go" kind of system where the resources you use on a day-to-day or week-to-week basis can change, so you don't want to spend more than what you actually need. To set up my billing alert, I clicked my account name in the top right corner and selected "Billing & Cost Management." Then, on the menu on the left side, I selected Budgets, then Create Budget. I can now configure my budget. I chose the "Monthly cost budget" option, and then set the amount to five dollars, as well as who to notify when this threshold was exceeded (IM5). I then needed to set up an alert so I would know if this budget was exceeded. Again, I would be alerted whenever the amount spent on resources exceeded the budget (IM6). To confirm, I went back to my budgets, and the one I just created was there (IM7). 

<img width="950" height="675" alt="image" src="https://github.com/user-attachments/assets/b134a048-3a25-42ba-9aba-c1d51861291d" />

IM5: Creating a Budget in AWS 

<img width="950" height="675" alt="image" src="https://github.com/user-attachments/assets/d9d347bb-66e1-43b0-a48a-ae3b3bb498f2" />

IM6: Creating an Alert for the Budget

<img width="1625" height="165" alt="image" src="https://github.com/user-attachments/assets/4e53688b-d224-4de3-89ee-d4fd43d01bdd" />

IM7: Confirming that the Budget was Created











































