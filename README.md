1. Project Overview
This is an Endpoint Telemetry Pipeline project which showcases my deployment, configuration and validation abilities using Splunk and Sysmon. In Splunk, I created a custom sysmon index to ingest, parse, normalise and analyse events.
This demostrates real SOC analyst work:
-Log Ingesting
-Windows Event Log analysis
-Splunk Configuration
Telemetry Validation
Preparing data for detection engineering

3. Architecture
   Data Flow
   - Sysmon: endpoint telemetry
   - Logs: written to Microsoft-Windows-Sysmon/Operational
   - Splunkd: accesses the event channel
   - Logs are stored in a custom index sysmon.
   - Splunk TA for sysmon: parses and normalizes XML logs.
   - Events made searchable for dashboard and detection.
     
Components
- Windows 11 vm
- Sysmon
- Splunk
- Splunk TA for Microsoft Sysmon

  3. Implementation
     a. Sysmon Deployment
     - Installed sysmon with the ... configuration file
     - Verified installion using Windows Event Viewer.
     - Used Powershell command Get-WinEvent -Logname "Microsoft-Windows-Sysmon/Operational" to verify event generation.

       b. Splunk Installation and troubleshooting
       -Splunk was successfully running but not indexing logs from sysmon.
       - Verified that the input.conf file was properly configured.
    
         d. Sysmon Index Creation
       - Discovered the sysmon index was not created.
       - Created sysmon index and restart Splunk with the command "C:\Program Files\Splunk\bin" .\splunk restart
    
         e. Ingestion Successful
       - Search: index=sysmon
       - Splunk is indexing, confirmed 422 Sysmon events.

       
       
