---
layout: page
title: About SoNIC
excerpt: ""
modified: 2015-02-18
---

## What is SoNIC:
SoNIC, Software-defined Network Interface Card, provides users with unprecedented flexible realtime access to the physical layer from software. In essence, SoNIC implements the physical layer in software to access and control every bit from the physical layer of 10 Gigabit Ethernet.

## Why access to the physical layer?
The physical and data link layers of the network stack offer untapped potentioal to systems programmers and network researchers. In particular, idle characters (/I/) that only reside in the physical layer can be used to accurately measure interpacket delays. Unfortunately, the physical and data link layers are usually implemented in hardware and not easily accessible to systems programmers. Further, systems programmers often treat them as a black box. Commodity network interface cards do not provide nor allow an interface for users to access the PHY. Consequently, operating systems cannot access the physical leyr either.

## How to use SoNIC?
Followings are required to use SoNIC:

* An [compatible]({{site-url}}/user-guide) FPGA development board
* A server/workstation equipped CPUs with PCIe Gen 2.0 and higher, and with Carry-less Multiplication instruction, e.g. Intel Westmere, Sandy-bridge, and Ivy Bridge. (SoNIC is currently tested with Westmere architecture.)
* SFP+ transceivers and optic fibers

<a markdown="0" href="{{ site.url }}/user-guide" class="btn">Build SoNIC</a>

## What to do with SoNIC?
Access to the physical layer allows network researchers to perform precise network measurements at the sub-nanosecond scale. Thus, network research based on interpacket delays/gaps can benefit from this unprecedented access. For example, SoNIC can generate packets precisely controlling interpacket gaps, can capture packets with sub-nanosecond timestamping, and can accurately monitor/profile/characterize network components such as routers, switches, and network interface cards. Please check out our [examples]({{site-url}}/).

[^1]: Example: *domain.com/category-name/post-title*
