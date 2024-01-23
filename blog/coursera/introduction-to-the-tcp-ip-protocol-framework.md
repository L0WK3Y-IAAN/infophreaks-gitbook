---
cover: ../../.gitbook/assets/Coursera-logo-square-compressor-600x330 (2).png
coverY: 0
---

# Introduction to the TCP/IP Protocol Framework

<figure><img src="https://1.bp.blogspot.com/-n9EozspLgds/X4hRjzryqWI/AAAAAAAAAbc/WkUoZ0l1QOwum-y81BPLhI7QtLaKuCbSQCNcBGAsYHQ/s0/Introduction%2Bto%2BCybersecurity%2BTools%2B%26%2BCyber%2BAttacks.png" alt=""><figcaption></figcaption></figure>

Alright, time to dive into one of the most important parts of cybersecurity. NETWORKING! This blog will teach about network basics of TCP/IP and OSI models, DNS, and DHCP, as well as switching and routing concepts, IP addressing, NAT, packet sniffing, and finally, structures and vulnerabilities of key databases including SQL, CouchDB, Oracle, and MongoDB. Let's get started!

### Stateless Inspection <a href="#stateless-inspection" id="stateless-inspection"></a>

To start the topic of networking let's discuss what firewalls are and how they utilize stateless and stateful inspection, then compare stateless firewalls to stateful firewalls. According to Cisco (one of the leading companies in network technology), firewalls are ["A firewall is a network security device that monitors incoming and outgoing network traffic and decides whether to allow or block specific traffic based on a defined set of security rules. Firewalls have been a first line of defense in network security for over 25 years. They establish a barrier between secured and controlled internal networks that can be trusted and untrusted outside networks, such as the Internet. A firewall can be hardware, software, or both."](https://www.cisco.com/c/en/us/products/security/firewalls/what-is-a-firewall.html). Now that we know what a firewall is, let's dig a little deeper into how firewalls filter incoming and outgoing network traffic with stateless and stateful inspection. Regular routers and some firewalls use the stateless way of filtering packets, this means the firewall inspects each packet without any knowledge of previous packets, the firewall will inspect the destination and source address of the packet and then block or restrict addresses that are deemed untrusted. There may also be an Access Control List rule (ACL) that will determine whether the source address and destination port of the packet is allowed on the network or if the destination address is allowed to be accessed or not. A few use cases for stateless inspection include:

* Protecting routing engine resources.
* Controlling traffic going in or out of your organization.
* Troubleshooting purposes.
* Control traffic routing (through the use of routing instances).
* Perform QoS/CoS (marking the traffic).

<figure><img src="https://1.bp.blogspot.com/-Plax-qDFvd0/X4hqY2HL6zI/AAAAAAAAAbw/1nDrm9sX4m4RzZqN4wBJerbhkN2juDdDQCNcBGAsYHQ/s0/2020-10-15%2B11_26_53-Meet%2B-%2Bpsc-oknk-aor%2B-%2BBrave.png" alt=""><figcaption></figcaption></figure>

### Stateful Inspection <a href="#stateful-inspection" id="stateful-inspection"></a>

