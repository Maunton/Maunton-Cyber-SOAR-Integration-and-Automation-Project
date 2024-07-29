
<h1>SOAR-EDR-Integration-and-Automation-Project</h1>



<h2>Description</h2>
The SOAR EDR Integration and Automation Project is a comprehensive hands-on initiative designed to enhance the efficiency and effectiveness of Security Operation Centers (SOCs) through the implementation of Security Orchestration, Automation, and Response (SOAR) solutions. This project, authored by Maunton Cyber, leverages the Tines SOAR platform and the LimaCharlie Endpoint Detection and Response (EDR) tool to automate repetitive security tasks and streamline incident response processes.

<h2>Key learnings, challenges faced, and solutions implemented.</h2>
In this project, key learnings include understanding the intricacies of integrating and automating security tools like LimaCharlie and Tines, developing custom detection rules, and creating effective playbooks to enhance SOC operations. Challenges faced involved configuring the tools to work seamlessly together, handling false positives, and ensuring the playbook's logic was sound. Solutions implemented included thorough testing and iterative refinement of detection rules to minimize false positives, leveraging community resources and documentation to troubleshoot issues, and employing tools like draw.io to visualize and organize the playbook workflow. Overall, the project provided comprehensive hands-on experience in SOAR and EDR, from setup and integration to automation and troubleshooting, reinforcing both technical skills and problem-solving abilities.




<br />


<h2>Project Stack:</h2>

- <b>Tines SOAR Platform: Utilized for creating and managing automation playbooks (stories).</b>
- <b>LimaCharlie EDR: Deployed to monitor and detect security threats on endpoint devices.</b>
- <b>Windows Virtual Machine: Acts as the agent for deploying and testing the detection and response mechanisms.</b>
- <b>Communication Tools: Integration with Slack for real-time alerts and user interaction.</b>
- <b>The LaZagne project from GitHub is utilized to simulate the detection of password recovery tools on a machine, enabling the development and testing of custom detection rules and automated response playbooks.</b>

<h1>Project walk-through:</h1>
  
<br />

<h3>Playbook Workflow Design:</h3>
Started with designing the workflow for the playbook, diagramming the desired automation processes:
<br />
<br />
<p align="center">
<img src="https://imgur.com/Qd1fCBP.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<br />
<h3>Set up LimaCharlie and configure it to collect data from a Windows machine:</h3>
In LimaCharlie, under the Sensors tab, go to the Instalation Keys tab and tap Windows 64 for instalation of sensor into your Windows machine.
<br />
<br /> 
<p align="center">
<img src="https://imgur.com/kOJORwX.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">  
Copy the Sensor Key for instalation.
<br />
<br />
<p align="center">  
<img src="https://imgur.com/6yrY6Y4.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
1. Open PowerShell on the Windows machine and run as Administrator
<br />  
2. Change directories into Downloads folder and install the newly downloaded file from LimaCharlie with the Sensor Key pasted after -i

   ## Usage:
    .\hcp_win_x64_release_4.29.2.exe -i [Sensor Key]
   
<br />
<br />
<p align="center">
<img src="https://imgur.com/7CDtTFa.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<h3>Developing a custom detection rule in LimaCharlie to identify the use of password recovery tools (Lazagne.exe):</h3>
<p align="left">
1. Install Lazagne.exe on the Windows machine (Windows firewall will need to be disabled): https://github.com/AlessandroZ/LaZagne
<br /> 
2. Run Lazagne.exe to view the output from LimaCharlie  
<p align="center">
<img src="https://imgur.com/6MajO1s.png" height="80%" width="80%" alt="Project walk-through"/>
<br /> 
<p align="left">
1. Go into the Timeline tab on LimaCharlie to view the detections.
<br /> 
2. Type Lazagne in the filter to locate it's process.
<br /> 
3. Tap the first NEW_PROCESS where LaZagne is. This will be used to create a new rule for detection.
<p align="center">
<img src="https://imgur.com/gme0cgD.png" height="80%" width="80%" alt="Project walk-through"/> 
<br /> 
<p align="left">
1. Open a new LimaCharlie tab in the browser.
<br /> 
2. In the Automation tab select D&R Rules.
<br /> 
3. Hit the New Rule tab.
<p align="center">
<img src="https://imgur.com/WQDijYk.png" height="80%" width="80%" alt="Project walk-through"/>
<br /> 
<p align="left">
This is where the new rule will be made.
<br /> 
<p align="center">
<img src="https://imgur.com/iuTnaj7.png" height="80%" width="80%" alt="Project walk-through"/>
<br /> 
<p align="left">
Instead of creating a new rule from scratch, it can be made from an existing rule.
<br />
Search for a rule that is similar.
<br />
Follow the link to the next page.
<p align="center">
<img src="https://imgur.com/B0W0i0H.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Follow the link to Github.
<p align="center">
<img src="https://imgur.com/AvKDBnY.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Hit the Raw button and copy the text.
<p align="center">
<img src="https://imgur.com/HJf5WtD.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
1. Paste the text into the Detect and Respond areas.
<br />
2. Delete the Detect and Respond words from the new rules.
<p align="center">
<img src="https://imgur.com/b5XUiTX.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Modify the new rules to match the Event condtions found in Timeline - NEW_PROCESS.
<p align="center">
<img src="https://imgur.com/1StyYZF.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="center">
<img src="https://imgur.com/q4D5ShH.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<img src="https://imgur.com/Rll29OK.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
1. To test the new rule copy the Event NEW_PROCESS from the Timeline and paste it into the Target Event area.
<br />
2. Hit the Test Event button.
<p align="center">
<img src="https://imgur.com/COWhYhw.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Success of creating the new rule will be shown by Match of True in green.
<p align="center">
<img src="https://imgur.com/EObg6xG.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
1. Create an account at Slack.com.
<br />
2. Add channel and label it as Alerts.
<p align="center">
<img src="https://imgur.com/kdbKGYv.png" height="80%" width="80%" alt="Project walk-through"/>

