# Investigation Notes

## Investigation Details

**Lab Name:** Windows SRUM Investigation

**Platform:** Windows 10

**Investigation Type:** Windows DFIR

**Artifact:** SRUDB.dat

---

# Lab Summary

The objective of this investigation was to safely acquire the Windows System Resource Usage Monitor (SRUM) database while preserving forensic integrity. The artifact was copied into a dedicated investigation directory and validated using SHA256 hashing before analysis.

---

# Analyst Methodology

The investigation followed a structured DFIR workflow:

1. Created a dedicated investigation workspace.
2. Located the protected SRUM database within the Windows system directory.
3. Copied the database to the investigation folder without modifying the original artifact.
4. Calculated the SHA256 hash of the copied database to preserve evidence integrity.
5. Documented acquisition steps and screenshots.
6. Prepared the evidence for future offline forensic parsing.

---

# Evidence Acquired

## Original Database

```
C:\Windows\System32\sru\SRUDB.dat
```

---

## Working Copy

```
C:\SRUMLab\SRUDB_Copy.dat
```

---

## Evidence Integrity

SHA256 hash successfully calculated using:

```
Get-FileHash
```

---

# Investigation Steps

- Created investigation folder
- Located SRUM database
- Copied SRUDB.dat
- Calculated SHA256
- Captured screenshots
- Preserved evidence

---

# Findings

- SRUM database located successfully.
- Evidence copied without modifying the source.
- Hash generated successfully.
- Acquisition completed successfully.

---

# Analyst Observations

- The SRUM database is stored in a protected system directory and should always be copied rather than opened directly.
- SHA256 hashing confirmed the integrity of the forensic copy.
- Capturing screenshots during acquisition improves investigation documentation and reproducibility.
- The acquired database is suitable for offline analysis using dedicated SRUM parsing tools.

---

# Conclusion

The Windows SRUM database was successfully acquired and preserved using forensic best practices. Evidence integrity was validated through SHA256 hashing, ensuring the artifact is ready for further offline analysis and timeline reconstruction.
