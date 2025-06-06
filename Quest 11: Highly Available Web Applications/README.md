---

# Quest 11: Highly Available Web Applications Lab - Resilient & Scalable Architectures 🌐 🚀

This project details my experience with the **Highly Available Web Applications** lab, focusing on deploying and managing applications designed for high availability and scalability in the cloud using AWS. This lab emphasizes configuring AWS services to distribute traffic, ensure application health, and automatically adjust capacity across multiple Availability Zones for enhanced resilience.

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

The core goals achieved in this practice lab included:
* Configuring an Auto Scaling group to use an Application Load Balancer. 
* Configuring load balancer health checks for the Auto Scaling group. 
* Adding additional Availability Zones to the Auto Scaling group for increased redundancy. 

---

## 🛠️ AWS Services I Conquered: My HA Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS services:
* **Amazon EC2 (Elastic Compute Cloud):** Provided the foundational compute instances for the web application.
* **Amazon EC2 Auto Scaling:** Managed the automatic scaling and healing of EC2 instances to meet demand.
* **Application Load Balancer (ALB):** Distributed incoming web traffic across multiple EC2 instances, ensuring high availability.
* **Amazon CloudWatch:** Used indirectly for health checks and monitoring instance status within the Auto Scaling ecosystem.
* **Amazon VPC (Virtual Private Cloud):** Provided the isolated network environment, including subnets and security groups.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

This section outlines the key steps undertaken to achieve the lab objectives, building a robust and highly available application environment:

---

### 1. Initial Auto Scaling Group Overview

I began by inspecting the pre-configured `TravelAgencyWebServers` Auto Scaling Group in the AWS Management Console to understand its current state and instance configuration. 

![ASG Initial Overview](images/highly_available_lab_01_asg_overview.png)
*Initial view of the TravelAgencyWebServers Auto Scaling Group.*

---

### 2. Reviewing Instance and Network Configuration

I reviewed the single running instance within the Auto Scaling group and observed that the ASG was initially configured to operate within a single subnet and Availability Zone.  This highlighted the need for multi-AZ expansion.

![Single Instance and AZ Review](images/highly_available_lab_02_instance_az_review.png)
*Reviewing the current instance count and single Availability Zone configuration.*

---

### 3. Attaching an Application Load Balancer (ALB)

To distribute traffic and enhance availability, I attached a new Application Load Balancer to the Auto Scaling Group:
* I navigated to the Load Balancing section and initiated the creation of a new load balancer. 
* I selected **Application Load Balancer** as the type and configured it as **Internet-facing** for public access. 
* For high availability, I selected all available **three Availability Zones** and their corresponding public subnets. 
* I created a new target group (accepting default routing settings) to register the EC2 instances, and then completed the ALB creation. 

![ALB Attachment](images/highly_available_lab_03_alb_attachment.png)
*Configuring the Application Load Balancer with type, scheme, Availability Zones, and target group settings.*

---

### 4. Configuring ALB Security Group

To control traffic flow to the ALB, I created a new security group:
* I navigated to **Security Groups** and clicked "Create security group." 
* I named it `TravelAgencyLoadBalancer` and added an **inbound rule** to allow HTTP traffic from `0.0.0.0/0` (anywhere). 
* For **outbound rules**, I configured it to allow HTTP traffic only to the `TravelAgencyWebServers` security group, ensuring secure communication between the ALB and the web servers. 
* This new security group was then associated with the ALB.

![ALB Security Group Configuration](images/highly_available_lab_04_alb_sg_config.png)
*Defining inbound and outbound rules for the Application Load Balancer's security group.*

---

### 5. Validating Application Connectivity via ALB

After the ALB was provisioned, I obtained its DNS name and accessed it in a web browser to confirm that the web application was successfully serving content through the load balancer. 

![ALB Connectivity Test](images/highly_available_lab_05_alb_test.png)
*Verifying web application accessibility through the Application Load Balancer's DNS name.*

---

### 6. Testing and Customizing Load Balancer Health Checks

I validated the default health check by appending `/health` to the ALB DNS name and confirming the instance was reported as healthy. 
To customize the health check for more accurate application monitoring, I modified the target group's health check settings, for example, by ensuring the path was correctly set to `/health`. 

![Health Check Validation and Customization](images/highly_available_lab_06_health_check.png)
*Confirming default health check functionality and modifying health check settings for the target group.*

---

### 7. Expanding Auto Scaling Group to Multiple Availability Zones

To enhance fault tolerance and geographic redundancy, I updated the Auto Scaling Group to span multiple Availability Zones:
* I returned to the Auto Scaling Group settings.
* In the Network section, I added a new Availability Zone to the existing configuration, specifically targeting a third AZ as per DIY goals. 

![Multi-AZ Expansion](images/highly_available_lab_07_multi_az_expansion.png)
*Configuring the Auto Scaling Group to operate across multiple Availability Zones for improved resilience.*

---

### 8. Scaling Up and Verifying New Instances

To observe the scaling in action and confirm the multi-AZ setup, I manually increased the `Desired capacity` of the Auto Scaling Group to `2`, also setting the `Max desired capacity` to `2`. 
I then reviewed the Auto Scaling group's activity history and confirmed that a new EC2 instance was launched in the newly added Availability Zone and reported as healthy by the load balancer. 

![Scaling Up and Verification](images/highly_available_lab_08_scale_verify.png)
*Manually increasing desired capacity and verifying the launch and health of new instances across AZs.*

---

## 🔑 Key Learnings & HA Revelations: 🔑

This lab provided critical insights into building highly available and fault-tolerant web applications:

* **Traffic Distribution with ALB:** Gained hands-on experience in using Application Load Balancers to efficiently distribute incoming web traffic, preventing single points of failure.
* **Enhanced Application Resilience:** Deepened my understanding of how combining Auto Scaling Groups with ALBs across multiple Availability Zones significantly enhances application resilience and fault tolerance, making applications robust against individual instance or AZ failures.
* **Proactive Health Monitoring:** Learned the importance of configuring comprehensive health checks on load balancers and target groups to ensure only healthy instances receive traffic.
* **Seamless Scaling:** Observed how Auto Scaling Groups automatically launch and register new instances with the load balancer when capacity needs increase, maintaining application performance.

---

## ✨ What's Next on My Cloud Quest: ✨

Mastering highly available web applications is crucial for any cloud professional. This lab has provided a strong foundation. I'm now eager to explore more advanced ALB features like content-based routing, integrating with AWS WAF for enhanced security, and diving deeper into blue/green deployments and other sophisticated deployment strategies for zero-downtime updates.

---

## 🤝 Let’s Connect!

Curious about highly available architectures, load balancing, or just want to chat about building robust cloud applications? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---

✨ Building resilient clouds, one highly available app at a time! 🛡️☁️🌐✨

---
