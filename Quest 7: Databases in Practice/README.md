---

# Quest 7: Databases in Practice Lab - My Data-Driven Cloud Journey! 📊🗄️💾

Building on my journey through **Cloud Economics**, **Networking Concepts**, and **Connecting VPCs**, this repo details the **Databases in Practice** lab within the AWS Cloud Quest series. This mission was all about diving deep into AWS's robust database offerings, understanding how to provision, manage, and interact with various database services to power applications. It's like becoming a master librarian for cloud data! 📚

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

This practice lab focused on gaining hands-on experience with AWS database services and understanding their practical applications.

The key objectives for this mission included:
* Learn about AWS database offerings.
* Provision and configure an Amazon RDS instance.
* Connect to a database instance.
* Perform basic database operations (e.g., creating tables, inserting data, querying data).

---

## 🛠️ AWS Services I Conquered: My Database Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS database and related services:

* **Amazon RDS (Relational Database Service):** Used to set up, operate, and scale relational databases in the cloud, automating time-consuming administration tasks.
* **Amazon EC2 (Elastic Compute Cloud):** Explored briefly as a service for secure and scalable computing capacity in the AWS Cloud.
* **MariaDB:** Chosen as the database engine for the RDS instance.
* **Security Groups:** Crucial for configuring network access and securing the database instance.
* **Amazon DynamoDB (briefly explored):** Learned about it as a non-relational, schema-less storage option.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

Working with databases in AWS felt like building and managing a highly organized digital vault! Each step was about ensuring data integrity, accessibility, and security.

Here's a peek at how it all went down:

---

### 1. Reviewing Lab Objectives and Starting the Lab

Began by reviewing the practice lab objectives in the Concept section and then starting the lab. AWS services not used in this lab were disabled, and the capabilities of the services used were limited to what the lab required.

---

### 2. Exploring EC2 (Initial Search)

I performed a search for "ec2" in the top navigation bar, reviewing the search results under Services.

