---

# Quest 6: Connecting VPCs Lab - Bridging My Cloud Networks! 🔗☁️

Building on my journey through **Cloud Economics** and **Networking Concepts**, this repo details the **Connecting VPCs** lab within the AWS Cloud Quest series. This mission focused on securely connecting isolated virtual networks (VPCs) to enable seamless communication between different parts of my cloud infrastructure. It's like building high-speed bridges between distinct digital cities! 🌉

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

This practice lab focused on establishing secure and efficient communication pathways between independent Virtual Private Clouds (VPCs).

The key objectives for this mission included:
* Understand VPC peering connections.
* Create a VPC peering connection.
* Accept a VPC peering connection.
* Configure route tables to enable traffic flow between peered VPCs.
* Review security group rules for inbound and outbound traffic.
* Test connectivity between instances in different VPCs.

---

## 🛠️ AWS Services I Conquered: My Network Interconnect Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS networking services to establish cross-VPC communication:

* **Amazon VPC (Virtual Private Cloud):** The fundamental service for creating isolated virtual networks where my resources reside.
* **VPC Peering:** This enabled me to create a networking connection between two VPCs, allowing instances in either VPC to communicate using private IPv4 addresses as if they are in the same network.
* **Route Tables:** Crucial for defining the rules that dictate where network traffic is directed, ensuring traffic between peered VPCs flowed correctly.
* **EC2 (Elastic Compute Cloud):** For launching and managing the virtual servers (instances) within each VPC that needed to communicate.
* **Session Manager:** Used to securely connect to and execute commands on my EC2 instances for testing connectivity, without needing open inbound ports or SSH keys.
* **Security Groups:** Acted as instance-level firewalls, controlling traffic to and from my instances, ensuring only authorized communication passed through.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

Connecting VPCs felt like orchestrating a complex, yet elegant, dance of data! Each step was about ensuring that different departments (represented by VPCs) could securely and privately share information without exposing it to the wider internet.

Here's a peek at how it all went down:

---

### 1. Initial VPC Landscape Overview:

* My mission began by surveying the existing VPC landscape. I reviewed three pre-configured VPCs: **Marketing VPC**, **Developer VPC**, and **Finance VPC**.
* I specifically examined the Finance VPC's details, noting that instances within it (like the `FinanceServer`) did not have public IPv4 addresses, emphasizing their private nature.

