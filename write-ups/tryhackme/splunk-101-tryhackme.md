---
cover: ../../.gitbook/assets/TryHackMe Logo (3).png
coverY: 0
---

# Splunk 101 - TryHackMe

<figure><img src="https://i.imgur.com/iavJPzF.jpg" alt=""><figcaption></figcaption></figure>

### Introduction to Splunk <a href="#introduction-to-splunk" id="introduction-to-splunk"></a>

Typically when people think of a SIEM, they think of Splunk, and rightly so. Per the Splunk website, they boast that 91 of the Fortune 100 use Splunk.

Splunk is not only used for security; it’s used for data analysis, DevOps, etc. But before speaking more on Splunk, what is a SIEM exactly?

A SIEM **(Security Information and Event Management)** is a software solution that provides a central location to collect log data from multiple sources within your environment. This data is aggregated and normalized, which can then be queried by an analyst.

As stated by [Varonis](https://www.varonis.com/blog/what-is-siem/), there are 3 critical capabilities for a SIEM:

* Threat detection
* Investigation
* Time to respond

Some other SIEM features:

* Basic security monitoring
* Advanced threat detection
* Forensics & incident response
* Log collection
* Normalization
* Notifications and alerts
* Security incident detection
* Threat response workflow

This room is a general overview of Splunk and its core features. Having experience with Splunk will help your resume stick out from the rest.

Splunk was named a “Leader” in [Gartner’s](https://www.splunk.com/en\_us/form/gartner-siem-magic-quadrant.html) 2020 Magic Quadrant for Security Information and Event Management.

Per Gartner, _“Thousands of organizations around the world use Splunk as their SIEM for security monitoring, advanced threat detection, incident investigation and forensics, incident response, SOC automation and a wide range of security analytics and operations use cases.”_

Room Machine

Before moving forward, deploy the machine. If you want to RDP into the machine yourself:

* Machine IP: `IP ADDRESS`
* User name: `administrator`
* User password: `letmein123!`

Open Chrome and navigate to the Splunk instance (`http://127.0.0.1:8000`). You may need to refresh the page until Splunk loads.

Note: Splunk can take up to five minutes to fully load.

If you want to install Splunk on your own machine, follow Splunk’s official installation notes [here](https://docs.splunk.com/Documentation/Splunk/8.1.2/SearchTutorial/InstallSplunk).

***

### Splunk Apps <a href="#splunk-apps" id="splunk-apps"></a>

![](https://i.imgur.com/ux2DMKT.png)

#### Q. What is the ‘Folder name’ for the add-on? <a href="#q-what-is-the-folder-name-for-the-add-on" id="q-what-is-the-folder-name-for-the-add-on"></a>

Answer: **TA-microsoft-sysmon**

#### Q. What is the Version? <a href="#q-what-is-the-version" id="q-what-is-the-version"></a>

Answer: **10.6.2**

### Adding Data <a href="#adding-data" id="adding-data"></a>

#### Q. Upload the Splunk tutorial data on the desktop. How many events are in this source? <a href="#q-upload-the-splunk-tutorial-data-on-the-desktop-how-many-events-are-in-this-source" id="q-upload-the-splunk-tutorial-data-on-the-desktop-how-many-events-are-in-this-source"></a>

**Note**: Make sure you upload the data once only.

To add the tutorial data, start by:

1. Clicking “Add Data” on the homepage.

![](https://i.imgur.com/2jbquKc.png)

2. Click “Upload”.

![](https://i.imgur.com/WPXn0GQ.png)

3. Click “Select file” or drag and drop the “tutorialdata” zip from the desktop into Splunk.

![](https://i.imgur.com/VWxBlw5.png)

4. Click “Next” to proceed to “Input Settings”.

![](https://i.imgur.com/0JCCNi5.png)

5. Leaving everything as default in “Input Settings” and click “Review”.

![](https://i.imgur.com/cVOZT2A.png)

6. Click “Submit”.

![](https://i.imgur.com/l7sY0P1.png)

7. Click “Start Searching”.

![](https://i.imgur.com/nRuebnV.png)

8. Lastly wait Splunk to load all the events.

![](https://i.imgur.com/BKAISAl.png)

Answer: **109,864**

***

### Splunk Queries <a href="#splunk-queries" id="splunk-queries"></a>

#### Q. What is the sourcetype? <a href="#q-what-is-the-sourcetype" id="q-what-is-the-sourcetype"></a>

1. Start by searching _“failed password”_ in the search field.

![](https://i.imgur.com/taadIn8.png)

2. The sourcetype can be found in the bottom right corner of each of the events.

![](https://i.imgur.com/d5BEkGo.png)

Answer: **www1/secure**

#### Q. What is the last username in this tab? <a href="#q-what-is-the-last-username-in-this-tab" id="q-what-is-the-last-username-in-this-tab"></a>

1. After heading over to the “Patterns” tab the last pattern mentions the username _“myuan”_.

![](https://i.imgur.com/XyQ0Jjh.png)

Answer: **myuan**

#### Q. Search for failed password events for this specific username. How many events are returned? <a href="#q-search-for-failed-password-events-for-this-specific-username-how-many-events-are-returned" id="q-search-for-failed-password-events-for-this-specific-username-how-many-events-are-returned"></a>

1. While still under the “Patterns” tab, add the username that was found to the search query. After doing so, the events will be filtered to match the query.

![](https://i.imgur.com/QVhGt2I.png)

Answer: **16**

***

### Sigma Rules <a href="#sigma-rules" id="sigma-rules"></a>

#### Q. Use the **Select document** feature. What is the Splunk query for ‘sigma: APT29’? <a href="#q-use-the-select-document-feature-what-is-the-splunk-query-for-sigma-apt29" id="q-use-the-select-document-feature-what-is-the-splunk-query-for-sigma-apt29"></a>

1. Head over to [Uncoder.io](https://uncoder.io/)
2. In the **“Select document”** bar start typing “apt” and select APT29
3. Select Splunk and translate, the splunk rule will be displayed in the box to the right.\
   ![](https://i.imgur.com/Uo1Px74.gif)

Answer: **CommandLine="**_**-noni -ep bypass $**_

#### Q. Use the Github Sigma repo. What is the Splunk query for ‘CACTUSTORCH Remote Thread Creation’? <a href="#q-use-the-github-sigma-repo-what-is-the-splunk-query-for-cactustorch-remote-thread-creation" id="q-use-the-github-sigma-repo-what-is-the-splunk-query-for-cactustorch-remote-thread-creation"></a>

1. Head over to the Sigma github [repo](https://github.com/SigmaHQ/sigma).
2. Navigate to \*rules > windows > create\_remote\_thread > sysmon\_cactustorch.yml.
3. Copy and paste the yml rule into [Uncoder.io](http://uncoder.io/) and translate it to Splunk.

![](https://i.imgur.com/djPTpXS.png)

Answer: **SourceImage=“**_**\System32\cscript.exe" OR SourceImage="**_**\System32\wscript.exe” OR SourceImage=“**_**\System32\mshta.exe" OR SourceImage="**_**\winword.exe” OR SourceImage=“**_**\excel.exe") AND TargetImage="**_**\SysWOW64\\\*” AND NOT StartModule="**

***

### Dashboards & Visualizations <a href="#dashboards-amp-visualizations" id="dashboards-amp-visualizations"></a>

1. Add the tutorialdata to Splunk and query for \* | top limit=5 EventID

![](https://i.imgur.com/F94LOK5.png)

2. From there follow the diagrams provided in the Dashboards & Visualizations and you should be able to get the graph to display.

![](https://i.imgur.com/mA9LRzp.png)

### Connect With Me ![:slightly\_smiling\_face:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/slightly\_smiling\_face.png) <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
