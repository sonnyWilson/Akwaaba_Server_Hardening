# Akwaaba Steakhouse Server Hardening Project

An enterprise cybersecurity server hardening and risk mitigation project for **Akwaaba Steakhouse** (headquarters and store locations in New York City, Atlanta, and Los Angeles). This repository contains the complete security documentation, LaTeX source files, configurations, and automated hardening scripts for securing a Red Hat Enterprise Linux (RHEL 8.4) infrastructure stack running Apache, MariaDB, and WordPress.

## Project Overview

This project follows a multi-phase cybersecurity lifecycle to secure Akwaaba Steakhouse’s e-commerce and point-of-sale (POS) server environment:

1. **Draft 1 – Risk Assessment & Baseline Policy:** Overall infrastructure evaluation, asset identification (digital and personnel), threat modeling, and a NIST SP 800-30 Rev. 1 risk assessment matrix.
2. **Draft 2 – Security Program Plan & Mitigation:** Development of a comprehensive Information Security Policy (ISP), Role-Based Access Control (RBAC) matrix, POSIX File ACL rules, and a targeted vulnerability mitigation roadmap.
3. **Final Implementation & Report:** Execution of server hardening scripts, DISA STIG compliance checks, Multi-Factor Authentication (MFA) deployment, and before-and-after screenshot validation.

##  Team Information

* **Institution:** Kennesaw State University
* **Course:** IT 4883 / IT 6823 Infrastructure Defense
* **Team Members:**
  * Sonny Wilson (System Admin Lead)
  * Nicholas Coats
  * Axel Palacios
  * Jc Sparks

## Infrastructure Stack Specifications

* **Operating System:** Red Hat Enterprise Linux (RHEL) 8.4
* **Web Server:** Apache HTTP Server 2.4.37
* **Database Engine:** MariaDB 10.6.4
* **CMS Application:** WordPress (`/var/www/html/home`)
* **Remote Management:** SSH (Port 22) secured via GlobalProtect VPN (`vpn.kennesaw.edu`)

## Repository Structure

```text
├── docs/
│   ├── Phase_1_Report.tex            # Full Phase 1 LaTeX source file
│   ├── Phase_1_Report.pdf            # Compiled Phase 1 PDF report
│   ├── Phase_2_Mitigation_Plan.md    # Vulnerability mitigation roadmap
│   └── screenshots/                  # Before/After terminal & UI evidence
├── hardening/
│   ├── os_hardening.sh               # RHEL 8.4 firewall & SSH hardening scripts
│   ├── web_acl_hardening.sh          # POSIX ACL and directory permission scripts
│   └── db_hardening.sql              # MariaDB user isolation & binding scripts
├── README.md                         # Repository documentation
└── .gitignore                        # Git ignore rules for LaTeX build artifacts
