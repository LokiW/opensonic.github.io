---
layout: page
title: FAQ
excerpt: ""
modified: 2015-02-18
---

##How is a packet formatted in the 10GbE physical layer?
<figure>
    <img src="/images/packet_format_10GbE.jpg"></img>
</figure>
The 10GbE physical layer uses 64b/66b encoding to reformat a packet before transmits the packet over the physical medium. On the transmit path, the physical layer encodes every 64-bit from an Ethernet frame into a 66-bit block, which consists of a two bit synchronization header and a 64-bit payload. There are two ways to encode a packet based on where the first byte is aligned. The picture below shows those two cases. The first four or eight bytes of a packet including the preamble will be encoded as a /S/ block followed by data blocks which encodes eight bytes from the packet. Then, The rest of the packet is encoded as a /T/ block along with idle characters. There is also a control block (/E/) which contains eight idle characters. In SoNIC, we define a packet length to be the number of bits from the first data byte of a packet to the end of the last data byte. In the picture above, the packet length is the number of bits between left arrow and right arrow.*


## What is an Idle character?
An Idle character (/I/) is a special control character in 10 Gigabit Ethernet that is inserted between any two Ethernet frames. In particular, IEEE 802.3 standard requires the MAC layer to insert at least 12 Idle characters after each Ethernet frame. However, the number of /I/s can be different between the MAC layer and the physical layer. The physical layer needs to insert or delete /I/s to correctly format a packet, if necessary, to compensate clock skew, or to achieve better throughput (i.e. DIC algorithm). SoNIC allows users to control the number of /I/s when generating packets and count the number of /I/s (or bits) between Ethernet frames when capturing packets.

## Interpacket gap? Interpacket delay?

Interpacket delay is the timing difference between the first bits of two subsequent packets. In the picture above, it is the number of bits between two left arrows multiplied by the bitwidth (=97ps). Interpacket gap is the timing difference between the last bit of one packet and the first bit of the next packet. In the picture above, it is the number of bits between the right arrow of the first packet and the left arrow of the second packet multiplied by the bitwidth (97ps).

##vs. BiFocals?
[BiFocals](http://bifocals.cs.cornell.edu) is a state-of-the-art tool that can access the physical layer with physics equipment. It consists of laser, modulator, oscilloscope, etc. to generate and capture raw optic symbols for offline analysis. In essence, both BiFocals and SoNIC access to the physical layer in software. However, BiFocals is not portable and realtime. BiFocals can store and analyze only a few microseconds worth of data because of the small memory installed in the oscilloscope. In addition, it requires a few thousands of CPU hours for processing raw opticcal signals. On the other hand, SoNIc is highly portable and realtime.

##vs. NetFPGA?

[NetFPGA](http://netfpga.org) is a network research platform that allows users to experiment with FPGA-based routers and switches. While NetFPGA 10G allows user to access the Layer 2 and above, SoNIC allows users to access the physical layer. In particular, NetFPGA pushes not only layers 1-2 into hardware, but potentially layer 3 as well. Furthermore, it is not possible to easily undo this design since it uses an on-board chip to implement the physical layer which prevents direct access.
