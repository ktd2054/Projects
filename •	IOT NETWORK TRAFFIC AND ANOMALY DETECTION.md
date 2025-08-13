
# IoT Network Traffic and Anomaly Detection
This project designs, simulates, and evaluates a lightweight intrusion detection framework for Internet of Things (IoT) networks using Contiki-NG and the COOJA simulator. It focuses on real-time anomaly detection in resource-constrained environments such as smart homes, healthcare, and industrial IoT.

## Key Features

- Simulated IoT Environment: Modeled normal, malicious, and sink nodes to represent real-world devices, attack nodes (DoS, spoofing), and monitoring gateways.

- Hybrid Detection Approach: Combined statistical thresholds with lightweight machine learning algorithms to identify abnormal traffic patterns while minimizing false positives.

- Threat Modeling: Applied STRIDE and DREAD methodologies to analyze potential vulnerabilities and prioritize mitigations.

- Security Countermeasures: Proposed AES-CCM encryption, DTLS authentication, DoS rate limiting, and secure logging.

- Scalability & Efficiency: Designed to operate under low computational cost and memory footprint for large IoT deployments.

## Implementation Highlights

- Developed C-based applications for UDP clients, sink anomaly detectors, and attack nodes.

- Configured packet transmission intervals to simulate normal and attack scenarios.

- Real-time logging and alerts triggered upon threshold breaches.

- Visualized network topology, timelines, and packet behavior via COOJA’s monitoring tools.
