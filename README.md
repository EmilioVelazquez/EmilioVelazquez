# Hi, I'm Emilio Velázquez 👋
### DevOps Engineer & Infrastructure Analyst

Based in **Asunción, Paraguay**, I specialize in designing, automating, and securing critical self-hosted and cloud infrastructure.

[🌐 Portfolio Website](https://gateway.cosmoslabs.work/) • [💼 LinkedIn Profile](https://linkedin.com/in/emiliovlz) • [✉️ Email Me](mailto:emilio.velazquez@cosmoslabs.work)

---

### 🚀 About Me
I'm a Systems and Infrastructure Engineer transitioning to DevOps. I have hands-on experience managing mission-critical enterprise environments, including core financial platform migrations and identity-based network access controls. I specialize in designing, automating, and securing self-hosted infrastructure using modern methodologies like GitOps, containerization, and Infrastructure as Code (IaC).

- 🔭 **Current Role**: Infrastructure Analyst at **Bolsa de Valores de Asunción** (Paraguay Stock Exchange), where I played a key technical role migrating core systems to a Nasdaq-powered trading platform.
- 🎓 **Education**: Studying Computer Engineering (*Ing. en Informática*) at **Universidad Autónoma de Asunción** (2019 – Present).
- 💬 **Ask me about**: Self-hosting, homelabs, container security, network hardening, or Zero Trust architecture.
- ⚡ **Fun Fact**: I find a well-reasoned critique far more satisfying than an unearned compliment.

---

### 🛠️ Tech Stack & Skills

| Category | Tools & Technologies |
| :--- | :--- |
| **Cloud & Virtualization** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Proxmox](https://img.shields.io/badge/Proxmox-E57000?style=flat-square&logo=proxmox&logoColor=white) ![OCI](https://img.shields.io/badge/Oracle_Cloud-F80000?style=flat-square&logo=oracle&logoColor=white) ![Azure](https://img.shields.io/badge/Azure-0089D6?style=flat-square&logo=microsoft-azure&logoColor=white) ![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazon-aws&logoColor=white) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white) |
| **Automation & CI/CD** | ![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white) ![Ansible](https://img.shields.io/badge/Ansible-EE0F0F?style=flat-square&logo=ansible&logoColor=white) ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnu-bash&logoColor=white) ![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat-square&logo=powershell&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) |
| **Networking & Security** | ![Zero Trust](https://img.shields.io/badge/Zero_Trust-000000?style=flat-square&logo=security&logoColor=white) `802.1X` `MAB` `IPSec VPN` `BGP` `OSPF` `EDR` `WAF` `IDS/IPS` |
| **Web Servers & Databases** | ![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white) ![Caddy](https://img.shields.io/badge/Caddy-00AD9F?style=flat-square&logo=caddyserver&logoColor=white) ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![MS SQL Server](https://img.shields.io/badge/MSSQL_Server-CC2927?style=flat-square&logo=microsoft-sql-server&logoColor=white) |
| **Monitoring & Home Lab** | ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white) ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white) ![Home Assistant](https://img.shields.io/badge/Home_Assistant-41BDF5?style=flat-square&logo=home-assistant&logoColor=white) |

---

### 📂 Featured Project: [Self-Hosted DevOps Portfolio](https://gateway.cosmoslabs.work/)
A highly available, secure portfolio website architected with strict security hardening and modern CI/CD GitOps practices.

#### ⚙️ Continuous Delivery Pipeline
```mermaid
graph LR
    A["GitHub Push"] --> B["GitHub Actions"]
    B --> C["Docker Build\n(Multi-stage)"]
    C --> D["GitHub\nContainer Registry (GHCR)"]
    D --> E["SSH Deploy\nto OCI"]
    E --> F["Live Site"]
    style A fill:#a6e3a1,color:#1e1e2e,stroke:#1e1e2e
    style B fill:#cba6f7,color:#1e1e2e,stroke:#1e1e2e
    style C fill:#89b4fa,color:#1e1e2e,stroke:#1e1e2e
    style D fill:#fab387,color:#1e1e2e,stroke:#1e1e2e
    style E fill:#f5c2e7,color:#1e1e2e,stroke:#1e1e2e
    style F fill:#94e2d5,color:#1e1e2e,stroke:#1e1e2e
```

#### 🌐 Deployment Topology
```mermaid
graph TB
    User["Visitor"]

    subgraph CF_Edge["Cloudflare Edge"]
        WAF["WAF & DNS"]
    end

    subgraph OCI["Oracle Cloud Infrastructure (OCI)"]
        FW["OCI Firewall\n(Ingress: Port 443 Only)"]
        subgraph Docker_Net["Docker Network: web-bridge"]
            CADDY["Caddy Reverse Proxy\n(Ports 80 / 443)"]
            NGINX["Nginx Container\n(Frontend Site)"]
            PROXY["contact-proxy\n(Go Sidecar - Port 3000)"]
        end
    end

    subgraph Home_Lab["Home Proxmox"]
        NTFY["ntfy Container\n(Self-hosted Server)"]
    end

    Phone["Mobile Device"]

    User -->|HTTPS: 443| WAF
    WAF -->|Proxy Traffic| FW
    FW -->|Forward to Host| CADDY

    CADDY -->|Route Static Assets| NGINX
    CADDY -->|Route /api/contact| PROXY

    PROXY -->|POST Request via Private VPN| NTFY
    NTFY -->|Push Notification| Phone

    style User fill:#a6e3a1,color:#1e1e2e,stroke:#1e1e2e
    style WAF fill:#fab387,color:#1e1e2e,stroke:#1e1e2e
    style FW fill:#f38ba8,color:#1e1e2e,stroke:#1e1e2e
    style CADDY fill:#74c7ec,color:#1e1e2e,stroke:#1e1e2e
    style NGINX fill:#89b4fa,color:#1e1e2e,stroke:#1e1e2e
    style PROXY fill:#a6e3a1,color:#1e1e2e,stroke:#1e1e2e
    style NTFY fill:#cba6f7,color:#1e1e2e,stroke:#1e1e2e
    style Phone fill:#f5c2e7,color:#1e1e2e,stroke:#1e1e2e

    style CF_Edge fill:#1e1e2e,stroke:#fab387,stroke-dasharray: 5 5,color:#cdd6f4
    style OCI fill:#181825,stroke:#94e2d5,color:#cdd6f4
    style Docker_Net fill:#11111b,stroke:#a6adc8,stroke-dasharray: 3 3,color:#a6adc8
    style Home_Lab fill:#1e1e2e,stroke:#f5c2e7,color:#cdd6f4

    linkStyle default stroke:#cba6f7,stroke-width:2px;
```

#### 🔒 Security Architecture
* **Container Hardening**: Frontend is powered by `nginx:alpine` (~25MB) and the Go backend sidecar `contact-proxy` (~8MB) runs on `distroless/static` with non-root execution and read-only filesystems.
* **Network Defense**: Strictly restricted OCI security list, Cloudflare Proxy (DDoS protection), Strict Content Security Policy (CSP), HTTP Strict Transport Security (HSTS), 3-layer rate limiting (10 req/min), and honeypot validation for spam defense.

---

### 💼 Professional Experience

#### **Infrastructure Analyst** @ Bolsa de Valores de Asunción *(2025 - Present)*
* Played a key technical role in the migration of the organization's core systems to a **Nasdaq-powered trading platform**.
* Architected and implemented a dynamic identity-based **Network Access Control (NAC)** system utilizing **802.1X** and **MAB** protocols.
* Migrated legacy systems to modern virtualized infrastructure using **Docker containerization** across hybrid environments.
* Designed and implemented automated **CI/CD pipelines** to streamline deployment processes.
* Administered IPSec VPNs, firewall policies, and network segmentation following **Zero Trust principles**.
* Deployed and managed **monitoring and alerting solutions** to ensure high availability and performance of critical systems.

#### **IT Coordinator** @ Club Centenario *(2023 - 2025)*
* Deployed and administered centralized security solutions including **EDR, WAF, and IDS/IPS systems**.
* Managed complex networks and oversaw the end-to-end lifecycle of internal IT infrastructure (150+ endpoints).
* Implemented automated backup and disaster recovery procedures ensuring business continuity.
* Administered relational databases and maintained continuous monitoring and alerting systems.

#### **IT Assistant** @ Club Centenario *(2021 - 2022)*
* Performed critical corrective and preventive hardware maintenance.
* Provided comprehensive Tier-1 support for organizational staff.

---

### 🏆 Credentials & Certifications
* **EF SET Certificate (C2 Proficient)** — Issued by EF SET (April 2025)
* **Microsoft Certified: Security, Compliance, and Identity Fundamentals** (October 2024)
* **Microsoft Certified: Azure Fundamentals** (August 2024)

---
<!-- Proudly created with love and refined manually -->
