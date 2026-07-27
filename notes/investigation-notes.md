# Investigation Notes

## Lab Summary

**Objective:**

Investigate Windows **System Resource Usage Monitor (SRUM)** artifacts to understand how Windows records application execution and system resource usage, preserve the SRU database, verify evidence integrity, and document findings using native Windows tools.

---

## Analyst Methodology

The investigation followed a standard host-based DFIR methodology:

1. Prepare a controlled investigation environment.
2. Generate sample user activity.
3. Locate the SRUM database.
4. Preserve forensic evidence.
5. Verify evidence integrity.
6. Examine SRUM artifacts.
7. Correlate collected evidence.
8. Document investigation findings.
9. Produce an investigation timeline.

---

## Investigation Steps

### Step 1

Created the investigation workspace.

**Evidence:**

- `C:\SRUMLab`
- `Reports` directory

---

### Step 2

Created sample files inside the Reports folder.

**Evidence:**

- Finance.xlsx
- Employees.txt
- IncidentReport.docx

---

### Step 3

Generated user activity.

**Actions performed:**

- Created files
- Accessed files
- Navigated through Windows Explorer

**Observation:**

Windows generated system activity that would later be recorded within the SRUM database.

---

### Step 4

Located the SRUM database.

**Path:**

```text
C:\Windows\System32\sru\
```

**Observed artifacts:**

- SRUDB.dat
- SRU.chk
- SRU.log files
- SRU.jfm
- SRU transaction logs

---

### Step 5

Preserved the primary forensic artifact.

**Action:**

Copied:

```text
SRUDB.dat
```

to

```text
C:\SRUMLab\SRUDB_Copy.dat
```

This ensured the original database remained untouched during analysis.

---

### Step 6

Calculated the SHA256 hash of the preserved database.

**Command used:**

```powershell
Get-FileHash C:\SRUMLab\SRUDB_Copy.dat
```

**Observation:**

A SHA256 hash value was successfully generated, confirming evidence integrity.

---

### Step 7

Examined the SRUM directory contents.

**Observed evidence:**

- SRU database
- Transaction log files
- Recovery files
- JFM file
- Temporary database components

---

### Step 8

Correlated evidence.

| Evidence | Purpose |
|-----------|---------|
| SRUDB.dat | Primary SRUM database |
| SHA256 Hash | Evidence integrity verification |
| Transaction Logs | Database consistency and recovery |
| Sample Files | Simulated user activity |

---

## Evidence Summary

Collected:

- PowerShell outputs
- SRUM directory screenshots
- SRUDB.dat copy
- SHA256 hash
- Investigation workspace
- Sample activity files

---

## Analyst Observations

The investigation demonstrated that:

- Windows stores resource usage information within the **SRUDB.dat** database.
- Preserving the database before analysis maintains forensic integrity.
- Computing a SHA256 hash provides a reliable method for validating evidence integrity.
- Transaction logs accompany the SRUM database and support recovery and consistency operations.
- Even without specialized forensic software, investigators can successfully locate, preserve, and validate SRUM artifacts using native Windows tools.

---

## Conclusion

The investigation successfully demonstrated Windows **System Resource Usage Monitor (SRUM)** artifact acquisition by locating the SRUM database, preserving a forensic copy, validating evidence integrity through SHA256 hashing, and documenting the collected artifacts using native Windows utilities. This workflow represents a foundational DFIR process for safely handling SRUM evidence prior to advanced forensic analysis.
