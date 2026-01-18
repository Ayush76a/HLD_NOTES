Perfect. Here is the **ultra-brief, interview-revision version**.
This is what you revise **10 minutes before interview**.

---

# ⚡ SYSTEM DESIGN — ULTRA BRIEF NOTES

---

## Monolithic vs Microservices

* **Monolith**: single codebase, easy to build, hard to scale
* **Microservices**: independent services, hard to build, easy to scale
* **Critical**: companies start monolith → migrate later

---

## Stateful vs Stateless

* **Stateful**: server stores session → hard to scale
* **Stateless**: no session on server → easy to scale
* **Critical**: stateless preferred for distributed systems

---

## REST

* REST is **stateless by design**
* Each request must carry all info
* Server must not remember client

---

## Redis

* In-memory key–value store
* Used for: cache, session, rate limit
* **Not a primary database**
* **Critical**: improves performance, not features

---

## Load Balancer Layers

* **L4**: TCP/UDP, IP + port, very fast
* **L7**: HTTP aware, routes by URL/header
* **Critical**: L4 = connections, L7 = requests

---

## Kafka

* Distributed event streaming platform
* Used for async communication
* Stores events, supports replay
* **Critical**: Kafka ≠ database, Kafka ≠ simple queue

---

## Hadoop

* Distributed storage + batch processing
* Used for huge offline analytics
* Slow but scalable
* **Not for real-time or APIs**

---

## Spark Streaming

* Near real-time processing
* Uses micro-batches
* Usually consumes data from Kafka
* **Critical**: Kafka moves data, Spark processes it

---

# 🔥 MUST-REMEMBER LINES

* Monolith easy, microservices scalable
* REST is stateless
* Redis = performance layer
* L4 balances connections, L7 balances requests
* Kafka = event log
* Hadoop = batch analytics
* Spark = stream processing

