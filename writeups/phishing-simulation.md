I safely simulated a harmless phishing attack to analyse its behaviour and how it is captured by an endpoint telemetry. Focusing on behavioural analysis is very important to detecting anomalies. Using Splunk and Sysmon, I investigated Sysmon EventCode=1 (Process Creation).

#Simulation
I created a harmless macro-enabled document using notepad, command: powershell.exe -NoProfile -WindowStyle Hidden -Command notepad.exe
When the file is opened cmd.exe spawned powershell.exe which also launches notepad.exe.Sysmon captures this in EventID=1 Process creation; Image=powershell.exe ParentImage=cmd.exe  CommandLine= powershell.exe -NoProfile -WindowStyle Hidden -Command notepad.exe
 
#Investigation 

-What initiated cmd.exe? User, System, Script or Browser? 

-Is this normal? 

-Behavioural analysis; Looked out for obfuscation, encoded commands, hidden execution, suspicious Powershell flags, suspicious processes and download activity.

#Results

1.Powershell.exe was spawned by cmd.exe, it can be observed that though cmd.exe is not part of the command, it is indicated as a parent process. This is because Splunk often spawns cmd.exe before powershell.exe

2.This is absolutely normal parent-child relationship

3.There were no indicators of obfuscation, download activity, hidden execution or encoded commands.

4. Though this is a harmless simulation, there are flags in the command which are suspicious;
           -NoProfile = this executes the code stealthily and fast.
           -WindowStyle Hidden = runs malicious scripts without alerting the user.

#Skills Learned

-Reading Sysmon logs

-Identifying suspicious flags

-Detecting phishing-styled execution chains

-Understanding process behaviour.

#Sysmon Log Example
https://github.com/Patricia-Ayerki-Anim/Security-Analysis-Lab/blob/499d4c7c6861ac339cf2d74a1859a353443c9a42/Screenshots/Phishing.png
