---
cover: ../../.gitbook/assets/TryHackMe Logo (3).png
coverY: 0
---

# Welcome to the Searchlight IMINT room! - TryHackMe

<figure><img src="https://i.imgur.com/jmKHOYC.png" alt=""><figcaption></figcaption></figure>

### TryHackMe - Welcome to the Searchlight IMINT room! | IAANSEC <a href="#welcome-to-the-searchlight-imint-room" id="welcome-to-the-searchlight-imint-room"></a>

In this room we will be exploring the discipline of IMINT/GEOINT, which is short for Image intelligence and geospatial intelligence. This room is suited for those of you who are just beginning your OSINT journey or those brand new to the field of IMINT/GEOINT.

**This room will introduce you to several topics within IMINT, among them:**

* Getting into the right mindset and how to be analytical.
* Visually extracting key data points from an image or video.
* Applying different tools to assist you in geolocation and answering context questions.

When you have completed this room you should be comfortable applying tools and methodologies to geolocate and answer context questions based on visual intelligence alone. This room will prepare you for harder CTF challenges in this category as well as real-world geolocation work.

Any thoughts, feedback or issues can be forwarded to me directly on the THM or Searchlight Discord. You’ll find me there as zewen.

The flag format is: `sl{flag}` - this means that every answer needs to be submitted within the brackets, sl{your answer}. No capitalization is needed.

