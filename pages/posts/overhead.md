---
title: Overhead of uNet
date: 2023-06-03T16:00:00Z
lang: en
duration: 9min
description: Overhead test for uNet
---
**Overhead:**

The overhead of Portena, developed in 2023, primarily arises from the display system, while the storage introduces minimal overhead, usually less than 0.5% of the system's CPU and memory. Therefore, we focus on evaluating the display overhead of the Portena system. The display overhead is measured on both the server side and the client side.

**Overhead on the Client:**

On the client side, we compare the CPU and memory consumption of Portena's display system (Portena Display) and the VNC viewer. We consider three typical cases in our experiment: standby, web browsing, and stream media playing. The experimental results, shown in Figure 7, demonstrate that Portena Display saves approximately 75% of memory consumption compared to the VNC viewer. However, the CPU consumption of Portena Display is slightly higher than that of the VNC viewer. Portena achieves memory savings by loading a smaller software suite and reducing data copy operations. The optimizations in Portena Display simplify data transport and processing, resulting in reduced memory requirements for data buffering or caching. The increased CPU consumption in Portena Display can be attributed to the absence of hardware acceleration provided by the Linux framebuffer driver used in 2023, as opposed to the Xlib-based VNC viewer.

![Overhead on the Client](https://media.discordapp.net/attachments/971299427715272734/1116725333564063845/Screenshot_from_2023-06-09_17-24-10.png?width=437&height=242)

**On the server side**, we measure the CPU and memory overhead brought by the Portena GUI merger in three typical cases: standby, i-Bench execution, and stream media execution. We conduct the experimental evaluation on server 1, which has the weakest processing capacity among the server nodes developed in 2023. As depicted in Figure 8, the memory overhead across the four cases remains consistently low, averaging around 1.3%. This memory overhead has minimal impact on the system's performance. The CPU overhead varies significantly among the three use cases. During client standby, the CPU overhead is approximately 1%. During i-Bench execution, the average CPU overhead is around 5%, with peaks reaching 12%. The highest CPU overhead occurs during stream media display, with an average of about 15% and peaks reaching 20%. Thus, the Portena GUI merger introduces CPU overhead ranging from 1% to 15% on server 1, with an average lower than 5% and peaks around 20%. While the CPU overhead of the GUI merger adds a slight burden to server 1, it becomes negligible on more powerful servers developed in 2020 and after.

![Overhead on the Server](https://media.discordapp.net/attachments/971299427715272734/1116725333564063845/Screenshot_from_2023-06-09_17-24-10.png?width=437&height=242)
