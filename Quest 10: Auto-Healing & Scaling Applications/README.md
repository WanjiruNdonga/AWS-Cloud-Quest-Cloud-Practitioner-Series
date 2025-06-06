---

# Quest 10: Auto-Healing & Scaling Applications Lab - Resilient & Dynamic Cloud Solutions ☁️🚀

This project documents my hands-on experience with the **Auto-Healing & Scaling Applications** lab, focusing on deploying and managing highly available and scalable applications in the cloud using AWS. This lab emphasizes configuring AWS services to automatically adjust application capacity, ensuring steady performance and cost efficiency even with fluctuating workloads.

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

The core goals achieved in this practice lab included:
* Creating an Amazon EC2 Auto Scaling group.
* Assigning EC2 instances to the Auto Scaling group.

---

## 🛠️ AWS Services I Conquered: My Elasticity Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS services:
* **Amazon EC2 (Elastic Compute Cloud):** Provided the fundamental compute capacity for the application instances.
* **Amazon EC2 Auto Scaling:** The central service used to automate the scaling of EC2 instances, ensuring optimal performance and availability.
* **Amazon CloudWatch:** Utilized for monitoring metrics and creating alarms that trigger scaling actions.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

This section outlines the key steps undertaken to achieve the lab objectives, building a robust and scalable application environment:

---

### 1. Initial EC2 Instance Preparation

* I accessed the AWS Management Console and navigated to the EC2 service. I identified and inspected the pre-configured "Game Server" EC2 instance provided in the lab environment, then accessed it via its public IP address to confirm connectivity and operational status.

