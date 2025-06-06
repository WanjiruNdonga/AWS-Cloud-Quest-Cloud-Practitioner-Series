---

# Quest 9: File Systems in the Cloud Lab - Shared Cloud Storage! 💾☁️

This lab explored the setup of shared cloud storage using AWS services. It details my experience with the **File Systems in the Cloud** lab, a crucial mission in the AWS Cloud Quest series. It's like setting up a shared digital drive for my cloud servers, enabling seamless collaboration and data access! 🚀

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

* I searched for "ec2" in the top navigation bar search box and clicked **EC2** under Services.

![Screenshot (5650)](https://github.com/user-attachments/assets/58b27693-bf9e-44fb-a238-646e7b64132b)
*Searching for EC2 in the AWS console and selecting the service.*

---

### 2. Reviewing EC2 Instances

* I navigated to the "Instances" section in the left navigation pane and reviewed the names of the three existing instances (WebServer1, WebServer2, WebServer3).
* I also reviewed the Availability Zones for each instance under the "Availability Zone" column.

![Screenshot (5651)](https://github.com/user-attachments/assets/1d74404c-4794-4414-9fc6-3d9589c4882a)
*Viewing the list of running EC2 instances.*

---

### 3. Navigating to Security Groups

* In the left navigation pane, under **Network & Security**, I clicked **Security Groups**.

![Screenshot (5655)](https://github.com/user-attachments/assets/836d4712-d5dc-4dd8-8be6-ee86f0f92ea3)
*Navigating to the Security Groups section.*

---

### 4. Reviewing WebServer Security Group

* In the Security Groups section, I reviewed the `Web Server SG` security group, noting that it was already linked to the web servers.

![Screenshot (5652)](https://github.com/user-attachments/assets/d1395e83-2483-462a-abc5-f1047e0cc03a)
*Reviewing the details of the 'Web Server SG' security group.*

---

### 5. Creating a New Security Group for EFS

* I clicked **Create security group**. For **Security group name**, I typed `PetModels-EFS-1-SG`, and for **Description**, I typed `Restrict access to web servers only`. I then selected the `PetModels` VPC.

![Screenshot (5656)](https://github.com/user-attachments/assets/f262cafb-9010-45dd-9daf-eeae9e269176)
*Specifying details for the new EFS security group.*

---

### 6. Configuring Inbound Rules for NFS

* In the **Inbound rules** section, I added a new rule. For **Type**, I chose `NFS`. Under **Source**, I clicked to expand the dropdown and selected the `webserver sg` security group to allow NFS client access to the file system from EC2 instances linked to this security group.

![Screenshot (5657)](https://github.com/user-attachments/assets/a8052794-d868-40c5-b56d-e0e626d1e5ef)
*Configuring inbound NFS rule for the EFS security group from the 'webserver sg'.*

---

### 7. Creating the Security Group

* After reviewing the details, I clicked **Create security group**. I confirmed that the security group (`sg-03077fc56a1b0d393 - PetModels-EFS-1-SG`) was created successfully.

![Screenshot (5659)](https://github.com/user-attachments/assets/4b4949ff-f99d-4202-b4bf-9957ceb9b50c)

![Screenshot (5660)](https://github.com/user-attachments/assets/e599502a-6213-4c9d-82fa-3318aa3938c8)
*Confirmation of successful creation of the EFS security group.*

---

### 8. Navigating to FSx (Initial Search)

 * I searched for "fsx" in the top navigation bar search box and clicked **FSx** under Services.

![Screenshot (5661)](https://github.com/user-attachments/assets/b2e02323-77e1-42ef-83e6-82b334b774da)
![Screenshot (5662)](https://github.com/user-attachments/assets/268891d8-a541-4e82-b1cd-103d6909b603)
*Searching for FSx in the AWS console.*

---

### 9. Navigating to EFS (Initial Search)

* I searched for "efs" in the top navigation bar search box and clicked **EFS** under Services.

![Screenshot (5663)](https://github.com/user-attachments/assets/34c359cb-4d33-4f83-a617-e7cab39f44b4)
*Searching for EFS in the AWS console and selecting the service.*

---

### 10. Creating a New EFS File System

* On the Amazon EFS console home page, I clicked **Create file system**.

![Screenshot (5664)](https://github.com/user-attachments/assets/7f851484-c124-415d-8e70-448d1778e330)
*Initiating the creation of a new EFS file system.*

---

### 11. Specifying EFS File System Details

* In the pop-up box, for **Name**, I typed `PetModels-EFS-1`. For **VPC**, I chose the `PetModels` VPC. I then clicked **Customize**.

![Screenshot (5665)](https://github.com/user-attachments/assets/e4779217-92db-43a5-a9b1-8bbdfd211aea)
*Naming the EFS file system and selecting its VPC.*

---

### 12. Configuring File System Settings

* Under **File system type**, I reviewed the types (Regional and One Zone). I cleared the checkbox to deselect **Enable automatic backups**.

![Screenshot (5667)](https://github.com/user-attachments/assets/34aa7a02-dda5-4dbf-89bf-3dfc5e228bc4)
*Adjusting EFS file system type and backup settings.*

---

### 13. Configuring Lifecycle Management and Throughput

* Under **Lifecycle management**, for **Transition into Infrequent Access (IA)**, I chose `None`. For **Transition into Archive**, I also chose `None`. For **Throughput mode**, I chose `Bursting`.

![Screenshot (5668)](https://github.com/user-attachments/assets/0fe443dc-26d9-47b5-9ba2-6fa8b1f8ca84)
![Screenshot (5669)](https://github.com/user-attachments/assets/ca6a439f-4d99-4a98-a9b8-e4f457946607)
*Configuring EFS lifecycle management and throughput mode.*

---

### 14. Configuring Network Access (Mount Targets)

* In the **Network access** step, under **Mount targets**, I removed the subnets for AZ `us-east-1c` and `us-east-1b`. For AZ `us-east-1a`, under **Security groups**, I removed the existing security group and then chose the `PetModels-EFS-1-SG` security group that I had previously created. I then clicked **Next**.

![Screenshot (5670)](https://github.com/user-attachments/assets/00f86bad-8737-4197-a150-bc3a4f4f5348)
*Configuring EFS mount targets and assigning the custom security group for network access.*

---

### 15. Reviewing File System Policy

* In the **File system policy** step, I clicked **Next**.

![Screenshot (5671)](https://github.com/user-attachments/assets/47367702-21c9-4ddb-bc94-7645ea7a70ce)
*Reviewing the EFS file system policy before creation.*

---

### 16. Creating the File System

* In the **Review and create** step, I clicked **Create** at the bottom of the page. I confirmed that the file system was available and reviewed its ID.

![Screenshot (5672)](https://github.com/user-attachments/assets/b6caea07-0883-4cbe-9b82-c59fb78ccf60)

![Screenshot (5675)](https://github.com/user-attachments/assets/74208034-ecbe-4bdc-8f36-289d8b7a79ca)
*Final step to create the EFS file system and confirming its availability.*

---

### 17. Attaching the EFS File System

* I clicked **Attach** on the EFS file system details page.

![Screenshot (5676)](https://github.com/user-attachments/assets/80d0d1c3-9c36-4c75-b3e6-1c0e2697221f)
*Locating the 'Attach' option for the newly created EFS file system.*

---

### 18. Copying the Mount Command

* In the pop-up box, I kept the default choice of **Mount via DNS**. Under **Using the EFS mount helper**, I copied the mount command provided, which would be used in later steps to mount the EFS file system to the EC2 instances. I then clicked **Close**.

![Screenshot (5680)](https://github.com/user-attachments/assets/b7ef7c2c-6bcf-4d72-874d-da6dca9452f2)
*Copying the EFS mount helper command for EC2 instances.*

---

### 19. Navigating Back to EC2 and Connecting to WebServer1 via Session Manager

* I navigated back to the Amazon EC2 console. 

![Screenshot (5681)](https://github.com/user-attachments/assets/6d589f48-6046-4062-8b96-ddcae0425afa)

![Screenshot (5682)](https://github.com/user-attachments/assets/70779ad2-2e0b-4cfb-a571-83c4a9a612b0)

![Screenshot (5683)](https://github.com/user-attachments/assets/6c3435a7-a93f-43ab-b999-6633aeeda988)

* I created a log file (efs-1-setup.log) on the first instance (WebServer1) and added some content, **efs-1 mounted in site A**.

![Screenshot (5684)](https://github.com/user-attachments/assets/fec544b7-d856-4a15-8358-f5d176eca6f8)
![Screenshot (5685)](https://github.com/user-attachments/assets/986c24ad-fefe-442a-a498-e8aba7da4740)
*Returning to the EC2 console to proceed with instance connection and file sharing.*

---

### 20. Repeated all the above steps for WebServer2

* After successfully mounting the EFS file system to both EC2 instances (WebServer1 and WebServer2), I proceeded to confirm shared access. 
* I connected to WebServer2 and not only confirmed the presence of efs-1-setup.log but also appended the entry **efs-1 mounted in site B** to the same log file. 
* The ability to seamlessly view and modify content originating from both WebServer1 and WebServer2 within the same log file served as conclusive evidence that the EFS file system was successfully shared and mutually accessible.

![Screenshot (5695)](https://github.com/user-attachments/assets/6f7629c0-e807-4279-bcba-6dd7991863ac)

![Screenshot (5696)](https://github.com/user-attachments/assets/ab20e360-a8ac-4da2-aa4a-4cdf55055dc3)

![Screenshot (5697)](https://github.com/user-attachments/assets/e4a08158-df42-4fc4-a34f-8e532fbe1370)
![Screenshot (5698)](https://github.com/user-attachments/assets/15d9d24a-69a4-4826-8d20-2903ca69db77)
*Confirming shared file access by viewing content created on one instance from another.*

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