If you are stuck or you want someone to discuss these challenges with, head on over to the OSINT Curious [Discord server](https://discord.gg/gX4KeWT). You can also find me on [Twitter](https://twitter.com/Zewensec) if you have any questions!

***

### Questions <a href="#questions" id="questions"></a>

### Task 2: “Your first challenge!” <a href="#task-2-your-first-challenge" id="task-2-your-first-challenge"></a>

![image alt](https://i.imgur.com/0fyTA20.jpg)

#### Q1: What is the name of the street where this image was taken? <a href="#q1-what-is-the-name-of-the-street-where-this-image-was-taken" id="q1-what-is-the-name-of-the-street-where-this-image-was-taken"></a>

With this being an introductory question, the answer is pretty straightforward. The street name is on the sign **Carnaby Street**.

***

### Task 3: “Just Google It!” <a href="#task-3-just-google-it" id="task-3-just-google-it"></a>

\
For starters I won’t be using reverse image search, because where’s the fun in that. Instead I will explain the thought process I had while analyzing the image. With that said, the first thing I noticed was the European architecture of the buildings in the background. Next, I noticed the _Circus St…_ on the sign above the stairway. After doing a Google search with the information gathered _Public Subway Underground Circus Station_, I was able to obtain the information needed to answer the questions.

<figure><img src="https://i.imgur.com/FXMcv4E.jpg" alt=""><figcaption></figcaption></figure>

#### Q1: Which city is the tube station located in? <a href="#q1-which-city-is-the-tube-station-located-in" id="q1-which-city-is-the-tube-station-located-in"></a>

The station is located in **London**.

#### Q2: Which tube station do these stairs lead to? <a href="#q2-which-tube-station-do-these-stairs-lead-to" id="q2-which-tube-station-do-these-stairs-lead-to"></a>

The first result shown after the Google search was a Wiki page for **Piccadilly Circus**, which lines up with the circus portion of the sign.

#### Q3: Which year did this station open? <a href="#q3-which-year-did-this-station-open" id="q3-which-year-did-this-station-open"></a>

_“Piccadilly Circus tube station was opened on 10 March **1906**, on the Bakerloo line, and on the Piccadilly line in December of that year.”_ - [Wikipedia](https://en.wikipedia.org/wiki/Piccadilly\_Circus)

#### Q4: How many platforms are there in this station? <a href="#q4-how-many-platforms-are-there-in-this-station" id="q4-how-many-platforms-are-there-in-this-station"></a>

Googling _“How many platforms are there in Piccadilly Circus?”_ returns **4**.

***

### Task 4: “Keep at it!” <a href="#task-4-keep-at-it" id="task-4-keep-at-it"></a>

![image alt](https://i.imgur.com/pM6NyT1.png)

Right off the bat I see a banner which says _“YVR Connects”_ and _“YVR.**CA**”_ which leads me to think this building is located in Canada. This is enough intel for me to start doing some research.

#### Q1: Which building is this photo taken in? <a href="#q1-which-building-is-this-photo-taken-in" id="q1-which-building-is-this-photo-taken-in"></a>

After searching _“YVR Connects”_ on Google, the first result I was presented with was the [**Vancouver International Airport**](https://en.wikipedia.org/wiki/Vancouver\_International\_Airport) Wikipedia page.

#### Q2: Which country is this building located in? <a href="#q2-which-country-is-this-building-located-in" id="q2-which-country-is-this-building-located-in"></a>

**Canada**

#### Q3: Which city is this building located in? <a href="#q3-which-city-is-this-building-located-in" id="q3-which-city-is-this-building-located-in"></a>

_“Vancouver International Airport (IATA: YVR, ICAO: CYVR) is a Transport Canada designated international airport\[5] located on Sea Island in **Richmond**, British Columbia.”_

***

### Task 5: “Coffee and a light lunch” <a href="#task-5-coffee-and-a-light-lunch" id="task-5-coffee-and-a-light-lunch"></a>

![image alt](https://i.imgur.com/ieseamd.png)

This task requires you to do a bit more searching than the others. After searching the name of the store across the street, _“The Edinburgh Wollen Mill”_ You are presented with numerous results. My approach to near down the choices was by adding “Coffee shops near…” at the start of the inital Edinburgh search. After doing so, a couple coffee shops popped up in the results, but I narrowed my choices down to two coffee shops **“The Wee Coffee Shop”** and _“Courtyard Coffee Shop”_. I made my final decision by doing a Google Street View for both coffee shop and The Wee Coffee Shop was the right coffee shop. With that I was able to gather the intel needed to answer the questions.

#### Q1: Which city is this coffee shop located in? <a href="#q1-which-city-is-this-coffee-shop-located-in" id="q1-which-city-is-this-coffee-shop-located-in"></a>

1 Allan St, **Blairgowrie** PH10 6AB, United Kingdom

#### Q2: Which street is this coffee shop located in? <a href="#q2-which-street-is-this-coffee-shop-located-in" id="q2-which-street-is-this-coffee-shop-located-in"></a>

1 **Allan St**, Blairgowrie PH10 6AB, United Kingdom

#### Q3: What is their phone number? <a href="#q3-what-is-their-phone-number" id="q3-what-is-their-phone-number"></a>

**+447878839128**

#### Q4: What is their email address? <a href="#q4-what-is-their-email-address" id="q4-what-is-their-email-address"></a>

[**theweecoffeeshop@aol.com**](mailto:theweecoffeeshop@aol.com) (Can be found on their Facebook page which is linked on their businesses Google maps panel.)

#### Q5: What is the surname of the owners? <a href="#q5-what-is-the-surname-of-the-owners" id="q5-what-is-the-surname-of-the-owners"></a>

Debbie and David **Cochrane** (Can be found by searching _“The Wee Coffee Shop Owners”_)

### Task 6: “Reverse your thinking” <a href="#task-6-reverse-your-thinking" id="task-6-reverse-your-thinking"></a>

![image alt](https://i.imgur.com/ND3iOOg.jpg)

This task will require you to do a reverse image search since there is no text that stands out in the image. The quickest way to do an reverse image search is by dragging and dropping the image into the Google search bar. After doing so you will be presented **“Katz’s Delicatessen”**

#### Q1: Which restaurant was this picture taken at? <a href="#q1-which-restaurant-was-this-picture-taken-at" id="q1-which-restaurant-was-this-picture-taken-at"></a>

**Katz’s Deli**

#### Q2: What is the name of the Bon Appétit editor that worked 24 hours at this restaurant? <a href="#q2-what-is-the-name-of-the-bon-appetit-editor-that-worked-24-hours-at-this-restaurant" id="q2-what-is-the-name-of-the-bon-appetit-editor-that-worked-24-hours-at-this-restaurant"></a>

**Andrew Knowlton** (Can be found by searching _“Katz’s Deli Bon Appétit Editor”_)

### Task 7: “Locate this sculpture” <a href="#task-7-locate-this-sculpture" id="task-7-locate-this-sculpture"></a>

\
For this task I started off with another reverse image search on Google. After doing so the first link to pop up was ![Visit Oslo](https://www.visitoslo.com/en/articles/outdoor-sculptures-in-oslo/). In the description of the URL before clicking it, there is a mention of **“Rudolph the Chrome Nosed Reindeer”**. Once on the site scroll down until you are presented with a map. Once the map is displayed click on the marker that is beneath _TJUVHOLMEN_. After clicking on the correct marker, a side panel will be displayed with name of the sculpture and the name of photographer.

<figure><img src="https://i.imgur.com/0LLAPO0.jpg" alt=""><figcaption></figcaption></figure>

![](https://i.imgur.com/dUS0Uh2.png)

#### Q1: What is the name of this statue? <a href="#q1-what-is-the-name-of-this-statue" id="q1-what-is-the-name-of-this-statue"></a>

**Rudolph the Chrome Nosed Reindeer**

#### Q2: Who took this image? <a href="#q2-who-took-this-image" id="q2-who-took-this-image"></a>

**Kjersti Stensrud**

### Task 8: “…and justice for all” <a href="#task-8-...and-justice-for-all" id="task-8-...and-justice-for-all"></a>

\
Once I opened the image, the first thing that stood out to me was _The Verge_ watermark in the bottom right corner. I made sure to keep the watermark in mind once proceeding to the reverse image search. After doing a RIS I realized that I can’t always rely on JUST Google RIS, it gave me results differing from Bing’s RIS. On Google the RIS returned the name _“Blind Justice Man”_, Bing returned **“Lady Justice”**. After a bit of scrolling through the related images on Bing my trail went cold. My thought process was to see if I could find any images of the statue from a wider angle to see if I could possibly find the building name. So I decided to transition over to Yandex and do a RIS there, I had better luck there because I found this as a related image

&#x20;![](https://diff.wikimedia.org/wp-content/uploads/2016/04/albert\_v\_bryan\_federal\_district\_courthouse\_-\_alexandria\_va\_-\_0018\_-\_2012-03-10.jpg)\
On Yandex you can search by image fragment, doing this you can crop just the text in the image and search for related images based on that fragment. After searching by fragment, I found this related image.\
![](https://static.politico.com/dims4/default/8c15ed8/2147483647/resize/1160x%3E/quality/90/?url=https%3A%2F%2Fstatic.politico.com%2Faa%2Fc9%2F7e4f93804e29b8499de680406967%2F190924-alexandria-courthouse-gty-773.jpg)

<figure><img src="https://i.imgur.com/LK0OmEK.png" alt=""><figcaption></figcaption></figure>

We can now see the text _“T V. Bryan United States Court”_. I then search, _“V. Bryan United States Court”_ on Yandex since I’m already on the site, and was then presented with the full name of the courthouse and it’s location. With that, I gathered enough information to answer the last question.\
![](https://i.imgur.com/bZbzorB.png)\
Now that I had the name of the court I went to Google Maps Street View and got the name of the building opposite of the courthouse.

![](https://i.imgur.com/0YXQVW2.jpg)

#### Q1: What is the name of the character that the statue depicts? <a href="#q1-what-is-the-name-of-the-character-that-the-statue-depicts" id="q1-what-is-the-name-of-the-character-that-the-statue-depicts"></a>

**Lady Justice**

#### Q2: Where is this statue located? <a href="#q2-where-is-this-statue-located" id="q2-where-is-this-statue-located"></a>

**Alexandria, Virginia**

#### Q3: What is the name of the building opposite from this statue? <a href="#q3-what-is-the-name-of-the-building-opposite-from-this-statue" id="q3-what-is-the-name-of-the-building-opposite-from-this-statue"></a>

**The Westin Alexandria Old Town**

### Task 9: “The view from my hotel room” <a href="#task-9-the-view-from-my-hotel-room" id="task-9-the-view-from-my-hotel-room"></a>

For this task, we are presented with a [video](https://www.youtube.com/embed/Yjj7MNj08ic) to analyze. A couple seconds into the video we can see a building with the sign _“Riverside Point”_. We can pause the video at this frame, screenshot it and do a RIS on this frame.

![](https://i.imgur.com/U4DBQfi.png)

On Yandex I was presented with this related image, on the bottom left we can see the location of the building.\
![](https://altermama.ru/wp-content/uploads/2015/12/IMG\_0411.jpg)\
Now that I know the location of the building, I do a search on Google Maps for _“Riverside Point Singapore”_. Once I’ve navigated to the location, I head back over to the video to have a look at the angle the Riverside Point building was recorded from. I’ve marked the location I believe the video was recorded from on the map.\
![](https://i.imgur.com/9Fi7eH6.png)\
I then confirmed my suspicions by heading into street view to have a look at the building. Google Street View’s last update of this building shows it was under construction as of Febuary 2021.

![](https://i.imgur.com/bYuCEGu.jpg)

Although, after searching around the building in Street View, if you click on this entrance to the construction site\
![](https://i.imgur.com/DUfe8BE.jpg)

It actually reveals an older 3D street view from 2018 before the construction. Once I came across the older street view model, I then noticed the name _“Tanyoto”_. I then searched “Tanyoto Singapore Hotel”, and was given the result [**Novotel Clarke Quay** - Singapore, 177a Riv Vly Rd](https://unilocal.net/singapore/singapore/novotel-clarke-quay). My guess is Tanyoto is the older name of the hotel before it’s reconstruction.

![](https://i.imgur.com/e01oYIb.jpg)

#### Q1: What is the name of the hotel that my friend is staying in? <a href="#q1-what-is-the-name-of-the-hotel-that-my-friend-is-staying-in" id="q1-what-is-the-name-of-the-hotel-that-my-friend-is-staying-in"></a>

**Novotel Singapore Clarke Quay**

### Connect With Me ![:slightly\_smiling\_face:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/slightly\_smiling\_face.png) <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
