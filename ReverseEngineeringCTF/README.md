## Introduction
This project was a Capture the Flag Activity(CTF) for a reverse engineering position. Since it was part of a job application I feel it important to not share some of the exact files I used, to maintain the integrity of their selection process. That being said, I found this project immensely interesting so I wanted to document how I solved this project. 

## First steps
I was asked to figure out what a rouge process on their system was doing, I was to accomplish this by analyzing a file containing network communications(.pcap).
I opened [Wireshark](https://www.wireshark.org/), my packet analyzer of choice, and opened the .pcap file inside. 

## Packet analysis
When you open Wireshark you are greeted with a view like this: 
![pcap Screenshot](./pcapScreenshot.png)
Once I had the packets opened inside Wireshark, I right-clicked on one of the packets to follow the TCP stream. I did this because normally when you 
