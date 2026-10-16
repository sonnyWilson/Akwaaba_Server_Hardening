# Akwaaba Steakhouse Phase 2: Vulnerability Mitigation Roadmap

## 1. Overview
This document outlines the vulnerability mitigation plan for the Akwaaba Steakhouse server environment (RHEL 8.4, Apache, MariaDB, WordPress) in accordance with NIST SP 800-30 Rev. 1 guidelines.

## 2. Risk Mitigation Roadmap

| Risk ID | Asset / Target | Identified Threat & Vulnerability | Target Hardening Tool / Script | Planned Remediation Strategy | Priority |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **R-01** | **MariaDB Database** | Database exposure & SQLi via default configurations listening on `0.0.0.0`. | `db_hardening.sql` | Bind MariaDB strictly to `127.0.0.1`, remove test DBs, enforce strong app passwords. | **High** |
| **R-02** | **Web Application (`/wp-admin`)** | Brute-force credential stuffing exploiting static default credentials (`Kennesaw123!`). | `web_acl_hardening.sh` / WP Plugin | Deploy login rate-limiting, mandate 14+ char complex passphrases, enable MFA. | **High** |
| **R-03** | **RHEL 8.4 OS / File System** | Local privilege escalation via world-readable `wp-config.php` (`644`). | `web_acl_hardening.sh` | Enforce `chmod 600` on `wp-config.php` and `750/640` permissions on web root. | **High** |
| **R-04** | **SSH Management (Port 22)** | Public SSH exposure allowing remote brute-force attacks. | `os_hardening.sh` | Restrict Port 22 to GlobalProtect VPN subnets via FirewallD rich rules and disable root SSH login. | **Moderate** |
| **R-05** | **Apache Web Stack** | Information disclosure via Apache version banners and missing security headers. | `web_acl_hardening.sh` | Apply `ServerTokens Prod` and enforce X-Frame-Options and X-XSS-Protection response headers. | **Moderate** |

## 3. Verification & Evidence Collection
All mitigations are verified by executing automated testing scripts (`/tests`) before and after running hardening scripts (`/hardening`). Terminal output logs and web UI screenshots are stored in `docs/screenshots/` for Final Report submission.