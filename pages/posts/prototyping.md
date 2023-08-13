---
title: Prototyping Portena
date: 2023-04-23T16:00:00Z
lang: en
duration: 9min
description: Prototyping with what I have.
---

I thought quite a lot about prototyping and creating a mini version of portena and chose esp32 as the microcontroller.
There's no specific reason for why I did that, but I've had a long history of working on projects using esp32 so just chose it.
What basically i am trying to make is an esp32 connect to a remote instances using a remote connection protocol (uNet) and mirror its activity to a screen by converting them to vga signals (my monitors are vga so that's why i chose it).
At the same time in a duplex way, it will be connected to Usb 12c modules which convert keyboard, mouse movements and send it over uNet to the instance.
Here is the code i wrote for espvga - 
https://github.com/NishantIyer/espvga

Advanced VGA Implementation for ESP32 Microcontroller

Welcome to the in-depth technical details of my VGA implementation for the ESP32 microcontroller. This readme.md will provide you with a comprehensive understanding of the intricate workings and optimizations that enable real-time rendering of 3D models and support for various screen resolutions.

ESP32 Enhancements and Performance Tweaks

To achieve superior performance and unlock unprecedented capabilities, I have gone beyond the standard specifications of the ESP32 microcontroller. By applying meticulous tweaks and optimizations, I have pushed the boundaries of the microcontroller's processing power, color depth, and resolution capacity. This allows for the seamless rendering of high-quality 3D models with exceptional speed and precision.

ESP32Lib Arduino Library Development
As part of this project, I have been actively developing the ESP32Lib Arduino library. This library, available in the Library Manager under the search term "bitluni," is tailored specifically for the ESP32 microcontroller and serves as a valuable resource for leveraging the full potential of this VGA implementation. While the library is still a work in progress, it already offers a collection of simple yet powerful examples that can serve as a foundation for your own projects.

Building the Implementation
To build and deploy the VGA implementation on your ESP32 microcontroller, follow these steps:

At the end of the code, you'll find the "R" value set to 150. This value is currently optimized for the available pins, providing optimal performance. However, if you encounter a dark display on a different monitor, you can experiment by increasing the "R" value to 1000, potentially enhancing the brightness.

If you prefer not to use resistors, an alternative approach is available. Simply connect the "R4," "G4," and "B3" pins directly to the "R," "G," and "B" pins of the cable. This streamlined configuration bypasses the need for additional resistors while maintaining a reliable connection.

Code Breakdown
Let's delve into the technical details of the code:

The code includes essential libraries and dependencies required for the VGA implementation, including the "I2SVGA.h" library from the ESP32Lib.
A series of pin configurations define the connections between the ESP32 and the VGA device, including the red, green, and blue pins, as well as the horizontal sync (hsync) and vertical sync (vsync) pins.
The "I2SVGA" object from the "I2SVGA" library is instantiated as "graphics," initializing the VGA functionality with the specified pin configurations.
The setup function is responsible for initializing the serial communication and configuring the VGA parameters, such as the graphics mode and the selected font.
The drawModel function handles the real-time rendering of the 3D model. It utilizes matrices for transformations and applies perspective projection for realistic rendering. The "model2" object represents the 3D model and is transformed and drawn using the specified graphics object.
The draw function orchestrates the overall output display. It calculates the frames per second (fps), clears the graphics buffer, renders the 3D model, and displays performance statistics on the VGA screen.
The loop function continuously calls the draw function, ensuring a smooth and uninterrupted execution of the VGA implementation.
Feel free to explore the code and experiment with the various parameters and functions to unleash the full potential of this advanced VGA implementation. Enjoy the incredible capabilities of the ESP32 microcontroller as you create stunning visuals and push the boundaries of what is possible in real-time rendering.
