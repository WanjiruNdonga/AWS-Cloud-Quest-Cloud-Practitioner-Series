---

# Quest 9: File Systems in the Cloud Lab - Shared Cloud Storage! 💾☁️

My continued development in cloud infrastructure now includes a detailed overview of the File Systems in the Cloud lab. This repo chronicles my experience with the **File Systems in the Cloud** lab, a crucial mission in the AWS Cloud Quest series. It's like setting up a shared digital drive for my cloud servers, enabling seamless collaboration and data access! 🚀

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

This practice lab provided hands-on experience with Amazon Elastic File System (EFS) and its integration with EC2 instances.

The key objectives for this mission included:
* Launch and configure an Amazon EFS file system.
* Mount the file system to an Amazon EC2 instance.
* Connect a second EC2 instance to the same file system.
* Share files between the two EC2 instances.

---

## 🛠️ AWS Services I Conquered: My Shared Storage Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS services:

* **Amazon Elastic File System (EFS):** A scalable, elastic, cloud-native NFS file system that provides shared storage for multiple EC2 instances.
* **Amazon Elastic Compute Cloud (EC2):** Used to launch and manage virtual servers (instances) to connect to the EFS file system.
* **AWS Identity and Access Management (IAM):** (Implicitly used for managing permissions, though not explicitly detailed in the provided lab steps for this specific lab, it's foundational for AWS interactions).
* **Amazon VPC (Virtual Private Cloud):** Security groups are linked to a VPC, controlling inbound and outbound traffic to instances.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

Enabling shared file access is vital for many cloud applications, and this lab provided an excellent practical foundation for implementing robust, scalable file systems.

Here's a peek at how it all went down:

---

### 1. Exploring EC2 (Initial Search)

I searched for "ec2" in the top navigation bar search box and clicked **EC2** under Services.

![EC2 Search Screenshot](images/efs_lab_1_ec2_search.png)
*Caption: Searching for EC2 in the AWS console and selecting the service.*

---

### 2. Reviewing EC2 Instances

I navigated to the "Instances" section in the left navigation pane and reviewed the names of the three existing instances (WebServer1, WebServer2, WebServer3).

![EC2 Instances Review Screenshot](images/efs_lab_2_ec2_instances.png)
*Caption: Viewing the list of running EC2 instances.*

---

### 3. Reviewing Availability Zones

I reviewed the Availability Zones for each instance under the "Availability Zone" column.

![EC2 AZ Review Screenshot](images/efs_lab_3_ec2_az.png)
*Caption: Confirming Availability Zones for EC2 instances.*

---

### 4. Navigating to Security Groups

In the left navigation pane, under **Network & Security**, I clicked **Security Groups**.

![Security Groups Navigation Screenshot](images/efs_lab_4_sg_nav.png)
*Caption: Navigating to the Security Groups section.*

---

### 5. Reviewing WebServer Security Group

In the Security Groups section, I reviewed the `Web Server SG` security group, noting that it was already linked to the web servers.

![Web Server SG Review Screenshot](images/efs_lab_5_web_sg_review.png)
*Caption: Reviewing the details of the 'Web Server SG' security group.*

---

### 6. Creating a New Security Group for EFS

I clicked **Create security group**. For **Security group name**, I typed `PetModels-EFS-1-SG`, and for **Description**, I typed `Restrict access to web servers only`. I then selected the `PetModels` VPC.

![Create EFS SG Screenshot](images/efs_lab_6_create_efs_sg.png)
*Caption: Specifying details for the new EFS security group.*

---

### 7. Configuring Inbound Rules for NFS

In the **Inbound rules** section, I added a new rule. For **Type**, I chose `NFS`. Under **Source**, I clicked to expand the dropdown and selected the `webserver sg` security group to allow NFS client access to the file system from EC2 instances linked to this security group.

![EFS SG Inbound Rule Screenshot](images/efs_lab_7_efs_sg_inbound.png)
*Caption: Configuring inbound NFS rule for the EFS security group from the 'webserver sg'.*

---

### 8. Creating the Security Group

After reviewing the details, I clicked **Create security group**. I confirmed that the security group (`sg-03077fc56a1b0d393 - PetModels-EFS-1-SG`) was created successfully.

![EFS SG Creation Success Screenshot](images/efs_lab_8_efs_sg_success.png)
*Caption: Confirmation of successful creation of the EFS security group.*

---

### 9. Navigating to FSx (Initial Search)

I searched for "fsx" in the top navigation bar search box and clicked **FSx** under Services.

![FSx Search Screenshot](images/efs_lab_9_fsx_search.png)
*Caption: Searching for FSx in the AWS console.*

---

### 10. Navigating to EFS (Initial Search)

I searched for "efs" in the top navigation bar search box and clicked **EFS** under Services.

![EFS Search Screenshot](images/efs_lab_10_efs_search.png)
*Caption: Searching for EFS in the AWS console and selecting the service.*

---

### 11. Creating a New EFS File System

On the Amazon EFS console home page, I clicked **Create file system**.

![Create EFS File System Screenshot](images/efs_lab_11_create_efs_button.png)
*Caption: Initiating the creation of a new EFS file system.*

---

### 12. Specifying EFS File System Details

In the pop-up box, for **Name**, I typed `PetModels-EFS-1`. For **VPC**, I chose the `PetModels` VPC. I then clicked **Customize**.

![EFS Details Screenshot](images/efs_lab_12_efs_details.png)
*Caption: Naming the EFS file system and selecting its VPC.*

---

### 13. Configuring File System Settings

Under **File system type**, I reviewed the types (Regional and One Zone). I cleared the checkbox to deselect **Enable automatic backups**.

![EFS Settings Screenshot](images/efs_lab_13_efs_settings.png)
*Caption: Adjusting EFS file system type and backup settings.*

---

### 14. Configuring Lifecycle Management and Throughput

Under **Lifecycle management**, for **Transition into Infrequent Access (IA)**, I chose `None`. For **Transition into Archive**, I also chose `None`. For **Throughput mode**, I chose `Bursting`.

![EFS Lifecycle and Throughput Screenshot](images/efs_lab_14_efs_lifecycle_throughput.png)
*Caption: Configuring EFS lifecycle management and throughput mode.*

---

### 15. Configuring Network Access (Mount Targets)

In the **Network access** step, under **Mount targets**, I removed the subnets for AZ `us-east-1c` and `us-east-1b`. For AZ `us-east-1a`, under **Security groups**, I removed the existing security group and then chose the `PetModels-EFS-1-SG` security group that I had previously created. I then clicked **Next**.

![EFS Network Access Screenshot](images/efs_lab_15_efs_network_access.png)
*Caption: Configuring EFS mount targets and assigning the custom security group for network access.*

---

### 16. Reviewing File System Policy

In the **File system policy** step, I clicked **Next**.

![EFS Policy Review Screenshot](images/efs_lab_16_efs_policy_review.png)
*Caption: Reviewing the EFS file system policy before creation.*

---

### 17. Creating the File System

In the **Review and create** step, I clicked **Create** at the bottom of the page. I confirmed that the file system was available and reviewed its ID.

![EFS Creation Screenshot](images/efs_lab_17_efs_create.png)
*Caption: Final step to create the EFS file system and confirming its availability.*

---

### 18. Attaching the EFS File System

I clicked **Attach** on the EFS file system details page.

![EFS Attach Screenshot](images/efs_lab_18_efs_attach.png)
*Caption: Locating the 'Attach' option for the newly created EFS file system.*

---

### 19. Copying the Mount Command

In the pop-up box, I kept the default choice of **Mount via DNS**. Under **Using the EFS mount helper**, I copied the mount command provided, which would be used in later steps to mount the EFS file system to the EC2 instances. I then clicked **Close**.

![EFS Mount Command Screenshot](images/efs_lab_19_efs_mount_command.png)
*Caption: Copying the EFS mount helper command for EC2 instances.*

---

### 20. Navigating Back to EC2 and Connecting to Instances

I navigated back to the Amazon EC2 console. (This step likely involves connecting to EC2 instances via SSH to run the mount command and test file sharing).

![Navigate Back to EC2 Screenshot](images/efs_lab_20_navigate_ec2.png)
*Caption: Returning to the EC2 console to proceed with instance connection and file sharing.*

---

### 21. Confirming Lab Completion

After successfully completing all the steps and observing the desired outcomes, I confirmed the completion of the lab, ensuring all objectives were met.

![Lab Completion Screenshot](images/efs_lab_21_lab_complete.png)
*Caption: Final confirmation of lab completion and successful achievement of objectives.*

---

## 🔑 Key Takeaways & File System Revelations: 🔑

This lab significantly deepened my understanding of shared file systems in AWS, particularly concerning Amazon EFS.

* **EFS for Scalable Shared Storage:** Amazon EFS provides a highly scalable and elastic NFS file system that can be shared across multiple EC2 instances, simplifying data sharing and collaboration.
* **Seamless EC2 Integration:** Mounting EFS to EC2 instances is straightforward, enabling instances to access the same data without needing to provision and manage storage on each individual instance.
* **Security Groups for Access Control:** Security groups are critical for controlling network access to EFS mount targets, ensuring that only authorized EC2 instances can connect to the file system.
* **Cost-Effectiveness and Elasticity:** EFS is designed to be cost-effective, with pricing based on usage, and it automatically scales storage capacity up or down as needed, eliminating the need for manual provisioning.
* **NFS Protocol:** EFS utilizes the Network File System (NFSv4) protocol, making it compatible with Linux-based EC2 instances.

---

## ✨ What's Next on My Cloud Quest: ✨

Mastering file systems in the cloud is a critical step towards building robust and collaborative cloud environments. This lab has provided me with invaluable hands-on experience in implementing shared storage. I'm now eager to delve into more advanced data management topics, including data migration, backup strategies, and optimizing file system performance, as I continue my journey to become a Cloud Architect.

---

## 🤝 Let’s Connect!

Curious about cloud file systems, EFS best practices, or just want to chat about building scalable cloud environments? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---
✨ Sharing data effortlessly, one EFS file system at a time! 🔒☁️✨

---