Heading back over to Cisco, a Stateful Inspection is ["Now thought of as a “traditional” firewall, a stateful inspection firewall allows or blocks traffic based on state, port, and protocol. It monitors all activity from the opening of a connection until it is closed. Filtering decisions are made based on both administrator-defined rules as well as context, which refers to using information from previous connections and packets belonging to the same connection."](https://www.cisco.com/c/en/us/products/security/firewalls/what-is-a-firewall.html). In some cases there can be a stateless and stateful inspection, the stateless inspection is going to be performed first and then will be followed up by an evaluation of the stateful data. Now that we know about stateless and stateful inspections what are the pros and cons of each method? Below is a list of the pros and cons of each inspection method courtesy of [CDW](https://www.cdw.com/content/cdw/en/articles/security/2019/04/29/stateful-versus-stateless-firewalls.html).\


<figure><img src="https://1.bp.blogspot.com/-synnIT0Ty3Q/X4oe7p0iUqI/AAAAAAAAAcU/SXdlNJfdT2EOUzb1M5uYr0LEHANuvA5ugCNcBGAsYHQ/s0/2020-10-16%2B18_29_33-Stateful%2Bvs%2BStateless%2BFirewalls%2B-%2BWhat%27s%2Bthe%2BDifference_%2B_%2BCDW%2B-%2BBrave.png" alt=""><figcaption></figcaption></figure>

### IDS and IPS Systems <a href="#ids-and-ips-systems" id="ids-and-ips-systems"></a>

Now that we've talked about firewalls and the different types of firewalls, let's talk a little about 2 types of firewall filters. Intrusion Detection and Intrusion Prevention Systems. An Intrusion Detection System (IDS) ["is a network security technology originally built for detecting vulnerability exploits against a target application or computer."](https://www.paloaltonetworks.com/cyberpedia/what-is-an-intrusion-detection-system-ids). Intrusion Prevention Systems (IPS) ["extended IDS solutions by adding the ability to block threats in addition to detecting them and has become the dominant deployment option for IDS/IPS technologies."](https://www.paloaltonetworks.com/cyberpedia/what-is-an-intrusion-detection-system-ids).

\


### Intrusion Detection Systems <a href="#intrusion-detection-systems" id="intrusion-detection-systems"></a>

An IDS needs to only detect threats on a network because the IDS only detects threats and reports its findings to an administrator. It is placed outside of the real-time communication path of the sender and receiver of information, which makes it a passive system. Due to the IDS not keeping up with real-time communication, it will often take advantage of a TAP or SPAN port to analyze a copy of the inline network traffic stream. This ensures that the IDS does not impact inline network performance. Unfortunately due to the nature of IDS solutions, they cannot prevent a detected exploit from taking over the system. Attackers are capable of quickly exploiting vulnerabilities once they've infiltrated the network. Rendering the IDS is useless.

\


### Intrusion Prevention Systems <a href="#intrusion-prevention-systems" id="intrusion-prevention-systems"></a>

IPS on the other hand, can block threats along with detecting them. The IPS often sits directly behind the firewall and adds a layer of analysis that actively searches for dangerous content. The IPS sites inline or in the direct path of communication of the sender and receiver and take automated actions on all traffic flows that enter the network. The actions performed by an IPS include:

* Sending an alarm to the administrator(as would be seen in an IDS)
* Dropping the malicious packets
* Blocking traffic from the source address
* Resetting the connection

Since the IPS works as an inline security component, the IPS must work fast and efficiently to avoid degrading network performance as well as detect and respond to exploits accurately since exploits can happen in near real-time. When it comes to detection methods IPS has several different detection methods but signature-based and statistical anomaly-based are the two dominant methods. Signature-based detection ["is based on a dictionary of uniquely identifiable patterns (or signatures) in the code of each exploit. As an exploit is discovered, its signature is recorded and stored in a continuously growing dictionary of signatures. Signature detection for IPS breaks down into two types:"](https://www.paloaltonetworks.com/cyberpedia/what-is-an-intrusion-prevention-system-ips)\


* Exploit-facing signatures identify individual exploits by triggering the unique patterns of a particular exploit attempt. The IPS can identify specific exploits by finding a match with an exploit-facing signature in the traffic stream
* Vulnerability-facing signatures are broader signatures that target the underlying vulnerability in the system that is being targeted. These signatures allow networks to be protected from variants of an exploit that may not have been directly observed in the wild but also raise the risk of false positives.

Statistical anomaly detection ["takes samples of network traffic at random and compares them to a pre-calculated baseline performance level. When the sample of network traffic activity is outside the parameters of baseline performance, the IPS takes action to handle the situation."](https://www.paloaltonetworks.com/cyberpedia/what-is-an-intrusion-prevention-system-ips)

<figure><img src="https://1.bp.blogspot.com/-lJd-kS_8X_c/X7Ml90BKByI/AAAAAAAAAjg/Ao6uFLgMNxswPZbYOu1t726BIxgxyWrJQCNcBGAsYHQ/s0/2020-11-16%2B20_00_53-The%2BDifference%2Bbetween%2BIDS%2Band%2BIPS%2BSystems%2B_%2BCoursera%2B-%2BBrave.png" alt=""><figcaption></figcaption></figure>

\


### Network Address Translation <a href="#network-address-translation" id="network-address-translation"></a>

NAT or Network Address Translation is essentially a method of converting a private IP address to a public IP address when connecting to the Internet. NAT remaps the IP address by modifying information in the IP datagram packet headers as they transit across a traffic routing device. This is just a summary of what NAT is but you can read more about it through a FAQ form on CISCO's website [Network Address Translation (NAT) FAQ](https://www.cisco.com/c/en/us/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html). Below is a diagram of a Juniper NAT router and 4 key facts about NAT.

<figure><img src="../../.gitbook/assets/2020-11-16_21_09_35-Network_Address_Translation___Coursera_-_Brave-transformed.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://1.bp.blogspot.com/-1uf45QYEek4/X7M9Ey_UZlI/AAAAAAAAAj4/QWhlYhsOx7cZj9lsEadV7lWJ1HIBH_yzQCNcBGAsYHQ/s0/2020-11-16%2B22_00_58-Network%2BAddress%2BTranslation%2B_%2BCoursera%2B-%2BBrave.png" alt=""><figcaption></figcaption></figure>

### Static, Dynamic, and PAT Address <a href="#static-dynamic-and-pat-address" id="static-dynamic-and-pat-address"></a>

* Static NAT- Allows one-to-one mapping between local and global addresses.
* Dynamic NAT- A technique in which multiple public IP addresses are mapped to a local IP address to be used.
* Port Address Translation (PAT) - Maps multiple local IP addresses to a single public address to conserve IP addresses. This method is often referred to as "Overloading". By using overloading, thousands of users can be connected to the Internet by using only one real public IP address.

***

### Connect With Me 😊 <a href="#connect-with-me" id="connect-with-me"></a>

[![Website](https://img.shields.io/website?label=IAANSec\&style=for-the-badge\&url=https%3A%2F%2Fiaansec.com\&color=green)](https://iaansec.com/) [![Website](https://img.shields.io/website?label=dev.to\&style=for-the-badge\&url=https%3A%2F%2Fdev.to/l0wk3y\&color=orange)](https://dev.to/l0wk3y) [![Website](https://img.shields.io/website?label=GitHub\&style=for-the-badge\&url=https%3A%2F%2Fgithub.com/l0wk3y\&color=yellow)](https://github.com/L0WK3Y-IAAN) [![Website](https://img.shields.io/website?label=LinkedIn\&style=for-the-badge\&url=https%3A%2F%2Flinkedin.com/in/l0wk3yiaansec\&color=blue)](https://www.linkedin.com/in/l0wk3yiaansec)
