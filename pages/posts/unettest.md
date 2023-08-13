---
title: uNet Test
date: 2023-05-01T16:00:00Z
lang: en
duration: 9min
description: Portena Distributed Virtual Personal Computing
---

## Remote Display Performance:

In the evaluation of remote display performance using the Portena system, I focused on measuring various aspects such as application startup speed, web page open latency, stream media packets missing rate, and media file display lag. A comparison was made between uNet (Portena) and two other systems: a VNC system and a local RFB display on Server 1.

**Figure 1 Application Startup Speed:**

![Figure 1](https://media.discordapp.net/attachments/971299427715272734/1116730737480171570/Screenshot_from_2023-06-09_19-39-03.png?width=392&height=290)

Figure 1 illustrates the startup speed of typical applications in the Portena system. It demonstrates that uNet is much faster in starting up applications compared to the VNC-based system and is nearly as fast as the local display.

**Table 1. Web: Average Page Latency:**

|                | Average Page Latency (s) |
|----------------|--------------------------|
| Local          | 0.39                     |
| uNet           | 0.51                     |
| VNC            | 1.10                     |

Table 1 presents the average page latency benchmarked using the i-Bench 3.0 suite. While uNet is slightly slower than the local display, it still outperforms the VNC-based system by a significant margin.

**Table 2. Stream Media: Packets Missing Rate:**

|                | Packets Missing (%) |
|----------------|---------------------|
| Local          | 7                   |
| uNet           | 12                  |
| VNC            | 38                  |

Table 2 displays the packets missing rate in the stream media display, as benchmarked by i-Bench 3.0. The local display experiences a packet loss of 7%, uNet encounters a packet loss of 12%, while the VNC-based system suffers from a significant packet loss of 38%. The video jumps severely on the VNC client, resulting in a poor user experience.

The display lag of the stream media was measured by screening a section of a media file with Realplayer and calculating the running time. The media file has a size of 360x240 pixels and a duration of 29 seconds. Both the original size display and full-screen size display were evaluated. As shown in Figure 6, the display on the uNet client experiences minimal lag, which is hardly perceivable. On the other hand, the display on the VNC client lags by approximately 20% in the original size and takes more than double the time in the full-screen size.


The superior performance of uNet in comparison to the VNC-based system on our testbed can be attributed to the advanced remote display technology and optimization techniques employed by uNet. These optimizations minimize latency and reduce the occurrence of packet loss, resulting in a smooth and seamless user experience.

I/O Performance of UTC Storage:

Portena's UTC (Universal Time Converter) provides CD-ROM drivers and USB storage interfaces. Table 4 demonstrates the I/O performance of UTC storage devices.

**Table 4. I/O Performance of UTC Storage:**

|                 | Average I/O (KB/s) | Maximum I/O (KB/s) | Maximum I/O (%) |
|-----------------|--------------------|--------------------|-----------------|
| USB Reading     | 184                | 137.9              | 62%             |
| USB Writing     | 228                | 147.5              | 67.3%           |
| CD-ROM Reading  | 85.3               | 51.2               | 100%            |

The table showcases the performance metrics of the UTC storage devices. The USB reading speed achieves a maximum of 184 KB/s and an average of 137.9 KB/s, utilizing approximately 62% of the total device I/O bandwidth. The USB writing speed reaches a maximum of 228 KB/s and an average of 147.5 KB/s, utilizing approximately 67.3% of the total device I/O bandwidth. The CD-ROM reading speed attains a maximum of 85.3 KB/s and an average of 51.2 KB/s, fully utilizing the available bandwidth of the CD-ROM device.

These results demonstrate the efficient and reliable I/O performance of the UTC storage devices in the Portena system.
