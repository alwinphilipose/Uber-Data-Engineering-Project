# 🚗 Uber Real-Time Data Engineering Project

A comprehensive data engineering project that simulates real-time Uber ride data generation, streaming, and processing. This project demonstrates end-to-end data pipeline architecture using modern cloud technologies.

---

## 📋 Table of Contents
- [Overview](#overview)
- [Architecture](#architecture)
- [Features](#features)
- [Technologies](#technologies)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Setup & Installation](#setup--installation)
- [Running the Project](#running-the-project)
- [How It Works](#how-it-works)
- [Credits](#credits)

---

## 🎯 Overview

This project builds a **real-time data pipeline** that:
- Generates synthetic Uber ride data
- Streams data to Azure Event Hubs
- Processes and transforms data using Apache Spark
- Organizes data into Bronze, Silver, and Gold layers (Medallion Architecture)
- Provides a simple web interface to book rides and trigger data generation

Perfect for learning **Data Engineering**, **Cloud Technologies**, and **Real-Time Processing**!

---

## 🏗️ Architecture

![Project Architecture](./architecture.png)

**Data Flow:**
```
Web Interface (FastAPI)
    ↓
Generate Fake Ride Data
    ↓
Send to Azure Event Hubs
    ↓
Apache Spark Processing
    ↓
Bronze Layer (Raw Data)
    ↓
Silver Layer (Cleaned Data)
    ↓
Gold Layer (Business Models)
```

---

## ✨ Features

- **Web Interface**: Book rides through a simple FastAPI web app
- **Fake Data Generation**: Creates realistic Uber ride data using Faker library
- **Real-Time Streaming**: Sends data to Azure Event Hubs
- **Multi-Layer Processing**: 
  - Bronze: Raw ingestion
  - Silver: Data cleaning and validation
  - Gold: Business-ready models
- **Dimension Tables**: Passenger, Driver, Vehicle dimensions with SCD Type 1
- **Scalable Architecture**: Ready for production-level data volumes

---

## 🛠️ Technologies

| Component | Technology |
|-----------|-----------|
| **Language** | Python 3.12+ |
| **Web Framework** | FastAPI + Uvicorn |
| **Data Generation** | Faker |
| **Cloud Messaging** | Azure Event Hubs |
| **Stream Processing** | Apache Spark (PySpark) |
| **Data Lakehouse** | Databricks |
| **Data Format** | JSON, SQL |
| **Package Manager** | uv |
| **Version Control** | Git |

---

## 📁 Project Structure

```
Uber_Data_Engineer_Project/
│
├── api.py                          # FastAPI web application
├── connection.py                   # Azure Event Hub connection logic
├── data.py                         # Fake data generation functions
├── pyproject.toml                  # Project dependencies
├── requirements.txt                # Python packages
├── uv.lock                        # Locked dependency versions
│
├── Code_Files/
│   ├── ingest.py                  # Bronze layer - Raw data ingestion
│   ├── silver.py                  # Silver layer - Data cleaning & transformation
│   ├── model.py                   # Gold layer - Business models & dimensions
│   ├── silver_obt.ipynb           # Silver layer notebook
│   ├── bronze_adls.ipynb          # Bronze layer notebook
│   └── silver_obt.sql             # SQL transformations
│
├── Data/
│   ├── bulk_rides.json            # Initial bulk ride data
│   ├── map_*.json                 # Lookup tables (cities, vehicle types, etc.)
│
├── templates/
│   ├── home.html                  # Home page for booking
│   └── confirmation.html          # Confirmation page
│
└── README.md
```

---

## 📋 Prerequisites

Before you begin, ensure you have:
- **Python 3.12 or higher**
- **Git**
- **uv** package manager
- **Azure Account** (for Event Hubs)
- **Databricks Workspace** (for Spark processing, optional for learning)

---

## 🚀 Setup & Installation

### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/Uber-Data-Engineering-Project.git
cd Uber_Data_Engineer_Project
```

### 2. Install uv (If Not Already Installed)
**Windows (PowerShell):**
```powershell
irm https://astral-sh.github.io/uv/install.ps1 | iex
```

**Or using pip:**
```bash
pip install uv
```

### 3. Install Project Dependencies
```bash
uv sync
```

### 4. Configure Environment Variables
Create a `.env` file in the project root:
```env
CONNECTION_STRING=your_azure_eventhub_connection_string
EVENT_HUBNAME=your_event_hub_name
```

---

## ▶️ Running the Project

### Option 1: Start the Web Server
```bash
uv run uvicorn api:app --reload
```
- Open browser: **http://localhost:8000**
- Click "Book Ride" to generate and stream data

### Option 2: Run Spark Processing
In a Databricks or Spark environment:
```bash
# Bronze layer (ingestion)
spark-submit Code_Files/ingest.py

# Silver layer (transformation)
spark-submit Code_Files/silver.py

# Gold layer (modeling)
spark-submit Code_Files/model.py
```

---

## 🔄 How It Works

### 1. **Data Generation** (`data.py`)
- Creates fake passenger, driver, vehicle, and ride data
- Uses Faker library for realistic details
- Includes pricing, location, and status information

### 2. **Event Streaming** (`connection.py`)
- Connects to Azure Event Hubs
- Sends generated ride data as JSON events
- Handles error logging and reconnection

### 3. **Web Interface** (`api.py`)
- FastAPI application with two routes:
  - `/` - Home page with booking form
  - `/book` - Generates ride and streams to Event Hub

### 4. **Data Processing Pipeline**
- **Bronze**: Raw data ingested from Event Hubs
- **Silver**: Data cleaned, deduplicated, and validated
- **Gold**: Dimension tables (Passengers, Drivers, Vehicles) with Change Data Capture (CDC)

---

## 📊 Sample Data Structure

Each ride event includes:
- **Ride Info**: ride_id, confirmation_number, booking_timestamp
- **Passenger**: name, email, phone, rating
- **Driver**: name, license, phone, rating
- **Vehicle**: type, make, model, color, license plate
- **Locations**: pickup/dropoff coordinates and addresses
- **Pricing**: base fare, distance fare, time fare, surge, total
- **Ride Status**: completed or cancelled

---

## 🎓 Learning Outcomes

By studying this project, you'll learn:
- Real-time data streaming architecture
- ETL/ELT pipeline design
- Medallion Architecture (Bronze/Silver/Gold)
- Apache Spark distributed processing
- Azure cloud services
- Web API development with FastAPI
- Data modeling and dimension tables

---

## 🙏 Credits

This project is a **real-time data engineering implementation** following modern data pipeline best practices and cloud architecture patterns.

---

## 📝 License

This project is for educational purposes. Please refer to the original project's license.

---

## 💡 Future Enhancements

- [ ] Add real-time dashboards (Power BI, Grafana)
- [ ] Implement data quality checks
- [ ] Add machine learning predictions
- [ ] Deploy to Kubernetes
- [ ] Add unit and integration tests
- [ ] Documentation for Databricks setup

---

## 📧 Contact & Questions

If you have questions or suggestions:
- Open an Issue on GitHub
- Feel free to fork and contribute!

---

**Happy Learning! 🚀**



