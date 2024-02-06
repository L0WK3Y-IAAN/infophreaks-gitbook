---
cover: ../../.gitbook/assets/TryHackMe Logo (3).png
coverY: 0
---

# REloaded - TryHackMe

<figure><img src="https://i.imgur.com/7XRakgP.jpg" alt=""><figcaption></figcaption></figure>

### TryHackMe - REloaded | IAANSEC <a href="#reloaded" id="reloaded"></a>

### Intro <a href="#intro" id="intro"></a>

_**“This room is dedicated for the RE challenges, each challenge has unique concepts divided in each binaries. As if now only phase 1 is added will decide about phase 2 on response. Developed by WhiteHeart and tested by IslaMukheef”**_

In this TryHackMe room, you will be tasked with cracking various executables and at each level, the challenges gradually increase in difficulty. This will test your skills as a reverse engineer.

_**-Windows OS**_\
_**-Ghidra**_\
_**-x64dbg**_

### Questions <a href="#questions" id="questions"></a>

{% hint style="info" %}
#### Task 1: This challenge is the most basic of RE. It will teach about how to enumerate files and get juicy details. <a href="#task-1-this-challenge-is-the-most-basic-of-re-it-will-teach-about-how-to-enumerate-files-and-get-jui" id="task-1-this-challenge-is-the-most-basic-of-re-it-will-teach-about-how-to-enumerate-files-and-get-jui"></a>
{% endhint %}

Like every reverse engineering CTF, I started things off by pulling strings from the executable to see what caught my eye. After searching for strings in Ghidra I found 1 string that looks like a flag that was referenced in the function _**FUN\_00401410**_ and address _**0040142b**_ and 2 that looks like an output string after a comparison is made between the correct string and the users' input, 1 more string that tells the user to enter the flag.\


<figure><img src="https://imgur.com/Vlg2YiR.png" alt=""><figcaption></figcaption></figure>

After navigating to the address where the “Enter The Flag” string is referenced I am now presented with what you see below in the decompiler. After analyzing the information I was able to deduce that `char local_40 [20];` must be the variable that holds the user's input since it is only allowed 20 bytes and the flag itself is 18 bytes. There were also a few empty functions, but looking towards the bottom we can see the same function where the flag string was referenced.

