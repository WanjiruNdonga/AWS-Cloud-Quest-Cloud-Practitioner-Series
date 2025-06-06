---

# Quest 8: Core Security Concepts Lab - Fortifying My Cloud Defenses! 🛡️☁️

Continuing my deep dive into the AWS ecosystem, this repo details my engagement through the **Core Security Concepts** lab within the AWS Cloud Quest series. This mission was pivotal in understanding the foundational elements of security in the cloud, particularly focusing on Identity and Access Management (IAM) to control access to AWS resources. It's like becoming a digital bouncer for my cloud environment, ensuring only authorized personnel get in! 👮

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

This practice lab provided hands-on experience with fundamental AWS security services, emphasizing the principle of least privilege.

The key objectives for this mission included:
* Create an IAM group and users.
* Manage secure access to AWS services and resources using IAM.

---

## 🛠️ AWS Services I Conquered: My Security Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS security service:

* **AWS Identity and Access Management (IAM):** The cornerstone of this lab, used to securely control access to AWS services and resources. IAM is offered at no additional charge.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

Securing cloud resources is paramount, and this lab provided an excellent practical foundation for implementing robust access controls.

Here's a peek at how it all went down:

---

### 1. Exploring IAM (Initial Search)

I searched for "iam" in the top navigation bar search box. In the search results, under Services, I clicked **IAM**.