<h3>Integration with Tines:</h3>
<p align="left">
Open Tines, create an account, and start a new story.
<br />   
<p align="center">
<img src="https://imgur.com/rWGe9ka.png" height="80%" width="80%" alt="Project walk-through"/>
<p align="left">
1. In the Tines workflow drag and drop Webhook. 
<br /> 
2. Copy the Webhook URL.
<br />   
<p align="center">
<img src="https://imgur.com/Nu2QRwm.png" height="80%" width="80%" alt="Project walk-through"/>
<p align="left">
In LimaCharlie go to the Outputs tab and select + Add Output.
<br />   
<p align="center">
<img src="https://imgur.com/em0FtGr.png" height="80%" width="80%" alt="Project walk-through"/>
<p align="left">
Select Detections.
<br />   
<p align="center">
<img src="https://imgur.com/MN8slEB.png" height="80%" width="80%" alt="Project walk-through"/>
<p align="left">
Select Tines.
<br />   
<p align="center">
<img src="https://imgur.com/Z4zo4bj.png" height="80%" width="80%" alt="Project walk-through"/>
<p align="left">
1. Paste the Webhook URL from Tines.
<br />
2. Create a name and save the Output.
<p align="center">
<img src="https://imgur.com/rdC0V51.png" height="80%" width="80%" alt="Project walk-through"/>
<p align="left">
Configuration saved.
<p align="center">
<img src="https://imgur.com/roIYmh7.png" height="80%" width="80%" alt="Project walk-through"/>
<p align="left">
Drag and drop Slack along with Send Email into Tines and add a connection from Webhooks to each.
<p align="center">
<img src="https://imgur.com/vPvSb9I.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Drag and drop User Prompt, add a boolean for Yes/No, and add connection from Webhooks.
<p align="center">
<img src="https://imgur.com/4crsXqX.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Drag and drop Triggers for Yes/No and add connections.
<p align="center">
<img src="https://imgur.com/GbzKl85.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Drag and drop Slack for the No Trigger and add a connection.
<p align="center">
<img src="https://imgur.com/1VMuLJs.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Drag and drop HTTP Request to Isolate Sensor and add a connection.
<p align="center">
<img src="https://imgur.com/nnB7Ke5.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
Drag and drop HTTP Request to get Isolation Status.
<br />
Drag and drop Slack in order to get a message about the isolated Windows machine.
<br />
This is the final set-up for the project.
<p align="center">
<img src="https://imgur.com/7zvh6Xe.png" height="80%" width="80%" alt="Project walk-through"/>
<h3>Run through of the project entirety:</h3>
<br />
<p align="left">
1. Lazagne.exe has infected the Windows machine.  
<p align="center">
<img src="https://imgur.com/Fj2R8xE.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
2. Ping command to a website shows that the infected Windows machine is still running on the network.  
<p align="center">
<img src="https://imgur.com/1auopUk.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
3. Message sent to Slack shows that Lazagne.exe executed.  
<p align="center">
<img src="https://imgur.com/nl0lGJU.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
4. Message sent to Email shows that Lazagne.exe executed.  
<p align="center">
<img src="https://imgur.com/3nUIF5V.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
5. User Prompt pops up asking Yes/No to isolate infected windows machine.  
<p align="center">
<img src="https://imgur.com/kPupmW3.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
6. Yes was selected from User Prompt and next window pops up.  
<p align="center">
<img src="https://imgur.com/z27G2j4.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
7. Tines workflow shows the events as Yes was selected.  
<p align="center">
<img src="https://imgur.com/fNiM09q.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
8. LimaCharlie shows that, yes indeed, the Windows machine is isolated.  
<p align="center">
<img src="https://imgur.com/P3wBLKd.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
9. Ping command to a website shows that the infected Windows machine is isolated from the network. 
<p align="center">
<img src="https://imgur.com/p0L4Rpy.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
10. Slack message shows that the Windows machine has been isolated. 
<p align="center">
<img src="https://imgur.com/79iC1sw.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
11. Lazagne.exe event was ran again and this time No was selected. 
<p align="center">
<img src="https://imgur.com/1irsAZ0.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
12. Tines workflow shows the events as No was selected.
<p align="center">
<img src="https://imgur.com/Hf7zfCz.png" height="80%" width="80%" alt="Project walk-through"/>
<br />
<p align="left">
13. Message in Slack shows, "...The computer was not isolated, please investigate".
<p align="center">
<img src="https://imgur.com/4Sfplkd.png" height="80%" width="80%" alt="Project walk-through"/>



<br />
<br />
  

  
</p>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
