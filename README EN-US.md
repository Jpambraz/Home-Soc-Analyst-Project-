# Home-Soc-Analyst-Project-
-A simple setup to make a Security Operation Center, Using Both Ubuntu and win11


Objectives With this project: Make a lab where one machine is an attacker and the other one is the defender, using LimaCharlie to see the telemetry and creation of YARA "Yet Another Recursive Acronym" and Sigma rules, blocking C2 "Command and Control" and privilege scalation, blocking automation using *Sliver*


What i m gonna need:
-a copy of windows 
-a ubutuntu copy 

Part 1 - Put yourself in Adversary Place *Taking Notes and making observations*.

Part 2- Simulating the adversary attack to notice detections.

Part 3- Blocking A Attack. 

Part 4- Adjusting False Positives.

Part 5- Scaning with YARA through rules of detection. 


Explaining a little of LimaCharlie. 
It is a platform of SecOps based in cloud with the focus being EDX/XDR *detection and response* collecting telemetry through the analysis of logs and Security Automation, being able to manage EndPoint Security.

<img width="632" height="309" alt="image" src="https://github.com/user-attachments/assets/b133ad4e-e7c2-4721-90d9-ef932e4d5789" /> 

-Creating a Organization on LimaCharlie 
-Name: it can be any but i choose *Home Soc Analyst*
-Data Residency Region: Closest avaiable  
-Template: No pre-configuration *but you can customize one for different purpouse*

*adicionar imagem do criando organização

-Sensors 
-Main fonts of receiving data on LimaCharlie, operating through many plataforms that are compatible and sending events in JSON throught the cloud of LimaCharlie live. (Change Later).
*adicionar imagem do sensores

-adding a new sensor 
1. Select Endpoint
2. Select Windows
3. I choose: *Windows VM -Lab* but you can choose through your preference
4. Create
5. Select The key that you just make

//add image of installation key 

-Installing a Sensor or Endpoint
//Add Image

Waiting for new sensors. 
-> configure the Virtual machines, and install the EDR of LimaCharlie in the windows system. 


-Windows EDR - Seonsors, monitoring and rules of defense.

open CMD and execute both those commands:
- cd C:\Users\Administrator\Downloads 
- install Key from LimaCharlie: lc_sensor.exe -i *[your_installation_key]*

will POP *connection acquired* of cmd and Lima charlie 
->ad both cmd and lima charlie images to the system. 

-Artifact Colletion:
      They are records of events and data collected from endpoints, networks, and other sources of threat analysis and response. These artifacts can be used for forensic investigation.

<add image>

name: windows-sysmon-logs 
Pattern: well://Microsoft-Windows-Sysmon/Operational:*
Retention Period: 10 Days
Platform: Windows

<add image>

-Extensions *ext-sigma*
Sigma is a detection rule format, enabling rules to identify malicious behavior.

<add image>




