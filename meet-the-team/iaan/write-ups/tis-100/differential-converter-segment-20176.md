---
cover: ../../.gitbook/assets/nv2eMzzAutRZf83whueCi-transformed.jpeg
coverY: -32.843523316062175
---

# “Differential Converter” (Segment 20176)

### Tasks <a href="#tasks" id="tasks"></a>

For the _“Differential Converter”_ _(Segment 20176)_ challenge we need to complete the following tasks:

* Read values from **IN.A** and **IN.B**.
* Write **IN.A** - **IN.B** to **OUT.P**.
* Write **IN.B** - **IN.A** to **OUT.N**.

### Solution <a href="#solution" id="solution"></a>

![](https://i.imgur.com/8nvTQdp.jpg)

To start things off let’s look at our expected output, we can see that the outputs are opposite of each other. My solution to this challenge was to take input from _IN.A_ `MOV` it to the _ACC_ register and take the input from _IN.B_, `MOV` it to node #2 and subtract it from the value in the _ACC_ register in node #2. So the first two inputs are _IN.A=44_ and _IN.B=93_ if we subtract the two values, the result will be _-49_ in node #2’s _ACC_ register. Once we have the expected result, we then `MOV` the result from the _ACC_ register to node #3 and use the _NEG_ instruction to negate whatever value that is passed from node #2. After doing these steps, majority of the logic for this challenge is done, all there is left to do now is to transfer the results from the arithmetic to their respective outputs. The sequence of commands to solve for this challenge are:

```
MOV UP, ACC     #N2
SUB RIGHT       #N2
MOV ACC, RIGHT  #N2
MOV ACC, DOWN   #N2
MOV UP, LEFT    #N3
MOV LEFT, ACC   #N3
NEG             #N3
MOV ACC, DOWN   #N3
MOV ACC, DOWN   #N6
MOV ACC, DOWN   #N7
MOV ACC, DOWN   #N10
MOV ACC, DOWN   #N11

```

After completing the following sequences, you can now press _F5_ to run and solve the program!

***

### Connect With Me 😊 <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=black)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
