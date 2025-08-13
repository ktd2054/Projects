# IoT Traffic Monitoring and Anomaly Detection

##  Project Overview
This project implements an **IoT network traffic monitoring and anomaly detection system** using **Contiki-NG** and the **COOJA simulator**.  
Unlike traditional signature-based Intrusion Detection Systems (IDS), this solution combines **rule-based thresholds** with **lightweight machine learning** to detect unusual network activity in real time.

The simulated environment models:
- **Normal Nodes** – Send regular sensor data
- **Attack Nodes** – Simulate malicious activity (e.g., DoS, spoofing)
- **Sink Node** – Aggregates all traffic and performs anomaly detection

The system is designed for **scalability, low computational cost, and deployability** in real-world IoT scenarios such as **smart cities, healthcare, and industrial IoT**.

---

## Key Features
- **Hybrid Detection Model** – Combines statistical thresholds with ML-based anomaly detection  
- **Simulated Real-world Attacks** – DoS and spoofing traffic patterns for testing  
- **STRIDE & DREAD Threat Modelling** – Identifies security risks and prioritizes mitigations  
- **Lightweight & Low-power** – Suitable for constrained IoT devices  
- **Modular Architecture** – Easily extendable for multiple IoT protocols (MQTT, CoAP, etc.)

---

## System Architecture
**Components:**
1. **UDP Client Nodes** – Send periodic data packets  
2. **Attack Nodes** – Flood network with abnormal traffic  
3. **Sink Node (Anomaly Detector)** – Monitors traffic, detects anomalies, triggers alerts  

**Data Flow:**
1. Sensor & attack nodes send UDP packets  
2. Sink node analyzes traffic using defined thresholds & detection logic  
3. Alerts are generated when abnormal behavior is detected  

---

## Technologies & Tools
- **Contiki-NG** – Lightweight OS for IoT devices  
- **COOJA Simulator** – Simulates IoT network and motes  
- **C Programming** – Custom anomaly detection logic  
- **Threat Models** – STRIDE, DREAD  
- **Security Enhancements** – AES-CCM encryption, DTLS authentication, rate limiting

---

## Results
- Successfully detected **high-frequency flooding attacks** in simulated IoT environments  
- Reduced **false positives** compared to traditional IDS  
- Validated **real-time detection capability** for constrained devices  
