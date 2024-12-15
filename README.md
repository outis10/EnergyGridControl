# SmartGrid Monitor

SmartGrid Monitor is a distributed system designed to monitor smart grids in real-time. It leverages microservices built with Spring Boot, Kafka, and JPA to process sensor data, detect anomalies, and generate alerts that help optimize the operation of the power grid.

## Key Features

1. **Real-time monitoring:** Processes sensor readings sent from distributed stations.
2. **Alert generation:** Detects anomalies such as overloads, voltage drops, or frequency imbalances.
3. **Alert management:** Tracks active alerts and their resolution.
4. **Historical analysis:** Provides metrics and historical data to optimize grid performance.

---

## General Architecture

### Key Technologies:
- **Java 17**
- **Spring Boot**
- **Apache Kafka** (for real-time data ingestion and distribution)
- **PostgreSQL** (as the relational database)
- **Docker** (for containerization)
- **Prometheus/Grafana** (for monitoring and visualization)

### Initial Microservices:
1. **Data Ingestion Service:** Consumes sensor data from Kafka and persists it.
2. **Alert Management Service:** Processes data to generate alerts in case of anomalies.
3. **Metrics Query Service:** Provides historical metrics and statistics.
4. **API Gateway:** Exposes a single entry point for API consumers.

---

## Project Structure

```plaintext
smartgrid-monitor/
├── data-ingestion-service/      # Microservice for data ingestion
├── alert-management-service/    # Microservice for alert management
├── metrics-query-service/       # Microservice for historical queries
├── api-gateway/                 # System entry gateway
├── kafka/                       # Apache Kafka configuration
├── docker-compose.yml           # Docker containers configuration
└── README.md                    # Project documentation
```

---

## Installation and Setup

### Prerequisites
1. **Java 17** and **Maven** installed.
2. **Docker** and **Docker Compose** configured.
3. **Apache Kafka** available locally or remotely.
4. PostgreSQL as the relational database.

### Installation Steps
1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/smartgrid-monitor.git
   cd smartgrid-monitor
   ```
2. Configure environment variables for each microservice. Example:
   ```plaintext
   SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/smartgrid
   SPRING_DATASOURCE_USERNAME=username
   SPRING_DATASOURCE_PASSWORD=password
   KAFKA_BOOTSTRAP_SERVERS=localhost:9092
   ```
3. Start the services with Docker Compose:
   ```bash
   docker-compose up
   ```

---

## Task List by Microservice

### **1. Data Ingestion Service**
- [ ] Configure Kafka connection to consume sensor data.
- [ ] Create a `SensorReading` entity and persist data in PostgreSQL.
- [ ] Implement data validation (e.g., voltage range checks).
- [ ] Simulate data producers to generate random sensor readings:
  - [ ] Create standalone applications that publish random data to Kafka topics.
  - [ ] Include metadata such as timestamp, sensor ID, voltage, and frequency.
- [ ] Expose a REST endpoint for manual data submission (for testing purposes).
- [ ] Configure unit tests with JUnit.

### **2. Alert Management Service**
- [ ] Create anomaly detection logic (e.g., overload, voltage drop).
- [ ] Define `Alert` entity and persist it in the database.
- [ ] Configure notifications to a Kafka topic (e.g., `alerts-topic`).
- [ ] Expose a REST endpoint to query active alerts.
- [ ] Configure integration tests with Kafka.

### **3. Metrics Query Service**
- [ ] Implement queries to fetch historical metrics (e.g., average load).
- [ ] Expose REST endpoints for:
  - [ ] Metrics by station.
  - [ ] Alert history.
- [ ] Implement pagination for large datasets.
- [ ] Optimize SQL queries with PostgreSQL indexes.

### **4. API Gateway**
- [ ] Configure a gateway using Spring Cloud Gateway or similar.
- [ ] Define routes to redirect traffic to the microservices.
- [ ] Implement basic authentication or JWT.
- [ ] Configure metrics for the gateway (e.g., response time).

---

## Roadmap
1. **Phase 1:** Set up basic services and Kafka communication.
2. **Phase 2:** Add business rules for anomaly detection.
3. **Phase 3:** Integrate monitoring with Prometheus and visualization with Grafana.
4. **Phase 4:** Scale the system to handle thousands of simultaneous readings.

---

## Contributions
Contributions are welcome. Open an issue or a pull request to suggest changes or add new features.

---

## License
This project is licensed under the [MIT License](LICENSE).
