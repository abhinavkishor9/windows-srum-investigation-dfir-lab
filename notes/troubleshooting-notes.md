# Troubleshooting Notes

## Issue 1

### Cannot access SRU folder

**Cause**

PowerShell not running with Administrator privileges.

**Resolution**

Run PowerShell as Administrator.

---

## Issue 2

### Copy-Item returns Access Denied

**Cause**

Insufficient permissions.

**Resolution**

Use an elevated PowerShell session.

---

## Issue 3

### SRUDB.dat not found

**Cause**

Incorrect folder path.

**Correct Location**

```
C:\Windows\System32\sru
```

---

## Issue 4

### Get-FileHash fails

**Cause**

Incorrect filename or path.

**Resolution**

Verify the copied file exists:

```
Get-ChildItem C:\SRUMLab
```

---

## Issue 5

### Cannot delete investigation folder

**Cause**

File handles still open.

**Resolution**

Close File Explorer windows and retry:

```
Remove-Item C:\SRUMLab -Recurse -Force
```

---

## Lessons Learned

- Always copy forensic artifacts before analysis.
- Never modify the original evidence.
- Verify evidence integrity immediately after acquisition.
- Maintain consistent documentation throughout the investigation.
