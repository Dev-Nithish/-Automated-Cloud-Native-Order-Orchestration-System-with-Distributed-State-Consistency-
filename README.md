# 📦 Cloud-Native Order Processing Pipeline

A high-performance, event-driven microservices architecture built with **Node.js**, **Docker**, and **AWS**. This project demonstrates the full lifecycle of an order—from a frontend dashboard to persistent archival in the cloud.

## 🚀 The Architecture
The system is built on a decoupled microservices pattern to ensure scalability and fault tolerance:

* **Gateway Service:** REST API (Express.js) that ingests orders and manages live state in DynamoDB.
* **Worker Service:** Background processor that handles heavy archival tasks to Amazon S3.
* **Infrastructure:** Orchestrated with Docker Compose for seamless local and cloud deployment.



## 🛠️ Tech Stack
* **Cloud:** AWS (EC2, DynamoDB, S3, IAM)
* **Backend:** Node.js, Express.js, AWS SDK v3
* **DevOps:** Docker, Docker Compose, AWS CLI
* **Frontend:** HTML5, Bootstrap 5 (Responsive Dashboard)

## 💡 Key Features & Solutions
### 1. Synchronized Data Archival
Solved the "Distributed State Mismatch" problem. I engineered the worker logic to ensure that S3 snapshots are perfectly synchronized with DynamoDB's updated status, providing a consistent "Source of Truth" across the entire pipeline.

### 2. IAM Least Privilege
Secured the infrastructure by implementing specific IAM policies, ensuring the EC2 instance only has the exact permissions required to read/write to specific S3 buckets and DynamoDB tables.

### 3. Real-Time Tracking
Built a live tracking dashboard that polls the backend to show the transition of orders from `PENDING` to `BATCHED` as they are processed by the worker service.

## 🏁 Getting Started
```bash
# Clone the repository
git clone [https://github.com/your-username/cloud-order-pipeline.git](https://github.com/your-username/cloud-order-pipeline.git)

# Build and Start the services
docker-compose up -d --build
