---
cover: ../../.gitbook/assets/TryHackMe Logo (3).png
coverY: 0
---

# Dunkle Materie - TryHackMe

<figure><img src="https://1.bp.blogspot.com/-V4OSIts6mBY/YUQlhSNm43I/AAAAAAAAAuo/OSjbqWWOh385dEMqZ3GgMXckiCsRJLPmACNcBGAsYHQ/s600/e7db29b3caba5e25bcdc5c049a3ff1cb.png" alt="" width="563"><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Intro" %}
#### This blog is a brief write-up of the TryHackMe room [Dunkle Materie](https://tryhackme.com/room/dunklematerieptxc9) and how to solve each question. This room revolves around using the tool [ProcDot](https://procdot.com/) to investigate a ransomware attack. Let’s begin!
{% endtab %}

{% tab title="Scenario" %}
_**The firewall alerted the Security Operations Center that one of the machines at the Sales department, which stores all the customers’ data, contacted the malicious domains over the network. When the Security Analysts looked closely, the data sent to the domains contained suspicious base64-encoded strings. The Analysts involved the Incident Response team in pulling the Process Monitor and network traffic data to determine if the host is infected. But once they got on the machine, they knew it was a ransomware attack by looking at the wallpaper and reading the ransomware note. Can you find more evidence of compromise on the host and what ransomware was involved in the attack?**_
{% endtab %}
{% endtabs %}

### Questions <a href="#questions" id="questions"></a>

#### Q1. Provide the two PIDs spawned from the malicious executable. (In the order as they appear in the analysis tool) <a href="#q1-provide-the-two-pids-spawned-from-the-malicious-executable-in-the-order-as-they-appear-in-the-ana" id="q1-provide-the-two-pids-spawned-from-the-malicious-executable-in-the-order-as-they-appear-in-the-ana"></a>

