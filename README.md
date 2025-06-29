# 🚀 JetQueue

## Overview

**JetQueue** is a high-performance, modular, distributed messaging queue built from the ground up in **pure Java**, with no external dependencies (except for testing). Inspired by Apache Kafka, JetQueue is designed to deliver faster, more predictable performance with architectural clarity, strict adherence to SOLID principles, and extensibility as a first-class concern.

The project is organized by **domain-driven modules** (e.g., core, server, storage, cluster) and is structured for long-term maintainability and evolution into a fully distributed system.

---

## 🧱 Core Principles

- **Modular Design** – Each module encapsulates a bounded context (e.g., server, storage, client, cluster)
- **Pure Java** – No external libraries for runtime dependencies (except JUnit/TestNG for testing)
- **SOLID Compliant** – Separation of concerns, dependency inversion, and single responsibility maintained throughout
- **Domain-Driven** – Messaging, partitioning, logs, replication, and cluster logic are modeled explicitly
- **Extensible Protocol** – All communication follows a versioned, type-safe binary protocol

---

## 💡 Use Cases

- Internal system-to-system communication
- Event-driven microservices architecture
- Log aggregation and processing
- Queueing with ordering guarantees
- Lightweight Kafka alternative with full control over source code

---

## 📦 Key MVP Features

1. **Topics & Partitions**
    - Each topic can be sharded into multiple partitions
    - Partitions are individually ordered, append-only logs

2. **Message Structure**
    - Message contains offset, payload (bytes), timestamp
    - TTL and future metadata fields supported

3. **Offset-based Consumption**
    - Consumers read messages from specific offsets
    - Designed for at-least-once delivery guarantees

4. **Persistent Storage**
    - Append-only commit log per partition
    - Segment-based file handling with rollover
    - Durable restart and crash recovery

5. **TTL & DLQ Support**
    - Configurable TTL per topic
    - Expired messages skipped or purged
    - DLQ logic scaffolded for future release

6. **CLI Testing Clients**
    - Produce and consume via command-line interface
    - Simulates real-world usage before networking is added

---

## 🔁 Planned Future Features

- Clustered brokers with leader election and replication
- Gossip-based or Raft-based discovery and metadata propagation
- Consumer groups with offset tracking and rebalancing
- Asynchronous follower replication for fault tolerance
- REST-based admin and monitoring APIs
- Protocol-level compression, batching, and schema validation

---

## 📁 Architecture

- `jetqueue-core`: Domain model (Message, Partition, Topic, Offset)
- `jetqueue-server`: Broker runtime, topic manager, and producer/consumer API
- `jetqueue-storage`: Append-only logs, file segments, disk persistence
- `jetqueue-client`: Client-facing protocol and interfaces
- `jetqueue-cluster`: Future cluster coordination (discovery, replication)
- `jetqueue-common`: Utilities, exceptions, and config handling
- `jetqueue-cli`: Developer CLI for local testing
- `jetqueue-test`: Unit and integration test suite

---

## 🛠️ Built With

- **Java 17+** (no external libraries except for tests)
- **Clean Architecture Principles**
- **Modular Project Layout** (ideal for microkernel or plugin design)
- **Manual Testing CLI** (prior to network protocol implementation)

---

## 🧪 Current Status: MVP In Progress

JetQueue is currently in active development. The MVP focuses on single-node capabilities:
- Topic/Partition management
- Durable message append/read
- CLI-based message flow
- TTL and recovery logic

Once MVP is stable, the project will evolve into a full-fledged distributed messaging platform.
