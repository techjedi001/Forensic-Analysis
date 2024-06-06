# Digital Forensic-Analysis Incident Report
A user from accounting found her computer turned on on Monday morning (1/30/17), despite having turned it off on Friday. She suspects unauthorized access and use of her computer during the weekend.


<h2>Description</h2>


<b>Project Overview:</b>
  - You receive a complaint from a Phyllis from accounting, who says that when she came to work Monday morning (1/30/17), her computer wasn’t in the same state as she left it – for one thing, it was off when she left work on Friday and on when she came in on Monday.  She thinks someone may have used her computer.

   - In this project, I utilize a fornesic tool (Autopsy) to execute forensica analysis on the user's computer for any findings and evidence that someone has used her computer.

<b>Deliverables/Analysis:</b> 
- Profile of the system, i.e. OS version, memory, disk, etc
- Analysis methodology
-	Description of log files or other resources examined
- Log on, log off activity for the computer
- Browser history – sites visited, times
- Identities located on the computer
- Findings
- Recommendations

<h2>Languages and Utilities Used</h2>

- bash
- Autopsy (forensic analysis tool)
<p align="center">
<img src="https://imgur.com/HlNPr5r.png" height="80%" width="80%" 
<br />
<br />
<p align="center">
  


<h2>Environments Used </h2>

- Linux Kali workstation
- Autopsy Graphic User Interface

<h2>Analysis </h2>

-  Profile of the system, i.e. OS version, memory, disk, etc

<p align="center">
<img src="https://imgur.com/p1BuM3G.png height="80%" width="80%" 
<br />
<br />
<p align="center">

a.	Windows 7 enterprise – WIndows NT
b.	4GB Memory RAM
c.	Vol2 size 1048576 bytes
d.	Vol3 size 105906176 bytes


  
<h2>Sample of suspicious programs executed </h2>
<p align="center">
<img src="https://imgur.com/EQxKNEY.png" height="80%" width="80%" 
<br />
<br />
<p align="center">

<h2>Setup.exe program executed: <h2/>  
<p align="center">
<img src="https://imgur.com/5PBM9yI.png" height="80%" width="80%" 
<br />
<br />
<p align="center">

<b> Suspicious executed programs </b>

- SETUP-STUB.EXE 20170129 13:12:23 PST
- SETUP.EXE 20170129 13:29:48 PST
- MCTADMIN.EXE 20170129 13:31:13 PST
- NETSH.EXE 20170129 12:49:38 PST
- CLICKONCE_BOOTSTRAP.EXE-384D7E95.of
- $BadClus:$Bad  file of 1GB+.  01/29/2017 12:22

<h2>Sample of webcache-sites visited: <h2/>
<p align="center">
<img src="https://imgur.com/WA9PLV8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">


<h2>Key word hits: <h2/>
  <img src="https://imgur.com/N33xCrr.png" height="80%" width="80%" />
  <br />
  <br />
<p align="center">


<h2>Sample of event log 4624 (login success): <h2/>
<p align="center">
<img src="https://imgur.com/Luu5FCF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<p align="center">


-	<b>Log on, log off activity for the computer </b>                              
-	  Windows event 4624 (successful logins)                                   
  -	Guest account login 20170129 20:55:24 (5 instances)                     
  -	Guest account login 20170129 21:30:51                                  
  - Anonymous login20170129 20:52:35

<h2>Sample of event log 4625 (login fails): <h2/>
  <img src="https://imgur.com/dIyOjCM.png" height="80%" width="80%" />
  <br />
  <br />
<p align="center">

<b>-		Windows event 4625 (Login fails)                                        
  -	20170129-20170130; 6 login failure events (non malicious (LocalService)</b>

<h2>Identities located on the computer</h2>

- Jane                      
- Joe                       
- Waldo                  
- Phillis                
- Guest                  
- Infosec                
- Administrator          
- Local System account   
- Network Service account
- Service virtual account

<h2>Findings</h2>

From 1/28/2017 to 1/29/2017 midnight, a user logged into the accounting employee’s desktop. In our investigation, the account of interest was the guest account, who logged into the workstation atleast 6 times. The other was an anonymous login, which was one instance on the day of 1/29/2017. This was determined to be from the LocalService account. The activity during these time periods shows activity of creating bookmarks to websites that are not malicious in nature. 
The web activity identified included browsing to multiple different websites, which also seemed to be harmless. The domains visited were not malicious. Some process/programs that were interesting during the time period was the “netsh.exe”. This network command shell allows users to display or modify a computer’s network configuration while it’s running. While it could be the user logged on is viewing network settings, it raises a red flag. The other interesting activity is a “setup-stub.exe”, which seems harmless since it is a Mozilla browser executable file. The concern is allowing users to install .exe programs, especially as guest user. 


<h2>Recommendations</h2>

The following recommendations aim to reduce the risk of confidentiality and integrity of the system.  While the events are specific to one workstation in accounting, the recommendations can be applied to all departments at the IT department's discretion. 
-	Have UAC enabled to prevent unauthorized changes to the operating system and have only administrators install ‘.exe’ files 
-	Enable UAC or group policy to prevent users from accessing and/or changing network settings. 
-	Enable group policy to have time of day login allowed. This can be allowed on a case-by-case basis to not put strain on users who don’t work during normal hours. Or specify different time of day login group policies. 
-	Review account lockout policy. This prevents a user account from being accessed after the wrong password is entered a specific number of times over a specified time period. An ideal period would be 5 times within a 2-minute period. 
-	Have standardized/sanctioned applications installed across organizations as needed




<p align="center">
 

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
