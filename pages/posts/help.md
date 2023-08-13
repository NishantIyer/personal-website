---
title: A miracle.
date: 2023-5-22T16:00:00Z
lang: en
duration: 9min
description: ESPFA - ESP32 Port Forwarding Accelerator
---

Today's blog is a living proof that some things happen for a reason. Code i wrote 2 years back is now a real boon to my current situation. It literally was a perfect fit for my errors!

2 years ago, when I was in grade 8, I built a Port Forwarding Accelerator called ESPFA for a project as my local router supported only 20 port forwarding rules. I needed more. My local router can forward a range of ports using one rule so I needed something inside my local network that could receive traffic on those ports and forward them to other IPs on my local network. It sounded like a good task for an ESP32 chip.

I was trying with an Arduino Nano to build a small solar tracker, made it well, you may find it [here](https://nishantiyer.netlify.app/gallery). I wanted to go a step ahead and create a swarm of solar trackers that could act like a charging point for my phone, but encountered many issues while creating it.

The lwip library as delivered with the ESP-IDF and Arduino IDEs does not support port forwarding back onto the same network, and the Arduino IDE, which I normally use, does not support modifying the lwip library. So, this was my first attempt at using ESP-IDF.

Starting with ESP-IDF version 4.4.0, I made some modifications to the following lwip files to support port forwarding back onto the same network the packets came in on.

I had to hard code turning on port forwarding in `opt.h` because `menuconfig` does not handle turning on all options needed:

- ESP-IDF\components\lwip\lwip\src\include\lwip\opt.h

The ESP32 Local Port Forwarder, as built, can support up to 32 port forwarding rules as defined by `IP_PORTMAP_MAX` set in `lwip_napt.h`.

As built, on first run after firmware install with a clean nvs, an AP with SSID `ESP32LocalPortForwarder` is started. Connect to that network, then to `192.168.4.1` with a browser to setup static IP network config info for your local network. After it reboots, the AP will be turned off. Connect to the static IP with a browser to configure port forwarding rules. If the ESP32 is connected to a serial interface, then all commands built into Martin-Ger's ESP32 NAT Router serial interface are still available, except the AP will be turned off after the static IP is set.

I also included OTA firmware updates through the web like I do in all my ESP32 projects so I can do firmware updates without physically connecting to the ESP32.

This is a firmware to use the ESP32 as WiFi NAT router. It can be used as:

- Simple range extender for an existing WiFi network
- Setting up an additional WiFi network with different SSID/password for guests or IOT devices

It can achieve a bandwidth of more than 15mbps.

The code is based on the [Console Component](https://docs.espressif.com/projects/esp-idf/en/latest/api-guides/console.html#console) and the [esp-idf-nat-example](https://github.com/jonask1337/esp-idf-nat-example). 

## Performance

All tests used `IPv4` and the `TCP` protocol.

| Board        | Tools   | Optimization | CPU Frequency | Throughput    | Power |
| ------------ | ------- | ------------ | ------------- | -------------- | ----- |
| `ESP32D0WDQ6` | `iperf3` | `0g`         | `240MHz`      | `16.0 MBits/s` | `1.6 W` |
| `ESP32D0WDQ6` | `iperf3` | `0s`         | `240MHz`      | `10.0 MBits/s` | `1.8 W` | 
| `ESP32D0WDQ6` | `iperf3` | `0g`         | `160MHz`      | `15.2 MBits/s` | `1.4 W` |
| `ESP32D0WDQ6` | `iperf3` | `0s`         | `160MHz`      | `14.1 MBits/s` | `1.5 W` |

Find more at - [https://github.com/NishantIyer/espfa](https://github.com/NishantIyer/espfa)

How is it helping Portena?

uNet (my firmware) that currently utilizes ESP32 for prototyping is limited by the limitation of local routers and solves a hell lot of problems I'm facing.

- Port forwarding: When the server is behind a firewall or NAT, which is, in fact, as I'm using third party now, ESPFA is a great solution to set up port forwarding on your local network, enabling incoming traffic on specific ports to be forwarded to your server. This way, you can establish a direct connection to your server from outside your network.
- Secure Remote Access: By using a remote connection protocol like SSH or uNet, you can securely access your server over the internet. The ESPFA firmware helps by efficiently forwarding the necessary network traffic to your server, ensuring that your remote connection protocol works as intended.
- Easier testing and work: The ESPFA firmware allows you to create a local port forwarder using an ESP32 chip. This means you can simulate remote connections to your server within your local network, making it easier to prototype and test the remote access functionality without getting a huge bill after my free tier ends.
- Gosh, OTA! I work in parallel with ESPs, one for the physical device and the other times for building client modules. OTA is a big saver here.

Obviously, I will have to make this as my codebase and modify a bit more, but really, this seems like a miracle.

Regards,
Nishant Iyer