[![](https://1.bp.blogspot.com/-0GgOS6953bM/YUQtIpDG8NI/AAAAAAAAAuw/vayfxgunMJEqAuUpphpcWxQoLfNiVL8DgCNcBGAsYHQ/s600/2021-09-17%2B01\_39\_08-TryHackMe%2B\_%2BDunkle%2BMaterie%2B-%2BBrave.png)](https://1.bp.blogspot.com/-0GgOS6953bM/YUQtIpDG8NI/AAAAAAAAAuw/vayfxgunMJEqAuUpphpcWxQoLfNiVL8DgCNcBGAsYHQ/s690/2021-09-17%2B01\_39\_08-TryHackMe%2B\_%2BDunkle%2BMaterie%2B-%2BBrave.png)

The first question can be found after uploading the _Logfile.CSV_ and _traffic.pcap_ files from the _Analysis Files_ to ProcDot and select the _Launcher_ button to select a process from the list. After doing so a list of processes that were active while procmon was monitoring while be shown. After looking through the list I was able tell these two PIDs _(**8644,7128**)_ were spawned from the malicious executable _exploreer.exe_. It’s safe to assume it was given this name so that it could be easily overlooked and would be confused for the actual explorer.exe.

***

#### Q2. Provide the full path where the ransomware initially got executed?(Include the full path in your answer) <a href="#q2-provide-the-full-path-where-the-ransomware-initially-got-executedinclude-the-full-path-in-your-an" id="q2-provide-the-full-path-where-the-ransomware-initially-got-executedinclude-the-full-path-in-your-an"></a>

Once ProcDot graphs all active processes and network activity, after looking through the data we can see the file path where exloreer.exe was initially executed. _**c:\users\sales\appdata\local\temp\exploreer.exe**_.

[![](https://1.bp.blogspot.com/-e0nX4ZxdZFQ/YUQ\_lyOkgfI/AAAAAAAAAvA/yY7cFjL\_zTEEldz5a7sukbbQ7yI\_UVWEgCNcBGAsYHQ/s600/2021-09-17%2B03\_04\_22-TryHackMe%2B\_%2BDunkle%2BMaterie%2B-%2BBrave.png)](https://1.bp.blogspot.com/-e0nX4ZxdZFQ/YUQ\_lyOkgfI/AAAAAAAAAvA/yY7cFjL\_zTEEldz5a7sukbbQ7yI\_UVWEgCNcBGAsYHQ/s567/2021-09-17%2B03\_04\_22-TryHackMe%2B\_%2BDunkle%2BMaterie%2B-%2BBrave.png)

***

#### Q3. This ransomware transfers the information about the compromised system and the encryption results to two domains over HTTP POST. What are the two C2 domains? (no space in the answer) <a href="#q3-this-ransomware-transfers-the-information-about-the-compromised-system-and-the-encryption-results" id="q3-this-ransomware-transfers-the-information-about-the-compromised-system-and-the-encryption-results"></a>

#### Q4. What are the IPs of the malicious domains? (no space in the answer) <a href="#q4-what-are-the-ips-of-the-malicious-domains-no-space-in-the-answer" id="q4-what-are-the-ips-of-the-malicious-domains-no-space-in-the-answer"></a>

To answer this question you will need to head over to the second instance of the malicious process _7128_ after scrolling through the captured data, you’ll find a segment where exploreer.exe is sending and receiving a stream of TCP traffic from cisco\[.]com, _**mojobiden\[.]com IP: 146.112.61.108**_ and, _**paymenthacks\[.]com IP: 206.188.197.206**_. Based on the flow of the traffic exploreer.exe seems to be sending and receiving data from _mojobiden\[.]com_ it’s safe to assume that this is how the threat actor sends commands to the malware and receives data from the victims system. _Paymenthacks\[.]com_ must be where all the data that was collected from the victims system is being sent to based on the flow of the traffic, there is only outgoing traffic being sent to that domain. ![img](https://i.imgur.com/EaMCWKk.png)

***

#### Q5. Provide the user-agent used to transfer the encrypted data to the C2 channel. <a href="#q5-provide-the-user-agent-used-to-transfer-the-encrypted-data-to-the-c2-channel" id="q5-provide-the-user-agent-used-to-transfer-the-encrypted-data-to-the-c2-channel"></a>

If you right click on the _mojobiden_ server and click _**Follow TCP Stream**_ you can scroll down until you come across information in red text, here you will find the User-Agent information which is _**Firefox/89.0**_.\
![img](https://i.imgur.com/NhdxiMF.png)

***

#### Q6. Provide the cloud security service that blocked the malicious domain. <a href="#q6-provide-the-cloud-security-service-that-blocked-the-malicious-domain" id="q6-provide-the-cloud-security-service-that-blocked-the-malicious-domain"></a>

Going back to the network traffic from question 3&4 there was data being sent to and from a Cisco server with the address _23.204.14.115_. If you right click on the Cisco Server bubble you will find _**Cisco Umbrella**_ being mentioned in the data. You can read more about Cisco Umbrella [here](https://umbrella.cisco.com/). ![img](https://i.imgur.com/L5cKgGf.png)

***

#### Q7. Provide the name of the bitmap that the ransomware set up as a desktop wallpaper. <a href="#q7-provide-the-name-of-the-bitmap-that-the-ransomware-set-up-as-a-desktop-wallpaper" id="q7-provide-the-name-of-the-bitmap-that-the-ransomware-set-up-as-a-desktop-wallpaper"></a>

#### Q8. Find the PID (Process ID) of the process which attempted to change the background wallpaper on the victim’s machine. <a href="#q8-find-the-pid-process-id-of-the-process-which-attempted-to-change-the-background-wallpaper-on-the" id="q8-find-the-pid-process-id-of-the-process-which-attempted-to-change-the-background-wallpaper-on-the"></a>

If you follow the thread _**4892**_ created by 7128 you will see that there is a value set in the register path _HKCU\Control Panel\Desktop\Wallpaper_ the value is c:\programdata\ _**ley9kpi9r.bmp**_.

***

#### Q9. The ransomware mounted a drive and assigned it the letter. Provide the registry key path to the mounted drive, including the drive letter. <a href="#q9-the-ransomware-mounted-a-drive-and-assigned-it-the-letter-provide-the-registry-key-path-to-the-mo" id="q9-the-ransomware-mounted-a-drive-and-assigned-it-the-letter-provide-the-registry-key-path-to-the-mo"></a>

You can find the answer to this question by following the thread _4892_ and you will see the registry path for the mounted device. _**HKLM\SYSTEM\MountedDevices\DosDevices\Z:**_.

***

#### Q10. Now you have collected some IOCs from this investigation. Provide the name of the ransomware used in the attack. (external research required) <a href="#q10-now-you-have-collected-some-iocs-from-this-investigation-provide-the-name-of-the-ransomware-used" id="q10-now-you-have-collected-some-iocs-from-this-investigation-provide-the-name-of-the-ransomware-used"></a>

For this question you can look up the C2 servers on threat intel sites like VirusTotal and AlienVault. On VirusTotal enter the C2 address in the VirusTotal search bar and head to the _community_ tab. This concludes the Dunkle Materie room and I hope you enjoyed this room as much as I did. Happy Hacking! 😊

![img](https://i.imgur.com/RCSJGtm.png)

### I am actively looking for work, feel free to connect with me and lets talk business. Also feedback is appreciated! Thank you! <a href="#i-am-actively-looking-for-work-feel-free-to-connect-with-me-and-lets-talk-business-also-feedback-is" id="i-am-actively-looking-for-work-feel-free-to-connect-with-me-and-lets-talk-business-also-feedback-is"></a>

***

### Connect With Me ![:slightly\_smiling\_face:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/slightly\_smiling\_face.png) <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
