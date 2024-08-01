# Honeypot VM with Microsoft Azure Sentinel Analysis

## Description
In this project, I setup a purposefully vulnerable virtual machine (VM) on Microsoft Azure to entice malicious actors to attempt login on the machine. This purposefully vulnerable VM is known as a honeypot. Through a series of tasks to enable log exportation automatically and using <a href="https://ipgeolocation.io/">IPGeolcation.io<a/>, I was able to pinpoint where all of these malicious login attempts were happening across a map.<br><br>

This project was very eye opening in terms of seeing just how many malicious login attempts were tried in such a short amount of time. In fact, before I could even RDP into my VM, there were already several attempts logged in my file. I also learned just how important scripting/automation is in regards to security. Simply monitoring the Windows Event Viewer was not enough nor even feasible and I only have one machine going. I could not imagine doing that across an enterprise to say the least. With scripting/autonation however, the task of logging malicious login attempts was made very simply especially with the ability to view the map as well.<br><br>

Below I will provide some screenshots of the process of making this project. I will not delve into a step by step process, but I will provide a blurb related to each screenshot. <br><br>

## Environments Used
* **Microsoft Azure**
* **Microsoft Sentinel**
  
## Tools Used
* **Windows Powershell ISE Script**
* **Kusto Query Language Script**
* **Log Analytics Workspace on Microsoft Azure**
* **Microsoft Defender for Cloud on Microsoft Azure**

## Screenshots
