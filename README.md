# Midas
Project repo for the JPMC Advanced Software Engineering Forage program

Midas Core – Transaction Processing Service
Overview

Midas Core is a Spring Boot microservice that simulates a high-volume transaction processing system, integrating Kafka messaging, REST APIs, and a relational database. This project was completed as part of the JPMorgan Chase & Co Advanced Software Engineering Virtual Experience Program.

It demonstrates handling transactions, applying incentives from an external API, and exposing user balance data via a REST endpoint.

Features

Kafka Consumer: Consumes transaction messages from a configurable Kafka topic.

Transaction Validation: Validates transactions and updates sender and recipient balances.

External Incentive API Integration: Posts validated transactions to an Incentive API and applies incentive amounts to recipient balances.

REST API Controller: Provides a /balance endpoint to query user balances by userId.

Persistence Layer: Uses Spring Data JPA with H2 database to store users and transactions.

Debuggable Workflow: Includes checkpoints for inspecting balances during execution.

Tech Stack

Java 17

Spring Boot

Spring Data JPA

Kafka (Spring Kafka)

H2 Database

REST API (Spring Web)

Maven

Project Structure
src/main/java
├── com.jpmc.midascore
│   ├── config          # RestTemplate Bean configuration
│   ├── controller      # REST API controllers
│   ├── entity          # JPA entities (UserRecord, TransactionRecord)
│   ├── kafka           # Kafka listeners for transaction messages
│   └── repository      # Spring Data JPA repositories

How to Run

Clone the repository:

git clone <your-repo-url>
cd <repo-folder>


Start Kafka (if testing Kafka integration) and the Incentive API JAR:

java -jar services/incentive-api.jar


Build and run the service:

mvn clean install
mvn spring-boot:run


Query user balances via REST API:

GET http://localhost:33400/balance?userId=<id>

Key Accomplishments

Integrated Kafka messaging with Spring Boot for high-throughput transaction ingestion.

Implemented end-to-end transaction workflows, including external incentive processing.

Developed a REST API to expose user balances while maintaining architectural boundaries.

Verified system behavior using Maven tests and debugger-driven inspection.

Notes

Default database is H2 (in-memory).

Incentive API must be running for incentive calculations to be applied.

Balances are stored as floats and updated atomically per transaction.

License

This project is for educational purposes only and was completed as part of the Forage virtual experience program. It is not intended for commercial use.
