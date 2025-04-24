# Z1000 Changelog

## Version 7.3.0 – April 2025

### New features

- **Sample Download API**  
  Added a new API endpoint: [`/api/v1/download_samples/`](https://example.com/api/v1/download_samples/).  
  It enables authorized users to retrieve original email attachments processed by Z1000 for detailed review or archiving.

- **Graphical Dashboard**  
  This release introduces a graphical dashboard that displays key statistics about analyzed emails, such as volume, threat types, and detection trends. 

### Bug fixes

- **PHP Execution Vulnerability**  
  Fixed a security issue that executed PHP files during analysis, which could have allowed attackers to access the virtual machine.

- **Large File Crash**  
  Resolved a stability issue causing the system to crash when analyzing attachments larger than 13.37 GB.
