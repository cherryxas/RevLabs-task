# Z1000 Changelog

## Version 7.3.0 – April 2025

### New Features

- **Sample Download API**  
  Added a new API endpoint: [`/api/v1/download_samples/`](https://example.com/api/v1/download_samples/).  
  This allows authorized users to download original attachments that were analyzed by Z1000 for further inspection or archiving.

- **Graphical Dashboard**  
  Introduced a new web-based dashboard that provides visual statistical insights into analyzed emails.  
  Includes charts on:
  - Number of analyzed emails per day
  - Malicious vs. clean file ratio
  - Common file types detected

### Bug Fixes

- **PHP Execution Vulnerability**  
  Fixed a critical security issue where PHP attachments were executed during analysis.  
  PHP files are now safely scanned without execution, closing a potential attack vector.

- **Large File Crash**  
  Resolved a stability issue causing the system to crash when analyzing attachments larger than 13.37 GB.  
  Z1000 now handles large files gracefully without performance degradation.
