---
cover: ../../.gitbook/assets/nv2eMzzAutRZf83whueCi-transformed.jpeg
coverY: -33.01139896373057
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# “Self-Test Diagnostic” (Segment 00150)

### Tasks <a href="#tasks" id="tasks"></a>

For the first challenge _“Self-Test Diagnostic” (Segment 00150)_ we need to complete the following task:

* Read a value from **IN.X** and write the value to **OUT.X**.
* Read a value from **IN.A** and write the value to **OUT.A**.

### Solution <a href="#solution" id="solution"></a>

![](https://i.imgur.com/N9gKknA.jpg)

This challenge will help you understand how to transfer input data from one node to another. _IN.X_ sends data to node #1 and needs to be transfered to _OUT.X_ below node #9. _IN.A_ sends data to node #4 and needs to be transfered to _OUT.A_ below node #12. To solve for _Ouput.X_, we need to `MOV` the data being inputed from _IN.X_ which is above node #1 `UP` and move it `DOWN` to node #5 and so on and so forth. The sequence of commands to transfer _IN.X_ to _OUT.X_ is:

```
MOV UP, DOWN #N1
MOV UP, DOWN #N5
MOV UP, DOWN #N9
```

To solve for Ouput.A we have to work around node #8 since there is a communcation failure and can not be accessed. The sequence of commands to solve for OUT.A are:

```
MOV UP, LEFT    #N4
MOV RIGHT, DOWN #N3
MOV UP, DOWN    #N7
MOV UP, RIGHT   #N11
MOV LEFT, DOWN  #N12
```

After completing the following sequences, you can now press _F5_ to run and solve the program!

***

### Connect With Me 😊 <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