![Screenshot (5774)](https://github.com/user-attachments/assets/353c13b7-2b0b-4f48-8468-269799775fdc)

![Screenshot (5775)](https://github.com/user-attachments/assets/f3cbf5a1-6506-452b-96c4-66f9c4075775)

![Screenshot (5776)](https://github.com/user-attachments/assets/a20b5b1d-fb24-4de3-b86d-0dd15242e1d2)

![Screenshot (5778)](https://github.com/user-attachments/assets/baf6a81e-7629-47e8-bbc4-9ce2f45d36f3)
*Overview of the initial EC2 instance (Game Server) and its status.*

---

### 2. Creating a Custom Amazon Machine Image (AMI)

* To create a repeatable blueprint for my Auto Scaling Group, I created a custom Amazon Machine Image (AMI) directly from the operational "Game Server" instance. This AMI encapsulates the necessary software and configurations for future instances.

![Screenshot (5780)](https://github.com/user-attachments/assets/40a12dc6-4447-4176-a51f-e1ad30427b59)

![Screenshot (5781)](https://github.com/user-attachments/assets/22ee00ec-5311-4b37-812f-7617d8180cd3)
![Screenshot (5782)](https://github.com/user-attachments/assets/783e19c7-861a-4f96-8471-8f8088467022)

![Screenshot (5783)](https://github.com/user-attachments/assets/bc257209-ec38-40c5-9012-bf28475ac438)
*The process of creating a custom AMI from the Game Server instance.*

---

### 3. Developing a Launch Template

* I designed a Launch Template to standardize the configuration of new instances that would be launched by the Auto Scaling Group. In this template, I specified the newly created AMI, selected the `t3.micro` instance type for cost-effectiveness and performance, configured the `GameServerKeyPair` for secure SSH access, and assigned the `WebServerSecurityGroup` to manage network traffic.

![Screenshot (5784)](https://github.com/user-attachments/assets/20592707-cac6-4b78-bb1b-9daeba9ae374)

![Screenshot (5785)](https://github.com/user-attachments/assets/064217c2-3836-48f7-8fe6-197ddef1e14e)

![Screenshot (5786)](https://github.com/user-attachments/assets/a31d69ac-d828-4d63-bc73-f14e2e931363)

![Screenshot (5787)](https://github.com/user-attachments/assets/8e83a8b7-5816-47c5-8e6d-e7035dc10cb8)

![Screenshot (5788)](https://github.com/user-attachments/assets/bae6ea84-81b5-4f2d-b270-8fb0f15c068e)

![Screenshot (5790)](https://github.com/user-attachments/assets/9aea2621-52c7-416a-a737-0322b447da45)

![Screenshot (5791)](https://github.com/user-attachments/assets/12b4b86e-06ae-4c72-ba5f-2544dacf28b3)

![Screenshot (5792)](https://github.com/user-attachments/assets/aaff3037-58ef-44a4-aa64-9bd5b7255548)

![Screenshot (5793)](https://github.com/user-attachments/assets/95e46e76-32a9-4c7a-8c03-95976a9a7bb7)

![Screenshot (5794)](https://github.com/user-attachments/assets/c2468610-6524-40b7-8521-7665744c0bc6)
![Screenshot (5795)](https://github.com/user-attachments/assets/ef3c9f9f-7777-4d2f-ba51-7226bdffa569)
*Configuration details of the Launch Template, including AMI, instance type, key pair, and security group settings.*

---

### 4. Implementing the Auto Scaling Group

* The core of the auto-healing and scaling solution involved creating an Auto Scaling Group. I configured this group to leverage the Launch Template I had just created. I set the desired, minimum, and maximum capacity parameters for the group, which dictate how many instances should ideally be running and the boundaries for automatic scaling. While specific scaling policies (e.g., Target Tracking scaling policy based on CPU utilization via CloudWatch alarms) are an inherent part of Auto Scaling, this setup laid the groundwork for dynamic capacity adjustments.

* **Navigated to Auto Scaling Groups:** From the EC2 console, I proceeded to the "Auto Scaling Groups" section in the left navigation pane.

    ![Screenshot (5796)](https://github.com/user-attachments/assets/f77d2e5d-2ff9-40fe-a5fa-bade5c3410f0)
    *Navigating to the Auto Scaling Groups section in the EC2 console.*

* **Initiated Creation:** I clicked "Create Auto Scaling group" and selected the Launch Template that was created in the previous step as the basis for the new group.
    * I gave the Auto Scaling group a descriptive name `RegularCustomerGameServer`.

    ![Screenshot (5797)](https://github.com/user-attachments/assets/47324885-1b70-4029-bd24-09f0f266a329)
    ![Screenshot (5798)](https://github.com/user-attachments/assets/2cda6c05-156a-4f05-aaff-0d8656c79f82)
    *Initiating the creation of a new Auto Scaling group and selecting the Launch Template.*

* **Configured Group Details:**
    * I specified the **Group size**, setting the `Desired capacity` to `2`, `Minimum capacity` to `2`, and `Maximum capacity` to `4` to ensure consistent availability.
 
    ![Screenshot (5802)](https://github.com/user-attachments/assets/2d531330-5d69-4012-a177-fb5f265b2273)

    * I selected the appropriate **VPC** and **subnets** to define where the instances would be launched.

    ![Screenshot (5799)](https://github.com/user-attachments/assets/bb876d8f-993b-4427-b0d9-b2bb0b8d4737)

* **Established Scaling Policies:** (This would involve configuring rules for automatic scaling based on metrics)
    * I configured a **target tracking scaling policy** to automatically adjust capacity in response to demand, such as scaling out (adding instances) if CPU utilization exceeded 70%.

    ![Screenshot (5803)](https://github.com/user-attachments/assets/36df7ff9-8bda-4112-862c-47b3f7e18934)

* **Automatic Scaling Group Summary:**

    ![Screenshot (5807)](https://github.com/user-attachments/assets/adf68037-33d7-47a6-b90f-7cc75776dcf9)
    ![Screenshot (5808)](https://github.com/user-attachments/assets/08c45ca2-6715-45de-a874-40028718b028)
    ![Screenshot (5809)](https://github.com/user-attachments/assets/e23f911f-8ce0-4efb-bbda-83cdb32aef82)
    ![Screenshot (5810)](https://github.com/user-attachments/assets/d0b09c05-e91c-43d8-88cc-3d23076883dd)

* **Automatic Scaling Group Created:**
  
    ![Screenshot (5811)](https://github.com/user-attachments/assets/6e0c62be-db15-4f05-941c-4ac29f3a3727)

    ![Screenshot (5812)](https://github.com/user-attachments/assets/0fe0b7ff-8862-4aa7-b45a-836d795398b3)

    ![Screenshot (5814)](https://github.com/user-attachments/assets/e6f80cf4-f8c1-43e5-95c9-ad16205333fc)

    ![Screenshot (5813)](https://github.com/user-attachments/assets/9aa5a863-d89c-4876-a01e-a9457aa08396)

* **For advanced automation**, I also explored setting up **scheduled actions**, like automatically scaling out or scaling down the number of instances to 0 at a specific time (e.g., 01:00 AM daily) to optimize costs during off-peak hours.

    * **Scaling Out Scheduled Action:**

    ![Screenshot (5815)](https://github.com/user-attachments/assets/76dc7950-d645-44ac-ac1b-3758a106d92b)

    ![Screenshot (5816)](https://github.com/user-attachments/assets/23d6b7b4-64b1-4dfa-be02-d0a0aaf0df8d)

    ![Screenshot (5817)](https://github.com/user-attachments/assets/994a96b6-dd25-47d9-a73a-0e7bef74669b)

    * **Scaling Down Scheduled Action:**
 
    ![Screenshot (5818)](https://github.com/user-attachments/assets/f78a5bc3-3ac2-435b-b057-f2b704699ba8)

    ![Screenshot (5820)](https://github.com/user-attachments/assets/c62cf776-a5eb-4088-8a98-bd458c648084)
    *Setting up scheduled actions for the Auto Scaling group.*

---

## 🔑 Key Learnings & Revelations: 🔑

This lab provided critical insights into building resilient and scalable cloud applications:

* **Automated Scalability:** Deepened my understanding of how Amazon EC2 Auto Scaling groups dynamically adjust EC2 instance capacity in response to real-time demand, thereby ensuring consistent application availability and performance.
* **Cost Optimization through Elasticity:** Learned how Auto Scaling contributes significantly to cost optimization by automatically provisioning instances only when needed and terminating them when demand subsides, preventing over-provisioning.
* **Infrastructure as Code Foundation:** Gained hands-on experience with fundamental building blocks like AMIs and Launch Templates, which are essential for creating repeatable, version-controlled, and robust cloud infrastructure.
* **Enhanced Application Resilience:** Recognized the inherent auto-healing capabilities of Auto Scaling, which automatically detects and replaces unhealthy instances, thereby significantly enhancing application resilience and fault tolerance.

---

## ✨ What's Next on My Cloud Quest: ✨

Mastering auto-healing and scaling is paramount for deploying production-grade applications. This lab has provided invaluable hands-on experience in implementing robust elasticity. I'm now eager to delve into more advanced scaling policies, predictive scaling, and integrating Auto Scaling with other AWS services like Load Balancers for even greater resilience and performance.

---

## 🤝 Let’s Connect!

Curious about cloud scalability, Auto Scaling best practices, or just want to chat about building resilient cloud applications? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---

✨ Building resilient clouds, one scalable app at a time! 📈🛡️☁️✨

---
