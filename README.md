1. Project Overview
This is an Endpoint Telemetry Pipeline project which showcases my deployment, configuration and validation abilities using Splunk and Sysmon. In Splunk, I created a custom sysmon index to ingest, parse, normalise and analyse events.
This demostrates real SOC analyst work:
   - Log Ingesting
   - Windows Event Log analysis
   - Splunk Configuration
   - Telemetry Validation
   - Preparing data for detection engineering

2. Architecture
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
   - Splunk  Enterprise
   - Splunk TA for Microsoft Sysmon

 3. Implementation
     a. Sysmon Deployment
     - Installed sysmon with SwiftOnSecurity configuration file
     - Verified installion using Windows Event Viewer.
     - Used Powershell command Get-WinEvent -Logname "Microsoft-Windows-Sysmon/Operational" to verify event generation.

     b. Splunk Installation and troubleshooting
       - Splunk was successfully running but not indexing logs from sysmon.
       - Verified that the input.conf file was properly configured.
         
     c. Debugging Configuration
       - Utilized btool to ensure Splunk was loading:
           system/local/inputs.conf
           TA-microsoft-sysmon/default/inputs.conf
       - Ensured Sysmon input was enabled: disabled = false
       - Validated correct stanza in system/local/inputs.conf
    
     d. Sysmon Index Creation
       - Discovered that sysmon index was not created.
       - Created sysmon index and restart Splunk with the command "C:\Program Files\Splunk\bin" .\splunk restart
    
     e. Ingestion Successful
       - Search: index=sysmon
       - Splunk is indexing, confirmed 422 Sysmon events.


 4. Skills Demonstrated
    
         Technical Skills
       - Splunk installation and service recovery
       - Windows Event log analysis
       - Sysmon deployment
       - Splunk inputs.conf configuration
       - Index creation and data onboarding
       - Using Splunk btool for debugging configuration
       - XML log interpretation

         SOC Analyst Skills
       - Telemetry validation
       - Root-cause analysis
       - Troubleshooting ingestion pipelines
       - Understanding endpoint behavior
       - Preparing data for detection
         
 5. Lessons Learnt
       - Why indexes are prerequisite for ingestion
       - Debugging ingestion pipelines using btool
       - Validation of logs at every stage
       - How Sysmon telemetry supports SOC investigations
       - How Splunk merges configuration layers

 6. Next Steps
       This project is the foundation for:
       - Detection Engineering
       - MITRE ATT&CK Mapping
       - Dashboards
       - Full Incident Simulation

 

       
       