![Screenshot (4008)](https://github.com/user-attachments/assets/01154edf-2974-4ff6-a862-dea06c31021f)
*Searching for EC2 in the AWS console, showing various related services.*

---

### 3. Reviewing AMI Catalog

Next, I navigated to the AMI Catalog to understand Amazon Machine Images. An AMI is a template containing the software configuration needed to launch an instance.

![Screenshot (4010)](https://github.com/user-attachments/assets/fd99bad9-7ccd-467a-aef9-f831b3a11b05)
*The AMI Catalog, displaying various Amazon Machine Images available for instance launches.*

---

### 4. Searching for SQL AMIs

I then searched for "sql" within the AMI search box to find available AMIs on Amazon EC2 that support SQL Server, reviewing the filtered results.

![Screenshot (4011)](https://github.com/user-attachments/assets/20add09e-8b1f-459e-90aa-8f7a9a11430b)
*Search results for "sql" in the AMI Catalog, showing different SQL Server options.*

---

### 5. Searching for Database Services

To proceed with database practice, I searched for "database" in the console, which showed results for various database services like Oracle Database@AWS, Database Migration Service, DynamoDB, and RDS.

![Screenshot (4012)](https://github.com/user-attachments/assets/6b96967e-d176-4dc6-a133-e537a7279a27)
*Search results in the AWS console for "database," highlighting different AWS database services.*

---

### 6. Reviewing Database Options and Selecting RDS

I reviewed the comprehensive portfolio of database services offered by AWS, such as Amazon RDS for relational databases and Amazon DynamoDB for non-relational storage. I then clicked on **RDS** to proceed with setting up a relational database.

![Screenshot (4013)](https://github.com/user-attachments/assets/96184777-8242-46ed-8838-00e16117d06d)
*List of available database services, with Amazon RDS highlighted for selection.*

---

### 7. Navigating to Create Database

After selecting RDS, I navigated to the Databases section and clicked on **Create database** to begin the provisioning process.

![Screenshot (4014)](https://github.com/user-attachments/assets/d743fd16-afad-4938-b9d3-52e363cd9a76)
*The Amazon RDS dashboard, showing the option to "Create database".*

---

### 8. Choosing Database Creation Method and Engine

I chose the **Standard create** method for database creation. For the engine type, I selected **MariaDB**, reviewing its description and features, including its strong support from the open-source community.

![Screenshot (4015)](https://github.com/user-attachments/assets/3ef36141-0680-4ae8-8fd7-99f78755bd10)
*Selecting "Standard create" and "MariaDB" as the database engine for the new instance.*

---

### 9. Configuring Engine Version and Instance Identifier

I kept the default MariaDB engine version and chose **Dev/Test** for the template. 

![Screenshot (4016)](https://github.com/user-attachments/assets/e6ffd8a4-7eda-4e35-b92d-5fd5ae72c6d7)
*Configuring the database engine version and setting the DB instance identifier to 'my-database'.*

---

### 10. Setting Credentials

For the DB instance identifier, I typed `my-database`.
Under credential settings, I kept the default master username `admin` and chose **Self managed** for credentials management. I then typed `ILoveLearning123` for both the master password and its confirmation.

![Screenshot (4017)](https://github.com/user-attachments/assets/c3b84bcf-d4ab-4d3e-bb37-6663e354b3f4)
*Entering the master username and password for the database instance.*

---

### 11. Configuring Instance Class and Storage

In the instance configuration, I selected **Burstable classes** for the DB instance class and specifically chose `db.t3.xlarge`. For storage type, I opted for **General Purpose SSD (gp3)** and set the allocated storage to 20 GB.

![Screenshot (4018)](https://github.com/user-attachments/assets/3759e74d-41ca-4d54-bd81-8d46c75371fc)
*Defining the DB instance class (db.t3.xlarge) and storage type (gp3) with allocated storage.*

---

### 12. Additional Storage Configuration and Multi-AZ Deployment

I confirmed that **Enable storage autoscaling** was selected, with a maximum storage threshold of 1000 GiB. For Multi-AZ deployment, I chose **Create a standby instance** for increased availability and redundancy.

![Screenshot (4019)](https://github.com/user-attachments/assets/5270723d-e17c-43a8-85b3-878ab35426e9)
*Configuring storage autoscaling and opting for a Multi-AZ deployment with a standby instance.*

---

### 13. Networking and Security Configuration

I selected the `default` VPC, confirmed the subnet group, and set Public access to **No**. For VPC security groups, I used the **Choose existing** option and selected the `default` security group, ensuring its inbound rule was configured appropriately for connections.

![Screenshot (4020)](https://github.com/user-attachments/assets/2c3bd431-2bef-44ae-8074-c0c2f0977547)
![Screenshot (4021)](https://github.com/user-attachments/assets/5a29caf5-b4d0-42a5-a14b-25a0de5b516c)
*Configuring network settings, including VPC, subnet group, public access, and an existing security group.*

---

### 14. Additional Configuration (Database Port and Backup Retention)

I kept the default database port for MariaDB (3306). For backup retention period, I selected **7 days**. This ensures that automated backups are enabled and retained for seven days.

![Screenshot (4040)](https://github.com/user-attachments/assets/d5dc56b7-0c5e-4894-bf22-a57f2e593a17)
![Screenshot (4023)](https://github.com/user-attachments/assets/6e7bd418-a37b-4c81-9f7d-d7a6febd52c9)
*Setting the database port and configuring the backup retention period to 1 day.*

---

### 15. Monitoring, Logging, and Maintenance Configuration

Under **Monitoring**, I selected **Database Insights - Standard**. For **Maintenance**, I set the auto minor version upgrade to **Disable**.

![Screenshot (4022)](https://github.com/user-attachments/assets/46cb3372-8e6c-4fb0-aec6-649ae15b4892)
*Configuring 'Database Insights - Standard' monitoring*

![Screenshot (4025)](https://github.com/user-attachments/assets/cfa31187-3c62-4bd7-a159-c50ba53ca2ec)
*Disabling auto minor version upgrades.*

---

### 16. Reviewing Estimated Monthly Costs

Before creating the database, I reviewed the estimated monthly costs based on the configurations chosen, confirming the understanding of the financial implications.

![Screenshot (4026)](https://github.com/user-attachments/assets/8ce32608-3b3d-4104-a013-9671ba338656)
*Reviewing the estimated monthly costs for the configured RDS instance.*

After reviewing all configurations and estimated costs, I clicked **Create database**. This initiated the provisioning process for the MariaDB instance.

![Screenshot (4028)](https://github.com/user-attachments/assets/7016d274-89d5-4a82-9a54-b36395de6173)

---

### 17. Database Creation

I monitored the database instance status in the RDS dashboard. Initially, it showed as `Creating`, then transitioned to `Backing up`, and finally to `Available` once fully provisioned and ready for use.

![Screenshot (4030)](https://github.com/user-attachments/assets/61b699fe-efb4-44a0-b17a-a20ffd864815)
*Observing the 'my-database' instance status as it transitions from 'Creating' to 'Available'.*

---

## 🔑 Key Takeaways & Database Revelations: 🔑

This lab was an immersive experience into the world of cloud databases, highlighting their power and ease of management.

* **Managed Services Power:** AWS managed database services significantly simplify database administration, allowing me to focus more on application development rather than infrastructure.
* **Scalability & Durability:** Realized how easily databases can be scaled up or down and how AWS handles underlying durability and availability.
* **Security by Design:** The importance of properly configuring security groups and network access for databases cannot be overstated to protect sensitive data.
* **Choosing the Right Database:** Gained a better understanding of the different database types offered by AWS (relational like RDS, non-relational like DynamoDB) and the scenarios where each excels.
* **Lifecycle Management:** Learned the complete lifecycle of a database instance, from provisioning and connecting to snapshotting and deletion.

---

## ✨ What's Next on My Cloud Quest: ✨

Mastering database concepts is fundamental to building any robust cloud application. This lab has significantly enhanced my ability to handle data in the cloud, and I'm excited to apply this knowledge to future projects involving more complex data architectures and application development. My journey towards becoming a Cloud Security Specialist is deeply intertwined with understanding how to secure and manage data effectively.

---

## 🤝 Let’s Connect!

Curious about cloud databases, security, or just want to chat about making your data journey smooth and secure? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---

✨ Securing the cloud and serving vibes! 🥂💅☁️✨

---
