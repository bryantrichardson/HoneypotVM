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
* **ipgeolocation.io**

## Screenshots
<img width="290" alt="PublicProfileFW-Off" src="https://github.com/user-attachments/assets/b662fb7b-9156-4865-ad61-0dc3ab6ce75d">

<img width="284" alt="PrivateProfileFW-Off" src="https://github.com/user-attachments/assets/c7ef7e4a-3be7-4bdc-9914-42d88ac8b875">

<img width="290" alt="DomainProfileFW-Off" src="https://github.com/user-attachments/assets/5f190d89-2a99-4ba5-89d2-88990123fd4e">


<img width="931" alt="JoshMadakor-Script" src="https://github.com/user-attachments/assets/1ab050a0-08f1-4b5a-b616-5d31b5363d37">

<img width="880" alt="Anastasia-Script" src="https://github.com/user-attachments/assets/4773a2c8-dda2-4df1-b9ef-4e850084c7aa">

<img width="406" alt="map" src="https://github.com/user-attachments/assets/1e508978-c3f6-4dad-ada3-9fdc8462a529">

## References
* <a href="https://www.youtube.com/watch?v=RoZeVbbZ0o0">Josh Madakor YouTube video</a>
   * His video was extremely helpful. It is a smidge outdated by now, but by either looking in the comments or online you can figure out the outdated parts fairly easily.
* <a href="https://medium.com/@michaellopezcs17/how-to-create-a-siem-microsoft-sentinel-2024-46ab6c7cfb8c">Michael Lopez Github</a>
 * One of the sources to help with the outdated parts
* <a href="https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1">Josh Madakor's Log Exploiter Script</a>
* <a href="https://github.com/AnastasiaCoskuner/Sentinel-Lab/blob/main/query_log">Anastasia Coskuner's Query Log Script</a>
 * Helped with one of the outdated parts in the video as well.
* <a href="https://ipgeolocation.io/">IPGeolocatio.io</a>
 * The website/API that made the whole map part doable

