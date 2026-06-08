# AI-Powered Community Health Monitoring and Early Disease Prediction System

## Project Overview

The AI-Powered Community Health Monitoring and Early Disease Prediction System is a web-based application that uses artificial intelligence to monitor health data and predict potential diseases at an early stage. The system helps individuals and healthcare providers identify health risks, enabling timely medical attention and improving community health management.

## Problem Statement

Many diseases are detected only after symptoms become severe, leading to delayed treatment and increased healthcare costs. Traditional health monitoring methods may not provide timely insights into potential health risks. An AI-based system is needed to analyze health data continuously and predict diseases at an early stage for better healthcare outcomes.

## Project Objectives

- Develop an AI-based system for health monitoring and disease prediction.
- Analyze health data to identify potential health risks.
- Provide early warnings for possible diseases.
- Support healthcare professionals in decision-making.
- Improve community health awareness and preventive care.
- Enable timely medical intervention through early detection.
## User Roles

🔸 Administrator

🔸 Doctor

🔸 Healthcare Worker

🔸 Community Member (Patient)

---

## Module List

### Dashboard
🔸 Provides an overview of community health statistics, disease trends, alerts, and prediction summaries.

### User Management
🔸 Manages user registration, login, profiles, roles, and access permissions.

### Health Data Collection
🔸 Collects patient health information such as symptoms, vital signs, medical history, and health records.

### Disease Prediction
🔸 Uses AI and Machine Learning algorithms to predict potential diseases based on health data.

### Community Health Monitoring
🔸 Tracks disease patterns, monitors community health status, and identifies high-risk areas.

### Alert & Notification
🔸 Sends health alerts, early disease warnings, reminders, and emergency notifications.

### Doctor Consultation
🔸 Allows doctors to review patient data and provide recommendations.

### Report Generation
🔸 Generates individual and community health reports.

🔸 Displays health statistics, charts, and trend analysis.

### Settings
🔸 Manages account and notification settings.
## Use Case Diagram

### Actors
- Administrator
- Doctor
- Healthcare Worker
- Community Member (Patient)

                     

```text
+----------------------+
| Community Member     |
|      (Patient)       |
+----------------------+
        |
-----------------------------
|      |        |         |
|      |        |         |
Register  Enter   View    Receive
Login     Health  Report  Alerts
          Data


+----------------------+
| Healthcare Worker    |
+----------------------+
        |
-----------------------------
|            |             |
|            |             |
Login    Collect Health   Update
          Data            Records


+----------------------+
|        Doctor        |
+----------------------+
        |
-----------------------------
|            |             |
|            |             |
Login     View Patient   Provide
           Data          Advice


+----------------------+
|    Administrator     |
+----------------------+
        |
-----------------------------
|            |             |
|            |             |
Manage      Monitor      Generate
Users       System       Reports

## SQL Schema

## Description

This SQL schema defines the database structure for the AI-Powered Community Health Monitoring and Early Disease Prediction System.

## Users Table

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL, -- Password hashing kaga length 255 ah mathiruken
    role VARCHAR(20) DEFAULT 'user' -- Default role set panniruken
);
```

## Health_Records Table

```sql
CREATE TABLE health_records (
    record_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    temperature DECIMAL(4,2),
    blood_pressure VARCHAR(20),
    heart_rate INT,
    blood_sugar DECIMAL(5,2),
    symptoms TEXT,
    record_date DATE,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
```

## Disease_Predictions Table

```sql
CREATE TABLE disease_predictions (
    prediction_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    record_id INT,
    predicted_disease VARCHAR(100),
    risk_level VARCHAR(20),
    prediction_date DATE,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);
```