![Screenshot (4673)](https://github.com/user-attachments/assets/5a7097ff-62a9-4e13-8a9b-9e577b48a4ae)

![Screenshot (4674)](https://github.com/user-attachments/assets/d738c192-2990-4aea-976b-08a0e56dc6df)
*A glance at the existing Marketing, Developer, and Finance VPCs in my AWS environment.*

---

### 2. Connecting to the Marketing Server via Session Manager:

* To prepare for testing, I navigated to the EC2 Dashboard and selected the `MarketingServer` instance.
* I then used Session Manager to establish a secure, browser-based terminal connection to this instance, avoiding the need for SSH keys or open ports.

![Screenshot (4688)](https://github.com/user-attachments/assets/852f3001-685e-4638-84f4-89ddc90bf2a5)

![Screenshot (4689)](https://github.com/user-attachments/assets/385ec93b-7825-401e-8e81-27b7c6af54be)

![Screenshot (4690)](https://github.com/user-attachments/assets/d6cc120e-7c5a-4ad2-ac58-01a987a81355)
*Securely connecting to the Marketing Server instance using Session Manager.*

---

### 3. Testing Initial Inter-VPC Connectivity (Expected Failure!):

* From the `MarketingServer`'s Session Manager terminal, I attempted to `ping` the `FinanceServer` using its private IP address (which I copied from the FinanceServer's details earlier).
* As anticipated, the `ping` command "hung" and resulted in 100% packet loss. This demonstrated the default isolation between VPCs and the immediate need for a peering connection.

![Screenshot (4686)](https://github.com/user-attachments/assets/50a02207-bd61-4df5-9e02-a5142f44a9cc)

![Screenshot (4690)](https://github.com/user-attachments/assets/d6cc120e-7c5a-4ad2-ac58-01a987a81355)
*Demonstrating the initial lack of connectivity between Marketing and Finance VPCs via a failed ping.*

---

### 4. Creating the VPC Peering Connection:

* I initiated the creation of a new VPC peering connection, naming it `Marketing-Finance`.
* I specified the `Marketing VPC` as the **Requester** and the `Finance VPC` as the **Accepter**, ensuring their CIDR ranges (`10.10.0.0/16` and `172.31.0.0/16` respectively) did not overlap, which is a critical requirement for peering.

![Screenshot (4696)](https://github.com/user-attachments/assets/da8ac2b3-f323-410c-baed-f740dfbbdc84)

![Screenshot (4697)](https://github.com/user-attachments/assets/709cf703-32e2-465e-9491-75cd1886f2d5)
![Screenshot (4698)](https://github.com/user-attachments/assets/d0b3d66b-5f65-495a-8c2c-9bb8d133ffbe)

![Screenshot (4699)](https://github.com/user-attachments/assets/cd1fc5a9-f0e9-4ccb-9d93-e924ee15d5f3)
*Configuring the new VPC peering connection between the Marketing and Finance VPCs.*

---

### 5. Accepting the VPC Peering Connection:

* After creation, the peering connection entered a "pending acceptance" state. I navigated to the "Peering connections" section and accepted the connection request. This is a crucial step to activate the peering link.

![Screenshot (4700)](https://github.com/user-attachments/assets/723b7280-ee10-4b97-be91-16db40658e3d)
![Screenshot (4701)](https://github.com/user-attachments/assets/6a949ac0-95e5-427e-b5c9-e4883b88d8b5)

![Screenshot (4702)](https://github.com/user-attachments/assets/e1de81db-d46d-4be2-a667-0ae41b9e9337)
*Accepting the pending VPC peering connection to activate the link.*

---

### 6. Configuring Route Tables for Marketing VPC:

* Once the peering connection was established, I updated the **Marketing VPC's route table**.
* I added a new route:
    * **Destination:** `172.31.0.0/16` (the CIDR block of the Finance VPC).
    * **Target:** The newly created `Marketing-Finance` peering connection.
* This rule tells the Marketing VPC that any traffic destined for the Finance VPC's network should be routed through the peering connection.

![Screenshot (4703)](https://github.com/user-attachments/assets/3bb4a6ca-1ac8-4b9b-9be8-0edf239aca1d)

![Screenshot (4704)](https://github.com/user-attachments/assets/cc8fd329-d040-4682-bfba-bb2e9942364c)

![Screenshot (4705)](https://github.com/user-attachments/assets/030508b8-70e6-4c5a-b108-de2caaefa5c0)

![Screenshot (4706)](https://github.com/user-attachments/assets/323464d7-46f9-44e4-8762-fb29c2ba999d)

![Screenshot (4708)](https://github.com/user-attachments/assets/c8ba949f-6f4f-4952-9683-34df874b52d1)
*Updating the Marketing VPC's route table to direct traffic to the Finance VPC via peering.*

---

### 7. Configuring Route Tables for Finance VPC:

* Critically, VPC peering requires routes in *both* associated route tables.
* Therefore, I also updated the **Finance VPC's route table**.
* I added another new route:
    * **Destination:** `10.10.0.0/16` (the CIDR block of the Marketing VPC).
    * **Target:** The `Marketing-Finance` peering connection.
* This ensured that traffic from the Finance VPC destined for the Marketing VPC would also flow correctly.

![Screenshot (4709)](https://github.com/user-attachments/assets/fecd8758-ce32-44f8-9f77-a5ddb636d6f5)

![Screenshot (4710)](https://github.com/user-attachments/assets/3f16b108-ba88-4221-92a8-1473efbe1cc8)

![Screenshot (4712)](https://github.com/user-attachments/assets/8ecd1395-a6cf-4524-b80d-51e5a7d474c1)

![Screenshot (4713)](https://github.com/user-attachments/assets/51037c03-942a-4005-b04b-7b4866a49680)

![Screenshot (4715)](https://github.com/user-attachments/assets/89b9895d-8d21-4f74-8512-64d9acff6d27)
*Updating the Finance VPC's route table to enable communication back to the Marketing VPC.*

---

### 8. Final Connectivity Test:

* With both route tables configured, I returned to the `MarketingServer`'s Session Manager terminal.
* I re-ran the `ping` command to the `FinanceServer`'s private IP address. This time, the `ping` commands were successful, indicating seamless and private communication between the two peered VPCs!

![Screenshot (4719)](https://github.com/user-attachments/assets/e2907a99-43a3-4379-8d37-4515b6f9d4dd)

![Screenshot (4720)](https://github.com/user-attachments/assets/4c631d9d-dc36-4921-be07-f8bcb0f06800)

![Screenshot (4721)](https://github.com/user-attachments/assets/d1069dfd-ad67-4cb5-acbf-3b8aeaf79458)

![Screenshot (4689)](https://github.com/user-attachments/assets/0d202797-93d5-469f-b329-26760adc3be3)
![Screenshot (4722)](https://github.com/user-attachments/assets/044132e4-10a9-450c-8dd0-de2516ba830c)
*Verifying successful communication between the Marketing and Finance VPCs after configuring peering!*

---

## 🔑 Key Takeaways & Networking Revelations: 🔑

This lab was an eye-opener into the power and intricacies of inter-VPC communication.

* **VPC Peering Demystified:** VPC peering is a fundamental way to connect VPCs privately, ensuring secure and direct communication without traversing the public internet.
* **Two-Way Street for Routes:** A crucial lesson learned is that for VPC peering to work, route tables in *both* peered VPCs must be updated to direct traffic to each other through the peering connection. One-way routing simply won't cut it!
* **No Overlapping CIDRs:** The importance of non-overlapping CIDR blocks for peered VPCs was reinforced. This prevents routing conflicts and ensures distinct network spaces.
* **Stateful Security Groups:** Understanding that security groups are stateful (meaning response traffic is automatically allowed) is key to designing effective and efficient security rules.
* **Architectural Flexibility:** VPC peering provides immense flexibility for designing complex, multi-VPC architectures, whether for different departments, environments (dev/prod), or multi-tier applications.

---

## ✨ What's Next on My Cloud Quest: ✨

Connecting VPCs has significantly expanded my understanding of how applications and services can interact securely across different network segments in AWS. This knowledge is invaluable as I continue to build robust, scalable, and secure cloud solutions. My journey towards becoming a Cloud Security Specialist is gaining serious momentum, and mastering these interconnected networks is a vital step!

---

## 🤝 Let’s Connect!

Curious about cloud networking, security, or just want to chat about building robust cloud foundations? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---

✨ Securing the cloud and serving vibes! 🥂💅☁️✨

---
