## CAP Theorem — **Brief Notes**

### Definition

In a **distributed database**, you can guarantee **only two** of the three at the same time:

* **C – Consistency**: All nodes return the same (latest) data
* **A – Availability**: Every request gets a response (success/failure)
* **P – Partition Tolerance**: System continues despite network failures

---

### Core Rule

* **Network partitions are inevitable**
* When a partition happens → **must choose between C and A**
* **P is mandatory** in real systems

---

### What it really means

* CAP **does NOT apply** during normal operation
* CAP **ONLY applies during network failure**
* No partition → you *can* have C + A
* Partition → pick **CP** or **AP**

---

### System Types

* **CP (Consistency + Partition Tolerance)**

  * Rejects requests during partition
  * No stale data
  * Example use: banking, payments

* **AP (Availability + Partition Tolerance)**

  * Always responds
  * May return stale data
  * Example use: social media, feeds, analytics

* **CA**

  * Possible only if **no partitions**
  * Not realistic at scale

---

### Why it matters

* Forces **explicit trade-offs**
* Prevents unrealistic architecture
* Explains real DB behavior under failure
* Directly affects user experience

---

### Common Confusions (exam + interviews)

* ❌ “CAP means you only get 2 always” → **Wrong**
* ✅ You get all 3 **until a partition occurs**
* ❌ “We can avoid partitions” → **Wrong**
* ❌ “Strong consistency + 100% uptime” → **Impossible**

---

### One-line takeaway

> **During network failure, you must choose: correctness (C) or uptime (A).**
