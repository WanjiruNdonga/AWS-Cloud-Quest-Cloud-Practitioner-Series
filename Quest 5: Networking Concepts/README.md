---

# Quest 5: Networking Concepts - Building My Cloud Network! 🌐🔒

After conquering the **Cloud Economics** quest and understanding the financial side of cloud operations, this repo chronicles my journey through **Networking Concepts**, a crucial practice lab in the AWS Cloud Quest series. This was all about diving into the backbone of cloud operations – building, securing, and understanding networks within AWS! Think of it as my first foray into becoming a true network architect in the cloud. 🏗️

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

This practice lab focused on getting hands-on with fundamental networking concepts and services in AWS.

The key objectives for this mission included:
* Explore the components of a Virtual Private Cloud (VPC).
* Configure a route table attached to your VPC.
* Configure a route table to direct Internet-bound traffic to the Internet Gateway.
* Review public and private IPv4 addresses.
* Review security group rules for inbound traffic.
* Test connectivity using a Java application.

---

## 🛠️ AWS Services I Conquered: My Network Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS networking services:

* **Amazon VPC (Virtual Private Cloud):** This allowed me to create my own isolated virtual network within the AWS Cloud, giving me complete control over my network environment.
* **Internet Gateway (IGW):** I attached this to my VPC to enable communication between my VPC and the internet, serving as a target for Internet-routable traffic.
* **Route Tables:** These defined rules for network traffic, determining where network traffic from my subnets and gateways is directed.
* **Subnets:** I used these to segment my VPC into logical sections where resources could be placed, each associated with an Availability Zone.
* **Security Groups:** These acted as virtual firewalls, controlling inbound and outbound traffic to instances, allowing me to specify allowed protocols and port ranges.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

Navigating the AWS Console for networking felt like drawing up blueprints for a new digital city! Every configuration was a foundational block for secure and functional communication.

Here's a peek at how it all went down:

---

### 1. Initial Setup and Instances Overview:

* My mission began with grasping the concept of a VPC – a logically isolated section of the AWS Cloud. I then proceeded to set up my very own, defining its IP address range. This was the first layer of isolation!

