<h1 align="center">Hi 👋, I'm Ismael Elsayed</h1>
<h3 align="center">Data Engineer | Microsoft Data Engineer Intern @ DEPI</h3>

<p align="center">
  Designing modern data architectures, high-performance data pipelines, and real-time data platforms. 
  <br>Based in Menoufia, Egypt.
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=som3a0&label=Profile%20Views&color=0e75b6&style=flat" alt="Profile Views" />
</p>

---

## 🚀 Professional Summary

I am a Data Engineer focused on building scalable and reliable data systems that transform raw data into actionable insights. Currently participating in the Digital Egypt Pioneers Initiative (DEPI) as a Data Engineer Intern, my work involves designing ETL/ELT pipelines, big data processing architectures, real-time streaming systems, and modern data platforms that support advanced analytics and machine learning.

* Architecting scalable **Data Pipelines**
* Building robust **ETL / ELT workflows**
* Processing **large-scale datasets** with distributed computing
* Developing **real-time streaming** systems
* Designing **data warehouses and data lakes**

---

## 🛠 Tech Stack

| Category | Technologies |
| :--- | :--- |
| **Programming** | <img src="https://skillicons.dev/icons?i=python,cpp,mysql" height="30" align="top"/> |
| **Big Data & Streaming** | ![Spark](https://img.shields.io/badge/Apache_Spark-orange?style=flat&logo=apachespark&logoColor=white) ![Kafka](https://img.shields.io/badge/Apache_Kafka-black?style=flat&logo=apachekafka) ![Hadoop](https://img.shields.io/badge/Apache_Hadoop-yellow?style=flat&logo=apachehadoop) ![Hive](https://img.shields.io/badge/Apache_Hive-yellow?style=flat) |
| **Architecture** | ![Data Modeling](https://img.shields.io/badge/Data_Modeling-0e75b6?style=flat) ![Data Warehouse](https://img.shields.io/badge/Data_Warehouse-2ea44f?style=flat) ![Data Lake](https://img.shields.io/badge/Data_Lake-0e75b6?style=flat) |
| **Databases** | <img src="https://skillicons.dev/icons?i=mongodb" height="30" align="top"/> ![SQL DB](https://img.shields.io/badge/SQL_Database-blue?style=flat) ![SSMS](https://img.shields.io/badge/SSMS-blue?style=flat) |
| **Integration (ETL)** | ![SSIS](https://img.shields.io/badge/SSIS-purple?style=flat) |
| **BI & Apps** | ![Power BI](https://img.shields.io/badge/Power_BI-yellow?style=flat&logo=powerbi) <img src="https://skillicons.dev/icons?i=streamlit" height="30" align="top"/> |
| **DevOps & OS** | <img src="https://skillicons.dev/icons?i=docker,git,linux" height="30" align="top"/> |

---

## 📊 Data Engineering Architecture

```mermaid
flowchart LR
    A[(Data Sources)] -->|Ingestion| B(APIs / Batch)
    A -->|Streaming| C(Apache Kafka)
    B --> D{Data Processing\nApache Spark / Python}
    C --> D
    D -->|Transform & Load| E[(Storage Layer\nData Lake / Warehouse)]
    E --> F[Analytics & Visualization\nPower BI / Grafana]
    E --> G[Machine Learning Models]
    
    classDef source fill:#f9f9f9,stroke:#333,stroke-width:2px;
    classDef process fill:#e1f5fe,stroke:#039be5,stroke-width:2px;
    classDef storage fill:#fff3e0,stroke:#fb8c00,stroke-width:2px;
    classDef analytics fill:#e8f5e9,stroke:#43a047,stroke-width:2px;
    
    class A source;
    class B,C,D process;
    class E storage;
    class F,G analytics;
