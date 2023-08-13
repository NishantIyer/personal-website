---
title: Testing PVPC in OpenShift
date: 2023-03-05T16:00:00Z
lang: en
duration: 9min
description: Portena Virtual Personal Computing
---

## Experiments and Evaluations:

The Portena testbed consists of state-of-the-art server configurations and a variety of clients, aiming to evaluate the performance of the system. The topology of the testbed is illustrated in Figure 4. It comprises three service nodes, one benchmark server, and multiple clients connected through two 100Mbps Ethernets Infibands with a gateway.

![Figure 1. Experimental Testbed](https://media.discordapp.net/attachments/971299427715272734/1116730690014709148/testbed.png?width=589&height=327)

**Table 1. Testbed Configuration:**

|  Computer |          CPU                |     Memory     |   OS                                            |
|-----------|----------------------------|----------------|------------------------------------------------|
| Server 1  | Intel Xeon E5-2670 2.6GHz  |      16 GB     | Ubuntu 22.04, Linux kernel 5.15                |
| Server 2  | AMD EPYC 7302 3.0GHz       |      32 GB     | Ubuntu 22.04, Linux kernel 5.15                |
| Server 3  | Intel Core i7-11700K 3.6GHz |      16 GB     | Ubuntu 22.04, Linux kernel 5.15                |
| Benchmark | Intel Core i5-11400F 2.6GHz |       8 GB     | Windows 11                                     |
| Clients   | Intel Core i5-11400F 2.6GHz |       8 GB     | Ubuntu 22.04, Linux kernel 5.15                |

To evaluate the Portena system, I conducted tests using typical office applications, word processing programs, network tools, developing tools, and streaming media applications. The evaluation employed the i-Bench benchmark suite [14] for web browsing and streaming media tasks.

System overhead was measured by integrating traces into the system, capturing CPU and memory utilization periodically throughout the experiments.

These instances were released in Red Hat's OpenShift infrastructure, which I have obtained in a free tier. I will be using this for further prototyping and development of DRATP.

The processed dataset will be used for machine learning algorithms in DRATP.
