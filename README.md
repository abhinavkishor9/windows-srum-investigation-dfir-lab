# windows-srum-investigation-dfir-lab
## Overview

The System Resource Usage Monitor (SRUM) database is one of the most valuable Windows forensic artifacts available to DFIR analysts. It records historical system activity including application execution, network usage, energy consumption, and resource utilization.

Unlike volatile artifacts, SRUM provides historical evidence that helps investigators reconstruct user behavior over time, making it particularly useful during incident response, insider threat investigations, and post-compromise analysis.

This lab demonstrates the forensic acquisition of the SRUM database while preserving evidence integrity through cryptographic hashing.

---

# Executive Summary

During this investigation, a forensic copy of the Windows SRUM database (SRUDB.dat) was acquired from the protected System32 directory without modifying the original evidence.

The copied database was validated using SHA256 hashing to ensure integrity prior to analysis. The investigation demonstrates proper forensic evidence handling practices and highlights how SRUM artifacts can support user activity reconstruction during DFIR investigations.

---

# Lab Objectives

- Understand the purpose of SRUM
- Locate the Windows SRUM database
- Acquire forensic evidence safely
- Preserve evidence integrity
- Calculate SHA256 hash
- Document acquisition workflow
- Prepare evidence for offline forensic analysis

---

# Skills Demonstrated

- Windows DFIR
- Evidence Acquisition
- Evidence Preservation
- File Integrity Validation
- SHA256 Hash Verification
- Windows System Artifact Analysis
- Windows Forensic Artifact Identification
- Timeline Preparation
- Incident Documentation
- Digital Evidence Handling
- Chain of Custody Awareness

---

# Tools Used

- Windows 10 VM
- PowerShell
- File Explorer
- Get-FileHash
- Windows System32
- SRUM Database

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Windows 10 x64 |
| Virtualization | VMware Workstation Player |
| Shell | Windows PowerShell |
| Artifact | SRUDB.dat |
| Hash Algorithm | SHA256 |
| Investigation Folder | C:\SRUMLab |

---

# MITRE ATT&CK Mapping

| Technique | ID |
|-----------|----|
| Indicator Removal on Host (attempted evidence deletion) | T1070 |
| File and Directory Discovery | T1083 |
| System Information Discovery | T1082 |
| Network Service Discovery (historical via SRUM) | T1046 |
| Application Layer Protocol Activity (historical evidence) | T1071 |

> **Note:** SRUM is a forensic artifact and does not represent malicious activity itself. It provides historical evidence that supports investigations into ATT&CK techniques.

---

# Evidence Collected

- SRUDB.dat
- SHA256 Hash
- File Explorer evidence
- PowerShell acquisition commands
- Investigation screenshots

---

# Evidence Correlation

The investigation correlated multiple sources of evidence:

- Original SRUM database location under `C:\Windows\System32\sru`
- Forensic copy stored in the investigation workspace
- SHA256 hash confirming acquisition integrity
- PowerShell acquisition logs
- Windows Explorer screenshots validating artifact location

Together, these artifacts establish a verifiable acquisition process suitable for DFIR documentation.

---

# Investigation Findings

- Successfully identified the SRUM database.
- Created a forensic working copy without altering the original database.
- Verified evidence integrity using SHA256 hashing.
- Confirmed that the copied artifact was ready for offline forensic parsing with specialized tools.
- Demonstrated proper evidence handling procedures consistent with DFIR best practices.

---

# Key Takeaway

SRUM is one of the most valuable Windows forensic artifacts because it preserves historical system activity that often survives reboots. Proper acquisition and integrity verification are essential to ensure the evidence remains admissible and trustworthy for further forensic analysis.
