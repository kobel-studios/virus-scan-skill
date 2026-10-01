---
name: virus-scan
description: Scan downloaded files using digital signature verification, VirusTotal reputation when available, and local heuristics
---

# Virus Scan Skill

Use this skill to safely check any file downloaded from the internet before running it.

## When to use
- Before running any downloaded installer, script, or executable
- Before running files from URLs the user hasn't verified
- Any time you download something from the web

## How to use

Run the scanner on any file:

```powershell
python .devin\skills\virus-scan\scanner.py <file_path>
```

The scanner will:
1. Check the file's digital signature (is it signed by a trusted publisher?)
2. Look up the file's SHA256 hash on VirusTotal (scans with 70+ engines)
3. Do basic heuristic checks (file type, suspicious patterns)
4. Print a clear SAFE / NOT SAFE / UNKNOWN verdict

## For downloads

When downloading a file, scan it BEFORE running it:

```powershell
# Download
Invoke-WebRequest -Uri "https://example.com/file.exe" -OutFile "C:\temp\file.exe"

# Scan it first
python .devin\skills\virus-scan\scanner.py C:\temp\file.exe

# Only run if it says SAFE
```

## Notes
- VirusTotal reputation may be unavailable or require an API key; treat unavailable results as UNKNOWN
- If the file has never been scanned before, it will show UNKNOWN and you should be cautious
- Digital signature check works on Windows executables and installers
- This does NOT use Norton or any paid antivirus
