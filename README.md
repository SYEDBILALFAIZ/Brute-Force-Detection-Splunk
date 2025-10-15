# Brute Force Attack Detection using Splunk

**Author:** Syed Bilal Faiz  
**Role:** SOC Analyst Intern (Student)  
**Date:** 16 October 2025

## Overview
This project demonstrates detection and analysis of brute-force login attempts by monitoring Windows Security logs (Event ID 4625) using Splunk Enterprise on Ubuntu.

## Files in this repository
- `windows_failed_logins.csv` — sample Windows Security logs (failed login events)
- `Brute_Force_Detection_Splunk_Project_Intern.pdf` — detailed project documentation
- `Brute_Force_Presentation_PreparedByOnlyTrim.pdf` — presentation summary (clean)
- `Brute_Force_Presentation.docx` — editable Word doc (optional)

## Quick Start (local)
1. Install Splunk Enterprise on Ubuntu and start Splunk Web (`http://localhost:8000`).
2. In Splunk Web: **Add Data → Upload File** → select `windows_failed_logins.csv` and set **Index = windows_logs**.
3. Run detection query:

index=windows_logs EventCode=4625
| stats count by Account_Name, IpAddress
| where count > 5

4. Save the search as an alert:
   - Name: **Brute Force Detection Alert**
   - Trigger: Number of results **is greater than** `0`
   - Action: Email or webhook to SOC channel (optional)

## Example Output
Account_Name IpAddress count
admin 192.168.1.15 5
guest 10.0.0.5 5


## Notes
- This repo is for educational/demo purposes.
- License: CC BY-NC-SA 4.0 (or choose MIT if you prefer).

## Contact
Syed Bilal Faiz — [bilalfaiz614@gmail.com 
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin&logoColor=white)](https://linkedin.com/in/syed-bilal-faiz-262324247)

