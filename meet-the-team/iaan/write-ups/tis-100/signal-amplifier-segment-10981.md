---
cover: ../../.gitbook/assets/nv2eMzzAutRZf83whueCi-transformed.jpeg
coverY: -34.75025906735751
---

# “Signal Amplifier” (Segment 10981)

### Tasks <a href="#tasks" id="tasks"></a>

For the second challenge _“Signal Amplifier”_ _(Segment 10981)_ we need to complete the following tasks:

* Read a value from **IN.A**.
* Double the value.
* Write the value to **OUT.A**.

### Solution <a href="#solution" id="solution"></a>

![](https://i.imgur.com/hvA3eM3.jpg)

In the _“Signal Amplifier”_ challenge, we are introduced to the `ADD` instruction and the `ACC` register. As you can see in the image above the output is expecting the value to be double that of the input. We can start by moving the value from _IN.A_ to the _ACC_ register in node #2. After moving the input value to _ACC_ we want to double the value, we can do this by adding the value stored in the _ACC_ register to itself. Once the value is doubled we can then transfer that value to the output. The sequence of commands to solve for _OUT.A_ are:

```
MOV UP, ACC     #N2
ADD ACC         #N2
MOV ACC, DOWN   #N2
MOV UP, DOWN    #N6
MOV UP, RIGHT   #N10
MOV LEFT, DOWN  #N11
```

After completing the following sequences, you can now press _F5_ to run and solve the program!

***

### Connect With Me 😊 <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
