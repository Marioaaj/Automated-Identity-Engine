# Automated Identity Lifecycle Engine (IAM)
<img width="1298" height="540" alt="Automated-Identity-Engine" src="https://github.com/user-attachments/assets/a437d128-3503-4b87-a877-a24a5329eb43" />
## 📋 Project Overview
This project is a containerized automation solution developed in **n8n** to streamline the employee onboarding lifecycle. It automates the transition from raw HR input to system-ready digital identities, enforcing corporate standards and security protocols automatically.

## 🛠️ Tech Stack
* **Automation Platform:** n8n (Self-hosted via Docker)
* **Runtime Environment:** Hardened Alpine Linux
* **Logic & Scripting:** JavaScript (Node.js)

* **Architecture:** Event-driven JSON Batch Processing

## 🚀 Key Features
* **Hardened Environment Compatibility:** Engineered to run within restricted Docker images where external package managers and runtimes (like Python) are stripped for security.
* **Standardized Identity Generation:** Automatically generates sanitized corporate emails for the `practice-demo.com` domain.
* **Role-Based Access Control (RBAC):** Integrated a **Switch-based Decision Engine** to route users to specific licensing tiers (M365 E5 vs. E3) and security groups based on department metadata.
* **High-Volume Scaling:** Built to handle bulk JSON payloads, allowing for simultaneous onboarding of multiple employees without manual intervention.

## 🧠 Technical Challenge & Resolution
**The Problem:** During deployment, the target environment was identified as a **Hardened Alpine Linux** container. This environment lacked the Python 3 runtime and restricted the use of `apk` or `apt` for security hardening.

**The Solution:** I performed an environment audit using `/etc/os-release` and pivoted the business logic from Python to **Native JavaScript**. This ensured 100% logic parity while maintaining the high security posture of the host container.

## 📂 How to Use
1. Import the `identity-engine-v1.json` file into your n8n instance.
2. Trigger the workflow manually or via Webhook.
3. The engine will process the input and route users to the appropriate provisioning path.
