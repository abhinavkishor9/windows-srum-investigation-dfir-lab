# Troubleshooting Notes

## Issue 1

Unable to locate the SRUM database.

### Cause

Incorrect directory path or hidden system files not visible.

### Resolution

Navigate to:

```text
C:\Windows\System32\sru
```

or verify using:

```powershell
Get-ChildItem "C:\Windows\System32\sru"
```

---

## Issue 2

Access denied while copying **SRUDB.dat**.

### Cause

Insufficient permissions or the database was in use.

### Resolution

Run PowerShell as **Administrator** before copying the database.

---

## Issue 3

SRUDB.dat not found.

### Cause

The SRUM service had not yet created the database or the wrong path was used.

### Resolution

Generate normal Windows activity, then verify the folder contents:

```powershell
Get-ChildItem "C:\Windows\System32\sru"
```

---

## Issue 4

Unable to copy the SRUM database.

### Cause

Incorrect destination path or missing investigation folder.

### Resolution

Create the investigation folder first:

```powershell
mkdir C:\SRUMLab
```

Then copy:

```powershell
Copy-Item "C:\Windows\System32\sru\SRUDB.dat" "C:\SRUMLab\SRUDB_Copy.dat"
```

---

## Issue 5

SHA256 hash could not be generated.

### Cause

Incorrect file path or the copied database did not exist.

### Resolution

Verify the copied file:

```powershell
Get-ChildItem C:\SRUMLab
```

Then calculate the hash:

```powershell
Get-FileHash C:\SRUMLab\SRUDB_Copy.dat
```

---

## Issue 6

Unexpected files present inside the SRUM directory.

### Cause

Windows maintains multiple Extensible Storage Engine (ESE) support files alongside the primary database.

### Resolution

This behavior is normal. Preserve the entire directory structure if performing a full forensic acquisition, while using **SRUDB.dat** as the primary artifact for this lab.