![img](https://i.imgur.com/tjS2c4d.jpg)

After heading to that function I was presented with this in the decompiler. It’s safe to assume that this must be the flag check function. On lines 9 and 11, it looks like the author of this program created callback functions that act similarly to how the strcpy and strcmp functions work.\
![img](https://i.imgur.com/eKMDqbu.jpg)\
I went ahead and renamed the functions accordingly as you can see below. On line 9 the flag string is copied into the variable _local\_28_. On line 11 the strcmp\_callback function is used to compare _param\_1_ (the users' input) to _local\_28_ (the flag variable). If at any point the users' input gets null-terminated in the comparison process the string _“Dont Worry its a start ;)”_ is printed to the terminal, if the users’ input and flag variable match, the string _“That was easy…Bruh!!!”_ is printed to the terminal.\
![img](https://i.imgur.com/iOMJji1.jpg)

***

{% hint style="info" %}
#### Task 2: Level 0 was a piece of cake for you now I am keeping my cake in the cage. <a href="#task-2-level-0-was-piece-of-cake-for-you-now-i-am-keeping-my-cake-in-the-cage" id="task-2-level-0-was-piece-of-cake-for-you-now-i-am-keeping-my-cake-in-the-cage"></a>
{% endhint %}

Again I start by pulling strings and come across a string named _“Thats your lucky number !!!”_ which is referenced in function _**FUN\_00401410**_.\
![img](https://i.imgur.com/2wnMtyS.jpg)

After heading to the function where the string was referenced I was presented with this code in the decompiler, as you can see the function takes a parameter as an integer if the parameter is equal to the hex value on line 5, we get the lucky number string that was referenced. All we have to do is convert the hex to decimal to get the answer.\
![image alt](https://i.imgur.com/txgJlgV.jpg)

***

After pulling strings from the binary I found one interesting string _“Wow Ur At L3?”_ after navigating to the function where the string is located (_**FUN\_004014cb**_) I was presented with this in the decompiler.\
![image alt](https://i.imgur.com/AfYJcZR.png)\
_FUN\_0040147f_ on line 13 is just an empty function. _**FUN\_00401410**_ leads to the function that creates the flag string. After navigating to that function, I was presented with this code in the decompiler. I converted all the local variables from hex to ASCII to see what value was returned, after doing so I was given the ASCII value: `1_3L02_shT_t1L_3t13`. So I tried entering that as the flag and it was incorrect so I figured each hex value must be reversed. After reversing the ASCII values and running it against the executable, the program printed the _“Get Ready For L4 ;)”_ string along with the correct flag.\
![image alt](https://i.imgur.com/ziIekAZ.png)

Another method of solving this task would be switching the `JG` instruction. at address _004014d9_ we can see there is a comparison between the hex value 0x1 and the 32bit value located at the address `[EBP + param_1]`. On the next line, we can see if 0x1 was greater than `[EBP + param_1]`, then a jump is made to address _004014f2_. If you change the JG instruction to JNE or JNZ, the program will move the function that prints the flag since the conditions have changed.\
![image alt](https://i.imgur.com/9YCyI7Z.png)

Now that the jump instruction has been changed, the decompiler should read as follows:\
![image alt](https://i.imgur.com/ULAqaNS.png)

***

#### Task 4: Bob was fired due to his inappropriate behavior with colleagues. While leaving he deleted the code which decrypts the password stored in the code. As a reverse engineer, it’s your task to recover that master password since the code is in prod now and can't be modified but you have a copy of the app. Everything depends on you now !!! <a href="#task-4-bob-was-fired-due-to-his-inappropriate-behavior-with-colleagues-while-leaving-he-deleted-the" id="task-4-bob-was-fired-due-to-his-inappropriate-behavior-with-colleagues-while-leaving-he-deleted-the"></a>

After pulling strings I found the string _“Rooted !!!”_ after heading to the function where the string was located, I was presented with this in the decompiler. Upon examining the code in the decompiler, I was able to make an educated guess at what the functions and variables are. Below are before and after images.\
![image alt](https://i.imgur.com/VjzCsr2.png)\
![image alt](https://i.imgur.com/jlEjSX9.png)

I only renamed the functions and variables that seemed important to me also I wasn’t entirely sure what local\_28 is and what line 13 of the code does, but I was still able to solve the challenge without knowing what they are. As for the _**xor\_string\_func**_ was able to conclude that this was an xor function seeing how the program behaves in a debugger. I felt the most logical place to set a breakpoint would be at the start of the XOR function that way I can see the flag string before it gets ciphered. The XOR function begins at the address `00401410`. In x64dbg hit Run until the program reaches the point where it asks you to enter the flag, after entering the wrong flag, step over to the next instruction until the debugger jumps to the XOR function breakpoint. From there continue to step over until you see the flag in the EAX register.

![image alt](https://i.imgur.com/lywijEX.png)\
![image alt](https://i.imgur.com/rZRXWtV.jpg)

***

#### Task 5: They are back!!! and using some sort of encryption algorithm to communicate. Although we intercepted their messages we can't decode them, Agent 35711 has successfully stolen their test encryption code. Now it’s on you to build a decryptor for test messages and save this world. <a href="#task-5-they-are-back-and-using-some-sort-of-encryption-algorithm-to-communicate-although-we-intercep" id="task-5-they-are-back-and-using-some-sort-of-encryption-algorithm-to-communicate-although-we-intercep"></a>

Alright, so this time pulling strings returns nothing of value but when executing the program it prints this in the console _**“Amcm↨QBuYP+lD↨V1pvYBdR”.**_ Just by looking at this string, I can tell it is being encrypted by an algorithm at some point in the program. So I figured since the string is being encrypted and printed to the console, I could see where the `printf` function was being used in the program. In Ghidra click on _“Display Symbol Tree”_ and search for and click _“printf”._ From there follow the XREFs until you land at the function where the printf function was used _**(FUN\_00401453)**_.

Once I arrived at the function where printf was referenced, I was presented with this in the decompiler. After analyzing the function and comparing it to the program behavior in the debugger, I was able to make an educated guess at what each variable is. Below are before and after pictures of the function.

![link text](https://i.imgur.com/ZvPwPyD.png)\
![image alt](https://i.imgur.com/2oRGZzD.png)

It looks like the function gets the length of the flag, and performs a preliminary check on lines 10-11 if the string meets certain requirements, the encryption algorithm is run against the flag string. Skipping ahead a bit, if you set a breakpoint at the start of the address where the function is located _**(00401453)**_, the flag will be displayed in memory before it is run through the encryption algorithm.

![image alt](https://i.imgur.com/8HFUABN.gif)

That concludes this write-up if you have any feedback, feel free to comment. Feedback is always appreciated and will help me learn and grow 😊.

### Connect With Me ![:slightly\_smiling\_face:](https://cdn.jsdelivr.net/npm/@hackmd/emojify.js@2.1.0/dist/images/basic/slightly\_smiling\_face.png) <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
