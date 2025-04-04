# **Realtime Data Streaming | End-to-End Data Engineering Project**

## **Table of Contents**
1. [Introduction](#introduction)
2. [System Architecture](#system-architecture)
3. [What You'll Learn](#what-youll-learn)
4. [Technologies](#technologies)
5. [Getting Started](#getting-started)
6. [Setup and Deployment](#setup-and-deployment)
7. [Conclusion](#conclusion)

---

## **Introduction**

In the modern data-driven world, real-time data processing plays a crucial role in analytics, monitoring, and decision-making. This project provides a comprehensive guide to building an end-to-end data engineering pipeline that ingests, processes, and stores data using a robust set of technologies.

The pipeline integrates multiple tools and frameworks such as **Apache Airflow, Apache Kafka, Apache Zookeeper, Apache Spark, and Cassandra**, all containerized using **Docker** for seamless deployment and scalability.

Whether you're a beginner or an experienced data engineer, this project will help you gain hands-on experience with **real-time data streaming, orchestration, and distributed processing**.

---

## **System Architecture**

### **Overview**
This real-time data pipeline consists of multiple interconnected components designed to efficiently ingest, process, and store data in a **distributed** and **fault-tolerant** manner.
![Data engineering architecture](https://github.com/user-attachments/assets/6de919c4-dd96-4920-9353-67cbf9ab182d)


### **Key Components:**
1. **Data Source**:
   - The project uses the **randomuser.me API** to generate synthetic user data for ingestion.
   
2. **Apache Airflow** (Orchestration Layer):
   - Automates the fetching of data from the API and stores it in a **PostgreSQL** database.
   
3. **Apache Kafka & Zookeeper** (Streaming Layer):
   - Kafka acts as the messaging backbone, streaming data from **PostgreSQL** to **Apache Spark**.
   - **Zookeeper** helps in managing Kafka brokers and leader elections.
   
4. **Control Center & Schema Registry**:
   - Provides tools for monitoring and schema validation of Kafka topics.
   
5. **Apache Spark** (Processing Layer):
   - **Master and Worker nodes** process the real-time data streams for transformation and analytics.
   
6. **Cassandra** (Storage Layer):
   - Stores processed data in a **scalable, distributed, and fault-tolerant** manner.
   
7. **Docker** (Containerization & Deployment):
   - Ensures the entire pipeline runs seamlessly by containerizing all services.

---

## **What You'll Learn**
By working through this project, you will gain valuable hands-on experience in:

✅ **Setting up an automated data pipeline with Apache Airflow**
✅ **Streaming real-time data using Apache Kafka**
✅ **Managing distributed synchronization with Apache Zookeeper**
✅ **Processing real-time data streams using Apache Spark**
✅ **Storing large-scale data efficiently with Cassandra and PostgreSQL**
✅ **Containerizing and deploying your pipeline using Docker**

---

## **Technologies Used**
This project leverages the following cutting-edge technologies:

| Technology        | Purpose  |
|------------------|----------|
| **Apache Airflow** | Workflow orchestration |
| **Python** | Scripting and data processing |
| **Apache Kafka** | Real-time data streaming |
| **Apache Zookeeper** | Kafka cluster management |
| **Apache Spark** | Distributed data processing |
| **Cassandra** | NoSQL database for storing processed data |
| **PostgreSQL** | Relational database for storing raw data |
| **Docker** | Containerization and deployment |

---

## **Getting Started**

### **1️⃣ Clone the Repository**
First, clone the project repository to your local machine:
```bash
git clone https://github.com/airscholar/e2e-data-engineering.git
```

### **2️⃣ Navigate to the Project Directory**
Move into the project folder:
```bash
cd e2e-data-engineering
```

### **3️⃣ Start the Pipeline using Docker Compose**
Run the following command to spin up all services:
```bash
docker-compose up
```
This command will pull the necessary Docker images and start all the services, including Airflow, Kafka, Spark, and Cassandra.

---

## **Setup and Deployment**

### **Environment Configuration**
- Ensure you have **Docker and Docker Compose** installed.
- Check the **docker-compose.yml** file to configure services as per your system requirements.
- Modify **Airflow DAGs** in `dags/` directory to customize data ingestion.
- Kafka topics are configured in **config/kafka-config.json**.

### **Running Airflow DAGs**
Once the services are up, navigate to **http://localhost:8080** to access the **Airflow UI** and trigger the DAG for data ingestion.

### **Monitoring Kafka Streams**
You can check the Kafka topics and messages using the following command:
```bash
docker exec -it kafka /bin/sh
kafka-console-consumer --bootstrap-server localhost:9092 --topic user_data --from-beginning
```

### **Processing Data in Spark**
Connect to the Spark master node and check the job execution status:
```bash
spark-submit --master spark://localhost:7077 scripts/spark_processor.py
```

### **Accessing Cassandra Data**
To query the processed data stored in Cassandra:
```bash
docker exec -it cassandra cqlsh
SELECT * FROM user_data;
```

---

## **Conclusion**
By the end of this project, you will have built a **fully functional, end-to-end real-time data streaming pipeline**. You will understand the core concepts behind **data ingestion, streaming, processing, and storage** using modern **big data technologies**.



🚀 Happy Coding & Data Engineering!

