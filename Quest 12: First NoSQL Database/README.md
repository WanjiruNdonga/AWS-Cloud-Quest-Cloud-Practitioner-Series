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

I created a new DynamoDB table, defining its primary (partition) & sort key. This foundational step sets up the structure for storing items.
* I clicked "Create table" in the DynamoDB console.
* I specified the table name i.e. `UserVideoHistory`.
* I defined the primary key, including a partition key (i.e. `userid`) and an optional sort key (i.e., `lastDateWatched`).

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

* I input values for the item's defined attributes and proceeded to create the item.

![Screenshot (5557)](https://github.com/user-attachments/assets/61660fef-c42d-40c3-8b42-373969b96b9b)

![Screenshot (5558)](https://github.com/user-attachments/assets/e782d095-fcee-45c6-929e-ba2a9deefbdf)

---

### 4. Adding New Attributes to an Existing Item

To enrich an existing record, I added new attributes i.e. `videoID`, `preferredLanguage` & `supportedDeviceTypes`, with their corresponding values to the item already present in the table. This demonstrated the schema-less nature of NoSQL databases.

![Screenshot (5561)](https://github.com/user-attachments/assets/35bfb7ea-d8f2-49c2-ae28-51f082413d62)

![Screenshot (5562)](https://github.com/user-attachments/assets/96bfdc73-2b7b-4369-ae84-090692cdb189)

![Screenshot (5563)](https://github.com/user-attachments/assets/1418bc72-3d52-4f06-b5a4-434c28368b6e)

![Screenshot (5564)](https://github.com/user-attachments/assets/fab37d3e-7a9c-45c6-ae92-5098898a382f)

---

### 5. Updating the Item with a New Attribute

I practiced modifying data by updating the item with a new attribute i.e. `lastStopTime`

![Screenshot (5565)](https://github.com/user-attachments/assets/d91530b5-30c5-4646-a9f2-da4a83bfe5fa)

![Screenshot (5566)](https://github.com/user-attachments/assets/b7418f9f-fa60-4cf3-9870-a3cdd67376d0)

---

### 6. Querying Items Using the Primary Key

To retrieve specific items efficiently and confirm data presence, I performed a query using the table's primary key.
* From the "Explore items" tab:
* I entered a specific values for the table's partition key and sort key into the search field.
* I then executed the query (e.g., by pressing Enter or clicking "Run") to retrieve all items that match the specified primary key.

![Screenshot (5568)](https://github.com/user-attachments/assets/dc759eff-b324-4267-86c3-c8f8b7752277)
![Screenshot (5569)](https://github.com/user-attachments/assets/cf7d9402-d698-40db-bb67-25b2b9a5e764)
*Executing a query operation using the primary key to retrieve specific items from the table.*

---

### 7. Deleting an Attribute from an Item

To demonstrate data manipulation flexibility, I specifically `removed` an attribute from an existing item, leaving the rest of the item intact.

![Screenshot (5574)](https://github.com/user-attachments/assets/fe7ef154-0bb8-4f5f-ab83-971e17aef874)
*Removing a specific attribute from an item in the table.*

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
