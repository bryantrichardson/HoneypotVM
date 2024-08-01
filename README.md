# Honeypot VM with Microsoft Azure Sentinel Analysis

## Description
In this project, I setup a purposefully vulnerable virtual machine (VM) on Microsoft Azure to entice malicious actors to attempt login on the machine. This purposefully vulnerable VM is known as a honeypot. Through a series of tasks to enable log exportation automatically and using ipgeolcation.io, I was able to pinpoint where all of these malicious login attempts were happening across a map.<br><br>

This project was very eye opening in terms of seeing just how many malicious login attempts were tried in such a short amount of time. In fact, before I could even RDP into my VM, there were already several attempts logged in my file. I also learned just how important scripting/automation is in regards to security. Simply monitoring the Windows Event Viewer was not enough nor even feasible and I only have one machine going. I could not imagine doing that across an enterprise to say the least. With scripting/autonation however, the task of logging malicious login attempts was made very simply especially with the ability to view the map as well.<br><br>

Below I will provide some screenshots of the process of making this project. I will not delve into a step by step process, but I will provide a blurb related to each screenshot. <br>

## Environments Used
* **Microsoft Azure**
* **Microsoft Sentinel**
  
## Tools Used
* **Windows Powershell ISE Script**
* **Kusto Query Language Script**
* **Log Analytics Workspace on Microsoft Azure**
* **Microsoft Defender for Cloud on Microsoft Azure**
* **ipgeolocation.io**

## Screenshots  <br>
Setting up the actual honeypot was relatively easy. The only thing I had to change about the initial setup of the VM was to configure a custom network security group that allowed for any/all inbound connections. <br>
<img width="260" alt="PublicProfileFW-Off" src="https://github.com/user-attachments/assets/b662fb7b-9156-4865-ad61-0dc3ab6ce75d">
<img width="260" alt="PrivateProfileFW-Off" src="https://github.com/user-attachments/assets/c7ef7e4a-3be7-4bdc-9914-42d88ac8b875">
<img width="260" alt="DomainProfileFW-Off" src="https://github.com/user-attachments/assets/5f190d89-2a99-4ba5-89d2-88990123fd4e"><br>
To further ensure the honeypot is truly vulnerable, I then disabled the Public, Private, and Domain firewall on the VM.<br>
I also setup a Log Analytics Workspace on Azure as well as configuring/connecting Microsoft Defender for Cloud to my VM so I could collect the log events from my VM. Connecting my VM to Microsoft Sentinel was the next step of the process.<br>
<img width="931" alt="JoshMadakor-Script" src="https://github.com/user-attachments/assets/1ab050a0-08f1-4b5a-b616-5d31b5363d37"><br>
Above is a snippet of Josh Madakor's Log Exporter script (my bad on the screenshot quaity, but it is linked down in sources in its entirety if you would like to see all of it). Running this script in Windows Powershell ISE will create an output of all of the failed RDP login attempts happening across the world outputting it in a logfile that is shown below.<br>
<img width="960" alt="sample of what failed rdp log" src="https://github.com/user-attachments/assets/024be92b-a950-4c3c-8bfa-d5126ed6a853"><br>
After creating a custom log in Windows Azure that is trained on the previous logfile, I was then able to use Anastasia's Script (below) to query the custom log into a more readable format. I chose the map to illustrate where all of the failed RDP logins are occurring across the world.
<img width="880" alt="Anastasia-Script" src="https://github.com/user-attachments/assets/4773a2c8-dda2-4df1-b9ef-4e850084c7aa"><br>
I left the VM open for roughly a day and a half, but somehow all of the attacks only came from 3 places. The one US login attempt was me testing to see if it worked in the beginning. There were already several failed login attempts before mine which was pretty scary/kind of interesting to be honest.<br>
<img width="606" alt="map" src="https://github.com/user-attachments/assets/1e508978-c3f6-4dad-ada3-9fdc8462a529"><br>
Overall, this project was very interesting and eye opening in regards to security. The fact other RDP login attempts were attempted before I could even test to see it worked was very exciting in a way. It would be interesting to see just how many non-RDP attempts were made against my honeypot, but perhaps I will do that in another project. <br><br> 
Thanks for reading and hope you have a great rest of your day/night :).<br>
## Sources
* <a href="https://www.youtube.com/watch?v=RoZeVbbZ0o0">Josh Madakor YouTube video</a>
   * His video was extremely helpful. It is a smidge outdated by now, but by either looking in the comments or online you can figure out the outdated parts fairly easily.
* <a href="https://medium.com/@michaellopezcs17/how-to-create-a-siem-microsoft-sentinel-2024-46ab6c7cfb8c">Michael Lopez Github</a>
   * One of the sources to help with the outdated parts.
* <a href="https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1">Josh Madakor's Log Exploiter Script</a>
   * The script that is key to automation and helping create the map.
* <a href="https://github.com/AnastasiaCoskuner/Sentinel-Lab/blob/main/query_log">Anastasia Coskuner's Query Log Script</a>
   * Helped with one of the outdated parts in the video as well.
* <a href="https://ipgeolocation.io/">ipgeolocation.io</a>
   * The website/API that made the whole map part doable.

