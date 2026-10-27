# 💻 Project: Web Server Infrastructure Homelab
**[GitHub Repository Name] | A Demonstration of Enterprise Backend Skills**

### 🚀 Overview & Goals
This project serves as a comprehensive, hands-on laboratory designed to model a modern, robust three-tier web architecture: **Client $\rightarrow$ Web/API Gateway $\rightarrow$ Application Logic $\rightarrow$ Database**. The lab was built incrementally, moving from foundational networking concepts up through secure database integration and operational process management.

The goal of this repository is to provide tangible, documented proof of capability across critical IT & Engineering domains: Linux System Administration (Ubuntu Server), Microservice Design (Flask/Python API), Complex Network Configuration (Nginx Proxying), and Secure Data Access (PostgreSQL).

### 🏗️ Architecture Diagram & Components
| Component | Technology | IP Address | Role | Key Skills Demonstrated |
| :--- | :--- | :--- | :--- | :--- |
| **Client** | Windows / Web Browser | N/A | User Interface Layer | HTTP Protocol Understanding, Client Interaction. |
| **WEB01** | Linux (Ubuntu Server) & Nginx | `192.168.10.20` | **Web Gateway / Reverse Proxy:** Handles incoming client requests and proxies API traffic (`/api/*`) to the backend. | Reverse Proxies, HTTP Header Manipulation, Load Balancing Concepts. |
| **APP01** | Linux (Ubuntu Server) & Flask/Python | `192.168.10.30` | **Application Backend:** Contains business logic and is managed as a reliable system service. | Python Development, REST API Creation, Environment Virtualization (`.venv`), Secure Credential Handling (`.pgpass`). |
| **DB01** | Linux (Ubuntu Server) & PostgreSQL | `192.168.10.40` | **Data Persistence:** The single source of truth for the application data, accessed via controlled connections. | Database Administration (SQL), Network Segmentation, Principle of Least Privilege ($LOD$). |

---

## ⚙️ Operational Milestones & Proof of Work
### ⭐ Phase 1: Foundation & Networking Setup
*   **Goal:** Establish a stable, multi-VM network backbone.
*   **Skills Covered:** VirtualBox resource management, static IP configuration, basic networking diagnostics (`ping`, `systemctl status`).
*   **Status:** Completed and validated connectivity between all three isolated nodes.

### ⭐ Phase 2: Web Gateway Implementation (Nginx)
*   **Goal:** Create a publicly accessible front-end that intelligently routes traffic.
*   **Key Learning:** Mastery of the Nginx configuration syntax and using `try_files` directives to route traffic between static content (`/`) and dynamic content (`/api/*`).

### ⭐ Phase 3: Application Backend Development & Service Reliability (Daemonization)
*   **Goal:** Transitioning from manual execution to professional, resilient service management.
*   **Action:** Created a persistent `systemd` unit file on APP01 (`webapp.service`) to automatically manage Flask's lifecycle.
*   **Key Skill Demonstrated:** **Operational Engineering**. The application is now guaranteed to restart upon failure or system reboot (using `Restart=on-failure`), ensuring high availability—a critical skill for backend SRE/DevOps roles.

### ⭐ Phase 4: Data Tier Hardening (PostgreSQL/DB01)
*   **Goal:** Establish a secure and audit-proof data persistence layer on DB01.
*   **Security Highlights:**
    *   **Least Privilege Principle (LOD):** Created dedicated, non-admin roles using custom users for the application (`homelab_app`).
    *   **Network Binding by IP:** Restricted PostgreSQL to listen *only* on the lab's private IP (`192.168.10.40`), providing defense-in-depth against local loopback attacks (The `listen_addresses` setting).
    *   **Secure Credential Management:** Employed the native **`.pgpass`** file mechanism for passwordless, secure client authentication, demonstrating expertise in handling sensitive information.

### 🔥 Phase 5: Full Stack Integration & Resilience Testing (The Capstone)
*   **Goal:** Link all components into a seamless, reliable system endpoint-to-endpoint.
*   **Process Synergy:** Integrated the database connectivity by modifying the Flask API to include `/api/database-health`. This required coordinating changes across Nginx (proxying), Flask (connection credentials), and PostgreSQL (user permissions).
*   **Validation:** The successful response (HTTP 200 OK) validated that a request travels seamlessly from client $\rightarrow$ WEB01 $\rightarrow$ APP01 $\rightarrow$ DB01, confirming the entire stack is stable and production-ready.

***
<img width="958" height="938" alt="final screenshot conection" src="https://github.com/user-attachments/assets/5a45e807-d019-4649-9be5-a97e3526ab49" />
<img width="960" height="933" alt="final-screenshot-daemon-running" src="https://github.com/user-attachments/assets/ba307036-58ae-4115-8e24-366919c2dc68" />
<img width="1269" height="885" alt="final-screenshot-nano-daemon" src="https://github.com/user-attachments/assets/90b98e91-f1ab-4fec-aad2-fa4de140716c" />
