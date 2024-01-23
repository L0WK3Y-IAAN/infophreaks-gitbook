---
cover: ../../.gitbook/assets/TryHackMe Logo (3).png
coverY: 0
---

# Classic Passwd - TryHackMe

<figure><img src="https://i.imgur.com/SfAaZVa.jpg" alt=""><figcaption></figcaption></figure>

### Intro <a href="#intro" id="intro"></a>

_**“I forgot my password, can you give me access to the program?”**_

In this TryHackMe room you will be tasked with cracking the password to a binary by bypassing the authentication sequence. There are multiple ways to solve this CTF, but I will go over a few of the ways I solved it.

### Scenario <a href="#scenario" id="scenario"></a>

_Practice your skills in reversing and get the flag bypassing the login._

### Questions <a href="#questions" id="questions"></a>

### Task: What is the flag? <a href="#task-what-is-the-flag" id="task-what-is-the-flag"></a>

#### Method 1: Convert the Hex Values to Decimal <a href="#method-1-convert-the-hex-values-to-decimal" id="method-1-convert-the-hex-values-to-decimal"></a>

To start things off, I pull the strings to find what catches my eye, scrolling through the strings I find _THM{ %d%d }_. After doing countless CTFs I already know that flags are typically formatted this way (e.g _flag{}, THM{}, htb{}_), _%d_ is a string format that takes an argument and prints it as an integer we will see that later on in Ghidra. You can read more about %d [**here**](https://www.quora.com/What-does-d-mean-in-the-C-programming-language?share=1).\
![img](https://i.imgur.com/5kVg9Dt.jpg)

After importing the file into Ghidra and head over to the main function we can see that two functions are called, _**vuln**_ and _**gfl**_. For this method I will only be focusing on the _gfl_ function. Once in the function we can see the printf function where the flag and the hex arguments that are being formatted into the flag string with _%d_. If we convert the hex values to decimal (0x638a78 = _**65235128496**_) and (0x2130 = _**8496**_) then append them to the string we get the full flag _**THM{652351284968496}**_.

![img](https://i.imgur.com/L8HOCH0.png)

***

#### Method 2: ltrace <a href="#method-2-ltrace" id="method-2-ltrace"></a>

For the second method I use a command line debugging utility called [**ltrace**](https://www.man7.org/linux/man-pages/man1/ltrace.1.html). After running the binary through ltrace it will ask the user to input the username. After doing so we can see that there is a _strcmp_ function called with compares the users input to the correct username (_**AGB6js5d9dkG7**_). We can test this by executing the binary again and using the same username from the comparison and we can see that it is valid and prints the flag.

![img](https://i.imgur.com/fDZNyVX.jpg)

***

#### Method 3: Swap the Jump Instruction <a href="#method-3-swap-the-jump-instruction" id="method-3-swap-the-jump-instruction"></a>

The third method involves changing the jump instruction that leads to the “_Welcome_” message and the flag. In this method we will focus on the _**vuln**_ function, this is where the user input is handled along with the if statement that handles the authentication. Below is the if statement and jump condition that handles the authentication. We can see that at address _00101261_ there is a _**JNZ**_ instruction which leads to the address _00101271_ which prints the _Authentication Failure_ message.

![img](https://i.imgur.com/ZTCB5j2.jpg)\
![img](https://i.imgur.com/YjWOeKI.jpg)

We can bypass this by switching the JNZ condition to JZ and patching the binary, which will essentially have the opposite output than that of the original program. Take a look back at the _ltrace_ screenshot, you can see that in the original binary for the first comparison the word “_test_” was entered and was compared with the expected input the program returned a status code of _51_. When the correct username is entered and compared the status code is 0. By swapping the jump condition, the user can input the wrong username, and the program will still print the _Welcome_ message and flag.

![img](https://i.imgur.com/pgkiWaw.jpg)\
![img](https://i.imgur.com/FaKQM7F.jpg)

### I am actively looking for work, feel free to connect with me and lets talk business. Also feedback is appreciated! Thank you! <a href="#i-am-actively-looking-for-work-feel-free-to-connect-with-me-and-lets-talk-business-also-feedback-is" id="i-am-actively-looking-for-work-feel-free-to-connect-with-me-and-lets-talk-business-also-feedback-is"></a>

***

### Connect With Me ![:slightly\_smiling\_face:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/slightly\_smiling\_face.png) <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
