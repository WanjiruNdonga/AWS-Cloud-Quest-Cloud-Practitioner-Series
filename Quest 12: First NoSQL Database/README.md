---

# Quest 12: First NoSQL Database Lab - Mastering DynamoDB Fundamentals 📊🚀 

This project chronicles my hands-on journey through the **First NoSQL Database** lab, where I gained practical experience with Amazon DynamoDB. This lab focuses on understanding the core concepts and fundamental operations of a NoSQL database, specifically through creating, manipulating, and managing data within DynamoDB tables.

---

## 🎯 Lab Mission Unlocked: Core Objectives 🎯

This lab allowed me to achieve proficiency in essential DynamoDB operations.

### Practice Lab Goals:
* Creating a new Amazon DynamoDB table.
* Adding an item to the table.
* Adding a new attribute to an existing item in the table.
* Updating an existing attribute in an item.
* Deleting an attribute from an item.
* Deleting an item from the table.
* Deleting a DynamoDB table.

### DIY Goals:
* Create a new item in the `UserVideoHistory` table with a unique `userid` value.
* Add a new attribute named "rating" with a Number data type to the newly created record.

---

## 🛠️ AWS Services I Conquered: My NoSQL Toolkit! 🛠️

For this mission, I primarily utilized the following core AWS service:
* **Amazon DynamoDB:** A fully managed, serverless, key-value NoSQL database designed to run high-performance applications at any scale.

---

## 🚀 My Journey Through the Lab (and What I Built!): 🚀

This section outlines the key steps undertaken to achieve the lab objectives, providing a practical demonstration of DynamoDB operations:

---

### 1. Navigating to DynamoDB and Reviewing Tables

I began by accessing the AWS Management Console and navigating to the DynamoDB service. I familiarized myself with the existing tables in the environment.

![Screenshot (5546)](https://github.com/user-attachments/assets/4d3baa75-61b6-4941-9575-8f131125d0e2)

![Screenshot (5548)](https://github.com/user-attachments/assets/96b4ea45-7cd4-4383-9159-63421050b6a8)
*Initial view of the Amazon DynamoDB console.*

---

### 2. Creating a New DynamoDB Table

I created a new DynamoDB table, defining its primary key. This foundational step sets up the structure for storing items.
* I clicked "Create table" in the DynamoDB console.
* I specified the table name i.e., `UserVideoHistory`.
* I defined the primary key, including a partition key (i.e., `userid`) and an optional sort key (i.e., `lastDateWatched`).

![Screenshot (5549)](https://github.com/user-attachments/assets/34f55041-a98b-4504-b0d0-81c7e36afaf6)
*Defining a new DynamoDB table with its primary key attributes.*
   
* I selected the default table settings and proceeded to create the table.

![Screenshot (5550)](https://github.com/user-attachments/assets/f788ce33-1dd1-4f5b-a21e-f6173a2c3b88)
![Screenshot (5551)](https://github.com/user-attachments/assets/21efd6b8-44e2-4ba2-8ff8-75e688de1874)

![Screenshot (5552)](https://github.com/user-attachments/assets/aaa34244-4162-463c-8857-36368cc26f40)

---

### 3. Adding a New Item to the Table

With the table successfully created, I proceeded to populate it by adding a new item, representing a single record in the database.
* I navigated to the "Explore items" tab for my newly created table.

![Screenshot (5554)](https://github.com/user-attachments/assets/b31e2dda-5a52-4b63-9980-54989e7b4ce9)

![Screenshot (5555)](https://github.com/user-attachments/assets/ee373756-29f0-4a63-86a1-57dcb0b49f73)

* I clicked "Create item" to open the item editor.

![Screenshot (5556)](https://github.com/user-attachments/assets/d820e266-d295-4fcf-8614-b83d2b7bfce9)

* I input values for the defined attributes for the item and proceeded to create the item.

![Screenshot (5557)](https://github.com/user-attachments/assets/61660fef-c42d-40c3-8b42-373969b96b9b)

![Screenshot (5558)](https://github.com/user-attachments/assets/e782d095-fcee-45c6-929e-ba2a9deefbdf)

---

### 4. Adding a New Attribute to an Existing Item

To enrich an existing record, I added a new attribute with its corresponding value to an item already present in the table. This demonstrated the schema-less nature of NoSQL databases.

![Add New Attribute](images/nosql_lab_04_add_attribute.png)
*Adding a new attribute to an existing item in the table.*

---

### 5. Updating an Existing Attribute

I practiced modifying data by updating the value of an existing attribute within an item.

![Update Attribute](images/nosql_lab_05_update_attribute.png)
*Caption: Modifying the value of an existing attribute for an item.*

---

### 6. Deleting an Attribute from an Item

To demonstrate data manipulation flexibility, I specifically deleted an attribute from an existing item, leaving the rest of the item intact.

![Delete Attribute](images/nosql_lab_06_delete_attribute.png)
*Caption: Removing a specific attribute from an item in the table.*

---

### 7. Deleting an Item from the Table

I performed a complete item deletion, removing an entire record from the DynamoDB table.

![Delete Item](images/nosql_lab_07_delete_item.png)
*Caption: Deleting an entire item (record) from the DynamoDB table.*

---

## 🔑 Key Learnings & NoSQL Revelations: 🔑

This lab provided critical insights into the fundamental operations of Amazon DynamoDB and NoSQL databases:

* **NoSQL Flexibility:** Gained hands-on understanding of DynamoDB's schema-less nature, allowing for flexible addition, modification, and deletion of attributes within items.
* **Core CRUD Operations:** Mastered the essential Create, Read (implied through viewing/updating), Update, and Delete (CRUD) operations for items and attributes in a NoSQL database.
* **Key-Value Store Concept:** Solidified my understanding of how DynamoDB operates as a key-value store, with items uniquely identified by their primary keys.
* **Managed Database Benefits:** Experienced the ease of use of a fully managed service like DynamoDB, abstracting away server provisioning, patching, and backups.

---

## ✨ What's Next on My Cloud Quest: ✨

Mastering foundational NoSQL operations is a crucial step in modern cloud development. This lab has provided a solid base. I'm now eager to delve into more advanced DynamoDB concepts such as:
* Querying and scanning data efficiently.
* Understanding and optimizing read/write capacity units (RCU/WCU).
* Implementing secondary indexes (Global Secondary Indexes and Local Secondary Indexes).
* Integrating DynamoDB with other AWS services like Lambda for serverless applications.

---

## 🤝 Let’s Connect!

Curious about NoSQL databases, DynamoDB, or just want to chat about data management in the cloud? Let’s connect!

* 💼 [LinkedIn Profile](https://www.linkedin.com/in/mercy-ndonga/)
* 🌍 Based in Nairobi, Kenya | Globally curious

---

✨ Diving deep into data, one NoSQL table at a time! 💾☁️✨

---