![Screenshot (4085)](https://github.com/user-attachments/assets/04ece585-ea60-48d3-83b4-fe09ba575c72)
*Searching for IAM in the AWS console and selecting the service.*

---

### 2. Navigating to Create User Group

In the left navigation pane, I clicked **User groups**. In the User groups section, I clicked **Create group**. A user group is a collection of IAM users used to specify permissions for a collection of users.

![Screenshot (4086)](https://github.com/user-attachments/assets/a02d1063-7ae4-41da-b4b1-e68e65f0e64d)
*Navigating to the User groups section and initiating the creation of a new user group.*

---

### 3. Naming the User Group

For the **User group name**, I typed `SupportEngineers`. A user group can contain many users, and a user can belong to multiple user groups, but user groups cannot be nested.

![Screenshot (4087)](https://github.com/user-attachments/assets/463d798d-f27d-4b78-9781-9164467783fc)
*Specifying 'SupportEngineers' as the name for the new user group.*

---

### 4. Attaching Permissions Policies

In the **Attach permissions policies** search box, I typed `AmazonEC2ReadOnlyAccess` and pressed Enter. I then selected the check box for `AmazonEC2ReadOnlyAccess` and reviewed its description, which states it provides read-only access to Amazon EC2 via the AWS Management Console. Finally, I clicked **Create user group**. All users in this group will inherit the permissions defined in the selected policies.

![Screenshot (4088)](https://github.com/user-attachments/assets/61605ccd-1852-4faa-821f-02962b5cf7fe)
*Attaching the `AmazonEC2ReadOnlyAccess` policy to the `SupportEngineers` group.*

![Screenshot (4089)](https://github.com/user-attachments/assets/36a2cb04-bd34-482d-a407-6a93625a117d)

---

### 5. Navigating to Create User

In the left navigation pane, I clicked **Users**. In the Users section, I clicked **Create user**. An IAM user is an entity created in AWS that represents either a human user or workload that interacts with AWS services, consisting of a name and credentials.

![Screenshot (4092)](https://github.com/user-attachments/assets/9024ed70-7561-49a6-8ce8-36f3a261bcf3)
*Navigating to the Users section to create a new IAM user.*

---

### 6. Specifying User Details and Password

In the **Specify user details** step, for **User name**, I typed `support-engineer-1`. I selected the check box to **Provide user access to the AWS Management Console**. For **Console password**, I chose **Custom password** and typed `supportPassword!125` in the text box below that. All passwords must contain at least eight characters.

![Screenshot (4094)](https://github.com/user-attachments/assets/fcdbcee5-fe69-441f-91b4-30fc72eb7e5b)
*Entering user details, including the username 'support-engineer-1' and a custom console password.*

---

### 7. Adding User to Group

In the **Set permissions** step, for **Permissions options**, I chose **Add user to group**. In the **User groups** section, I selected the check box to select `SupportEngineers`. Using groups is a best practice for managing user permissions by job functions. I then clicked **Next**.

![Screenshot (4095)](https://github.com/user-attachments/assets/befb851d-7cab-4667-8feb-66940c956c3b)
*Adding the new user 'support-engineer-1' to the 'SupportEngineers' group.*

---

### 8. Adding Tags and Creating User

In the **Review and create** step, in the Tags section, I clicked **Add new tag**. For **Key**, I typed `job-title`. For **Value**, I typed `Support Engineer`. Tags are key-value pairs that help identify, organize, or search for resources. Finally, I clicked **Create user**.

![Screenshot (4096)](https://github.com/user-attachments/assets/c27f07a0-b0be-4f84-ad3b-e3aa1ffd1d4e)
*Adding 'job-title' and 'Support Engineer' tags before creating the IAM user.*

---

### 9. Retrieving Password and Console Sign-in URL

In the **Retrieve password** step, under **Console sign-in URL**, I clicked the copy icon to copy the provided URL and pasted it into a text editor. I also had the option to download the `.csv` file containing the console sign-in link and credentials. I then clicked **Return to users list**.

![Screenshot (4097)](https://github.com/user-attachments/assets/efa649a8-4f12-4ed4-864c-9c9bdd00863b)
*Retrieving the console sign-in URL and confirming user creation.*

---

### 10. Viewing User Details

I clicked on the `support-engineer-1` user to view its details.

![Screenshot (4102)](https://github.com/user-attachments/assets/6fb054f9-07ad-43c3-9cad-219ccd7e8e36)
*Viewing the details of the newly created 'support-engineer-1' IAM user.*

---

### 11. Reviewing Permissions Boundaries 

I reviewed any existing permissions boundaries attached to the user, understanding that these define the maximum permissions that an identity-based policy can grant.

![Screenshot (4104)](https://github.com/user-attachments/assets/e7960bfa-7e87-4dc7-aba4-4df17f9dc5c6)
*Reviewing permissions boundaries associated with the IAM user.*

---

### 12. Navigating to Security Credentials

In the user details page, I navigated to the **Security credentials** tab to view access keys and other credential information.

![Screenshot (4101)](https://github.com/user-attachments/assets/b7304545-e727-4f4f-88fa-d637ffea239e)
*Accessing the Security credentials tab for the IAM user.*

---

### 13. Reviewing Policy Details

I selected an existing policy, such as `AmazonEC2ReadOnlyAccess`, and reviewed its JSON policy document to understand the specific permissions it grants.

![Screenshot (4100)](https://github.com/user-attachments/assets/4412f907-a35e-4aba-9d2b-404055f5ab97)
*Reviewing the JSON document of an IAM policy to understand its permissions.*

---

### 14. Retrieving Password and Console Sign-in URL

In the **Retrieve password** step, under **Console sign-in URL**, I clicked the copy icon to copy the provided URL and pasted it into a text editor. I also had the option to download the `.csv` file containing the console sign-in link and credentials. I then clicked **Return to users list**.

![Screenshot (4097)](https://github.com/user-attachments/assets/29af2c05-1f85-4713-a94a-024a80d2d249)
*Retrieving the console sign-in URL and confirming user creation.*

---

### 15. Logging Out and Logging In as Restricted User

I first logged out of the AWS Management Console as the admin user. Then, I opened a new browser window or incognito tab and used the copied console sign-in URL. I entered the `support-engineer-1` username and the password `supportPassword!125` to log in as the newly created user.

![Screenshot (4105)](https://github.com/user-attachments/assets/049ba542-7c54-4c49-8108-c219ed38ad6f)
*Logging into the AWS Management Console as 'support-engineer-1'.*

---

### 16. Describing EC2 Instances (Permitted Action)

As `support-engineer-1`, I navigated to the EC2 dashboard. I was able to successfully view and describe the running EC2 instances, confirming that the `AmazonEC2ReadOnlyAccess` policy granted the expected permissions.

![Screenshot (4107)](https://github.com/user-attachments/assets/c45d2ef0-a60e-4082-a5c2-d233a1e5687a)
*Successfully viewing EC2 instance details as 'support-engineer-1'.*

---

### 17. Attempting to Terminate an EC2 Instance (Denied Action)

Still logged in as `support-engineer-1`, I attempted to terminate an EC2 instance. As expected, this action failed, and an "Access Denied" error message was displayed. This perfectly demonstrated the principle of least privilege, as the user only had read-only access and could not perform write operations.

![Screenshot (4108)](https://github.com/user-attachments/assets/75e94166-229a-4583-8d8f-48ae090c5616)
![Screenshot (4109)](https://github.com/user-attachments/assets/6bfa9d25-f399-4872-9888-347663a542ab)
![Screenshot (4110)](https://github.com/user-attachments/assets/35605ebb-20bc-4033-984f-01c095f73e19)
*Attempting to terminate an EC2 instance as 'support-engineer-1' resulted in an "Access Denied" error.*

---

## 🔑 Key Takeaways & Security Revelations: 🔑

This lab significantly deepened my understanding of security in AWS, particularly concerning access control.

* **IAM is Foundational:** IAM is not just a service; it's the bedrock of security in AWS, allowing granular control over who can do what with which resources.
* **Principle of Least Privilege:** This lab reinforced the importance of granting only the necessary permissions (least privilege) to users and roles, minimizing potential security risks.
* **Groups for Scalability:** Using IAM groups simplifies managing permissions for multiple users with similar job functions, promoting scalability and consistency.
* **Policies Define Access:** IAM policies are the language of permissions, clearly defining the actions allowed or denied on specific resources. Understanding policy structure is crucial.
* **Separation of Duties:** The practice of creating different users with specific roles (e.g., `support-engineer-1` with read-only access) helps enforce separation of duties, a key security best practice.

---

## ✨ What's Next on My Cloud Quest: ✨

Mastering core security concepts is a critical step towards becoming a proficient cloud professional. This lab has provided me with invaluable hands-on experience in implementing robust access controls. I'm now eager to delve into more advanced security topics, including data encryption, network security, and compliance, as I continue my journey to become a Cloud Security Specialist.

---

## 🤝 Let’s Connect!

Curious about cloud security, IAM best practices, or just want to chat about building secure cloud environments? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---

✨ Securing the cloud, one IAM policy at a time! 🔒☁️✨

---