![Screenshot (3914)](https://github.com/user-attachments/assets/6e41e5f6-277d-40f8-8d12-7378a9bed189)

![Screenshot (3915)](https://github.com/user-attachments/assets/68f62572-798a-4a16-9ec4-4dfa69a64786)
*Initial view of my EC2 instances, noting their public and private IP addresses.*

---

### 2. Testing Initial Connectivity (and the expected failure!):

* I reviewed the Public and Private IPv4 addresses associated with the "Web Server" instance.
* Before any network configurations, I attempted to access the Web Server instance using its Public IP address in a new browser tab. As expected, this resulted in a "This site can't be reached" message, demonstrating the initial lack of internet connectivity to my VPC. This was a crucial step to highlight the need for proper networking setup.

![Screenshot (3916)](https://github.com/user-attachments/assets/007ffebd-ae36-4470-ae34-f4f928f7f363)

![Screenshot (3917)](https://github.com/user-attachments/assets/1708b808-5b53-430c-b5e6-9f287e514cb1)
*Confirming that my Web Server instance is not yet accessible from the internet.*

---

### 3. Subnet Exploration and Route Table Association:

* I delved into the details of the subnet associated with my "Web Server" instance by clicking on its Subnet ID. This helped me understand how my VPC is segmented.
* Next, I selected the "network-concepts" subnet and clicked on the "Route table" tab to examine its associated route table.

![Screenshot (3918)](https://github.com/user-attachments/assets/3ad36a3a-344e-43bc-a4f0-22cdb6fff7c2)

![Screenshot (3919)](https://github.com/user-attachments/assets/51576ab0-fae4-4027-842f-7a236a715ff1)
*Exploring the subnet details and its associated route table to understand traffic flow.*

---

### 4. Understanding and Modifying Route Table Entries:

* I reviewed the existing route table entries, noting that one route sent local traffic within the network, and another sent all other traffic through a NAT gateway.
* The lab required removing the NAT gateway route to prepare for direct internet access.
* Then, I added a new route to direct all Internet-bound traffic (`0.0.0.0/0`) to the Internet Gateway, making the subnet reachable from the internet.

![Screenshot (3920)](https://github.com/user-attachments/assets/eaec9104-a651-4b7d-b872-4569e4119535)

![Screenshot (3921)](https://github.com/user-attachments/assets/32b54984-0d54-45c8-abd7-cc1e8f72403e)

![Screenshot (3922)](https://github.com/user-attachments/assets/a7718923-fe6d-47d4-aa07-daf33eb432b4)

![Screenshot (3923)](https://github.com/user-attachments/assets/6cf9c183-8717-4e28-a4a9-dd9f35ff58cb)
*Configuring my route table to enable internet connectivity for my public subnet.*

---

### 5. Deep Dive into Security Groups:

* I navigated to the Security tab of my "Web Server" instance and then clicked on "WebServerSecurityGroup" to inspect its rules.
* I edited the inbound rules, adding a new rule for `HTTP` traffic from `Anywhere-IPv4`. This was a critical step for allowing web access to the server.

![Screenshot (3925)](https://github.com/user-attachments/assets/60b12322-e3ac-420f-ba24-6c429a9702b6)

![Screenshot (3926)](https://github.com/user-attachments/assets/4c379d02-b4fd-45b1-a442-f9988a12e2f4)

![Screenshot (3927)](https://github.com/user-attachments/assets/36e1411d-ca67-4b64-9eb1-9cc50a14ce36)

![Screenshot (3928)](https://github.com/user-attachments/assets/d73306f2-ab88-4a7c-a827-de5a2fc8ac10)

![Screenshot (3929)](https://github.com/user-attachments/assets/de91ec95-9dde-4e7e-9bd3-91b0cfaafc0a)
*Defining inbound rules for my Security Group to allow HTTP traffic.*

* I also edited the inbound rules, adding a new rule for `MySQL/Aurora` traffic from `WebServerSG`. This was a critical step for allowing database access from the web server.

![Screenshot (3951)](https://github.com/user-attachments/assets/14cf44c2-7f59-453d-b8f8-49b058a41c99)
*Database Server should not be accessible from the Internet.*

![Screenshot (3952)](https://github.com/user-attachments/assets/32872a18-2219-40ed-8c26-9250564ea58a)

![Screenshot (3953)](https://github.com/user-attachments/assets/fa96d86a-80e0-43fd-9dae-273465e73a90)

![Screenshot (3954)](https://github.com/user-attachments/assets/20d078db-7f5b-4b9e-87b3-cbc9a93793fa)

![Screenshot (3956)](https://github.com/user-attachments/assets/853b0843-cb46-4f7d-b0a6-6bf2d2e44a47)
![Screenshot (3957)](https://github.com/user-attachments/assets/47590cc1-e0a8-4a6c-b6b2-8df5fde2281f)

![Screenshot (3958)](https://github.com/user-attachments/assets/fa877ea6-bdbb-4188-b97c-80f13bafa397)
*Database Server accessible from the Web Servert.*

---

### 6. Final Connectivity Test:

* With the Internet Gateway configured and security group rules updated, I again opened a new browser tab and pasted the instance's Public IP address (using HTTP, not HTTPS). This time, the Java application loaded successfully, confirming that the Web Server was now accessible from the internet and the Database Server accessible from the Web Server.

![Screenshot (3959)](https://github.com/user-attachments/assets/40e2d338-9e8f-4889-b7f0-a76b7a4636d4)
*Verifying successful connectivity to my Web Server instance from the internet!*

---

## 🔑 Key Takeaways & Networking Revelations: 🔑

This lab was my deep dive into the foundational networking concepts that underpin all cloud architectures.

* **VPC is the Foundation:** A well-designed VPC is the bedrock of a secure and scalable cloud environment, providing logical isolation and control over your network.
* **Routing is Critical:** Understanding how traffic flows through subnets, route tables, and internet gateways is essential for both internal and external connectivity.
* **Security is Layered:** Network security isn't a single point; it's a combination of VPCs, subnets, and especially Security Groups that act as virtual firewalls to protect your resources.
* **Hands-on Builds Confidence:** Directly configuring these services significantly solidified my theoretical understanding of networking concepts. The initial connectivity failure and subsequent resolution highlighted the importance of each networking component.

---

## ✨ What's Next on My Cloud Quest: ✨

With a solid grasp of networking fundamentals, I'm ready to build even more complex and secure cloud infrastructures. My journey towards becoming a Cloud Security Specialist is all about mastering these core components, and networking is undeniably a critical piece of the puzzle.

---

## 🤝 Let’s Connect!

Curious about cloud networking, security, or just want to chat about building robust cloud foundations? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---
✨ Securing the cloud and serving vibes! 🥂💅☁️✨

---
