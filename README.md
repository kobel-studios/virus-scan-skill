# Virus Scan Skill

A reusable Devin skill and Python scanner for checking downloaded files with SHA-256 hashing, Windows Authenticode verification, VirusTotal reputation data when available, and simple script heuristics.

## Install

Copy `SKILL.md` and `scanner.py` to `.devin/skills/virus-scan/` in a project or your user-level Devin skills directory.

## Use

```bash
python scanner.py path/to/file
```

A clean result from this helper is not a guarantee of safety. Keep your operating system and antivirus protection current, and treat unavailable reputation data as unknown.
