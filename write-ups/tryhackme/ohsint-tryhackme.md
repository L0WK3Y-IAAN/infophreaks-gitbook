---
cover: ../../.gitbook/assets/TryHackMe Logo (3).png
coverY: 0
---

# OhSINT - TryHackMe

<figure><img src="https://i.imgur.com/ld9qJRt.png" alt=""><figcaption></figcaption></figure>

### Intro <a href="#intro" id="intro"></a>

In this TryHackMe room you will be tasked with gathering intel on a target based on an image, you must use Open Source Intelligence to solve the questions.

### Scenario <a href="#scenario" id="scenario"></a>

_What information can you possibly get with just one photo?_\
![link text](https://i.imgur.com/eZxOF9B.jpg)

### Questions <a href="#questions" id="questions"></a>

#### Q1. What is this users avatar of? <a href="#q1-what-is-this-users-avatar-of" id="q1-what-is-this-users-avatar-of"></a>

To get started you will need to extra metadata from the photo, this can be done using a tool called [_**Exiftool**_](https://exiftool.org/). This tool needs to be downloaded but I will be using an online version of this tool called [ExifMeta](https://exifmeta.com/). After uploading the image to exifmeta, you will be presented with a list of RAW data pulled from the image’s metadata. Right off the bat, I see a few things that catch my eye. XMP-exif:GPSLatitude, XMP-exif:GPSLongitude, and _**XMP-tiff:Copyright**_. After Googling OWoodflint the first result should be a twitter user with the profile picture of a _**cat**_.

| System:FileName            | WindowsXP.jpg             |
| -------------------------- | ------------------------- |
| System:FileSize            | 234081                    |
| System:FileModifyDate      | 2021:09:24 19:18:32+00:00 |
| System:FileAccessDate      | 2021:09:24 19:18:32+00:00 |
| System:FileInodeChangeDate | 2021:09:24 19:18:32+00:00 |
| System:FilePermissions     | 100644                    |
| File:FileType              | JPEG                      |
| File:FileTypeExtension     | JPG                       |
| File:MIMEType              | image/jpeg                |
| File:ImageWidth            | 1920                      |
| File:ImageHeight           | 1080                      |
| File:EncodingProcess       | 0                         |
| File:BitsPerSample         | 8                         |
| File:ColorComponents       | 3                         |
| File:YCbCrSubSampling      | 2 2                       |
| XMP-x:XMPToolkit           | Image::ExifTool 11.27     |
| XMP-exif:GPSLatitude       | 54.2947963                |
| XMP-exif:GPSLongitude      | -2.2503684                |
| XMP-tiff:Copyright         | _**OWoodflint**_          |
| Composite:ImageSize        | 1920 1080                 |
| Composite:Megapixels       | 2.0736                    |
| Composite:GPSLatitudeRef   | N                         |
| Composite:GPSLongitudeRef  | W                         |
| Composite:GPSPosition      | 54.2947963 -2.2503684     |

***

#### Q2. What city is this person in? <a href="#q2-what-city-is-this-person-in" id="q2-what-city-is-this-person-in"></a>

#### Q3. What’s the SSID of the WAP he connected to? <a href="#q3-whats-the-ssid-of-the-wap-he-connected-to" id="q3-whats-the-ssid-of-the-wap-he-connected-to"></a>

After finding the targets’ Twitter account, you will find the user made a tweet with a BSSID. For this question you will need to head over to a site called [WiGLE](https://wigle.net/) _(a website for collecting information about the different wireless hotspots around the world)_. Once on the site enter the BSSID in the map search box and hit _“Filter”_. After hitting filter, zoom out on the map and head over to the marked location on the map, once you find the marked location zoom all the way in and you’ll find the answers for questions 2 (_**London**_) and 3 (_**UnileverWiFi**_).\
![img](https://i.imgur.com/HtxEDoW.png)\
![img](https://i.imgur.com/NcoGMvw.png)

***

#### Q4. What is his personal email address? <a href="#q4-what-is-his-personal-email-address" id="q4-what-is-his-personal-email-address"></a>

#### Q5. What site did you find his email address on? <a href="#q5-what-site-did-you-find-his-email-address-on" id="q5-what-site-did-you-find-his-email-address-on"></a>

The answer to questions 4 and 5 can be found by doing a Google search on the targets username and searching through the each link. Eventually you will come across their _**Github**_ page which has an _**email**_ on one of their repos.

![img](https://i.imgur.com/TTP39KC.png)

***

#### Q6. Where has he gone on holiday? <a href="#q6-where-has-he-gone-on-holiday" id="q6-where-has-he-gone-on-holiday"></a>

#### Q7. What is this persons password? <a href="#q7-what-is-this-persons-password" id="q7-what-is-this-persons-password"></a>

The last two questions can be answered by heading over to the targets WordPress blog page, the target states that they are in _**New York**_ at that point in time. Their is also hidden text on the page that is colored the same color as the background of the webpage _(if you don’t have a night mode extension enabled)_

![img](https://i.imgur.com/hJ1ssc9.png)\
![img](https://i.imgur.com/ngLwao0.png)

This was a really fun room and a great room to test your OSINT skills, OSINT is personally one of my favorite aspects of Cyber Security! 😊

### I am actively looking for work, feel free to connect with me and lets talk business. Also feedback is appreciated! Thank you! <a href="#i-am-actively-looking-for-work-feel-free-to-connect-with-me-and-lets-talk-business-also-feedback-is" id="i-am-actively-looking-for-work-feel-free-to-connect-with-me-and-lets-talk-business-also-feedback-is"></a>

***

### Connect With Me ![:slightly\_smiling\_face:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/slightly\_smiling\_face.png) <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
