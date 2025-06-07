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

![Screenshot (7323)](https://github.com/user-attachments/assets/d139190a-cd28-4710-adb6-5e650d3192bb)

![Screenshot (7324)](https://github.com/user-attachments/assets/50242f03-88a0-4f30-8c3d-5668d0ad6f40)

![Screenshot (7325)](https://github.com/user-attachments/assets/264998a3-44ba-4e40-9f59-b56197eb8654)
*Initial view of the TravelAgencyWebServers Auto Scaling Group.*

---

### 2. Reviewing Instance and Network Configuration

I reviewed the single running instance within the Auto Scaling group and observed that the ASG was initially configured to operate within a single subnet and Availability Zone.  This highlighted the need for multi-AZ expansion.

![Screenshot (7326)](https://github.com/user-attachments/assets/11e5a756-67f5-4b54-96c9-94752bfb6570)

![Screenshot (7327)](https://github.com/user-attachments/assets/3a18c870-65fe-44fe-a73d-7b031b2d43b7)
*Reviewing the current instance count and single Availability Zone configuration.*

---

### 3. Attaching an Application Load Balancer (ALB)

To distribute traffic and enhance availability, I attached a new Application Load Balancer to the Auto Scaling Group:
* I navigated to the Load Balancing section and initiated the creation of a new load balancer.

  ![Screenshot (7328)](https://github.com/user-attachments/assets/127cce3c-ab16-42d7-a0d7-d9de0065b6bb)
  
  ![Screenshot (7329)](https://github.com/user-attachments/assets/e0ed43b2-2dba-4901-a4ba-5622e8dd6f43)
  
* I selected **Application Load Balancer** as the type and configured it as **Internet-facing** for public access.

  ![Screenshot (7330)](https://github.com/user-attachments/assets/d77ce44b-5ba6-4954-97a7-c23d60b82854)

* For high availability, I selected all available **three Availability Zones** and their corresponding public subnets.

  ![Screenshot (7331)](https://github.com/user-attachments/assets/89b2cced-e2e3-4d8a-bf05-74776a2c3920)

* I created a new target group (accepting default routing settings) to register the EC2 instances, and then completed the ALB creation. 

  ![Screenshot (7333)](https://github.com/user-attachments/assets/1e5a3ee3-8c7b-48f2-a23b-5d3c34fe4b78)

  ![Screenshot (7334)](https://github.com/user-attachments/assets/faeb3bf3-cda3-4ca1-a009-d741c15f4413)
  *Configuring the Application Load Balancer with type, scheme, Availability Zones, and target group settings.*

---

### 4. Configuring ALB Security Group

To control traffic flow to the ALB, I created a new security group:
* I navigated to **Security Groups** and clicked "Create security group."

  ![Screenshot (7335)](https://github.com/user-attachments/assets/60875b76-98f8-49ba-b484-beecd237df9d)

* I named it `TravelAgencyLoadBalancer` and added an **inbound rule** to allow HTTP traffic from `0.0.0.0/0` (anywhere).

  ![Screenshot (7336)](https://github.com/user-attachments/assets/8f89b634-4ddb-46a4-8e9b-34a633f35bed)
  ![Screenshot (7337)](https://github.com/user-attachments/assets/024b4b42-3214-47b9-9809-fdeba771c1be)

* For **outbound rules**, I configured it to allow HTTP traffic only to the `TravelAgencyWebServers` security group, ensuring secure communication between the ALB and the web servers.

  ![Screenshot (7338)](https://github.com/user-attachments/assets/d33e17a1-05a3-485d-91c2-84da0de6cedf)
  *Defining inbound and outbound rules for the Application Load Balancer's security group.*
  
* This new security group was then associated with the ALB.

* I also ensured the TravelAgencyWebServers security group (attached to the EC2 instances) had an inbound rule explicitly allowing HTTP traffic originating from the TravelAgencyLoadBalancer security group. This step ensures the web servers only accept requests from the load balancer, enhancing security.

  ![Screenshot (7339)](https://github.com/user-attachments/assets/3977d856-32d2-4aef-a81e-07bb3470b8e9)

  ![Screenshot (7340)](https://github.com/user-attachments/assets/7efdb951-f8b6-43e8-ad7a-9b6c94b1b21d)

  ![Screenshot (7341)](https://github.com/user-attachments/assets/f06b4fb9-236e-4f1a-8c45-2d8b827fd3b7)

  ![Screenshot (7342)](https://github.com/user-attachments/assets/f65ee87d-e8a3-4a90-b5f2-b19ce2a2fc25)

---

### 5. Validating Application Connectivity via ALB

After the ALB was provisioned, I obtained its DNS name and accessed it in a web browser to confirm that the web application was successfully serving content through the load balancer. 

![Screenshot (7347)](https://github.com/user-attachments/assets/a22281a3-8789-48dc-866f-d65d845df1a2)

![Screenshot (7348)](https://github.com/user-attachments/assets/10563e8a-72b9-4ead-a460-8c92d0b9e1e2)
*Verifying web application accessibility through the Application Load Balancer's DNS name.*

---

### 6. Testing and Customizing Load Balancer Health Checks

I validated the default health check by appending `/health` to the ALB DNS name and confirming the instance was reported as healthy. 
To customize the health check for more accurate application monitoring, I modified the target group's health check settings, for example, by ensuring the path was correctly set to `/health`. 

![Screenshot (7350)](https://github.com/user-attachments/assets/8ff8ac97-5117-40ff-85d1-5557d323fc53)
![Screenshot (7351)](https://github.com/user-attachments/assets/f8888b89-773d-4191-9cae-732e2b181518)

![Screenshot (7352)](https://github.com/user-attachments/assets/f2deb22f-5b68-4023-b4e0-c7e5555f3ba3)
![Screenshot (7353)](https://github.com/user-attachments/assets/5050e3ac-a2d8-4810-bd5f-4c3b4413b0ee)

![Screenshot (7349)](https://github.com/user-attachments/assets/47b37a7e-25c9-4fbd-aa6a-6e0bc8a4e0ac)
*Confirming default health check functionality and modifying health check settings for the target group.*

---

### 7. Expanding Auto Scaling Group to Multiple Availability Zones

To enhance fault tolerance and geographic redundancy, I updated the Auto Scaling Group to span multiple Availability Zones:
* I returned to the Auto Scaling Group settings.

  ![Screenshot (7355)](https://github.com/user-attachments/assets/b37b0851-d675-44bd-8a19-b516a2db878b)

* In the Network section, I added 2 new Availability Zones to the existing configuration. 

  ![Screenshot (7356)](https://github.com/user-attachments/assets/b198140e-ec84-46e4-b1c4-50a9ae7a0640)

  ![Screenshot (7357)](https://github.com/user-attachments/assets/5e69950f-c884-4350-936e-6dd70998e76a)

  ![Screenshot (7358)](https://github.com/user-attachments/assets/5f03c398-4dca-4f4d-9689-f885b6cf3e25)
  *Configuring the Auto Scaling Group to operate across multiple Availability Zones for improved resilience.*

---

### 8. Scaling Up and Verifying New Instances

To observe the scaling in action and confirm the multi-AZ setup, I manually set the `Desired capacity` of the Auto Scaling Group to `3`, also setting the `Max desired capacity` to `3`. 

![Screenshot (7369)](https://github.com/user-attachments/assets/86c9ba47-17ae-4ffe-8bd9-6729793a6da6)

![Screenshot (7370)](https://github.com/user-attachments/assets/67e3a2ee-790d-4da3-aa63-b1b9acc28aad)
*Manually increasing desired capacity.*

I then reviewed the Auto Scaling group's activity history and confirmed that 3 new EC2 instance were launched in the newly added Availability Zones and reported as healthy by the load balancer. 
* Before Scaling, there was only 1 EC2 Instance:

  ![Screenshot (7361)](https://github.com/user-attachments/assets/14a64157-4678-4a9d-9169-7bcec2a3f604)

* After Scaling, the number of EC2 Instances increased to 3 as I had set:

  ![Screenshot (7372)](https://github.com/user-attachments/assets/1f1a3b5e-3246-46fe-89ac-a44a1807c49f)

  ![Screenshot (7373)](https://github.com/user-attachments/assets/41a9b044-4d76-4e91-a2fa-5d97090893df)

* Verified the launch and health of new instances across AZs:

  ![Screenshot (7371)](https://github.com/user-attachments/assets/1378a7c6-171b-4f1b-99b5-cfe224aaa97d)

  ![Screenshot (7376)](https://github.com/user-attachments/assets/9b29294a-3298-416f-8a3d-be0876dee14f)

  ![Screenshot (7375)](https://github.com/user-attachments/assets/49066bd9-a500-454a-93ce-33cd49f35a33)

  ![Screenshot (7374)](https://github.com/user-attachments/assets/33e1712c-15e7-4afe-bd53-80b07145b231)

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
