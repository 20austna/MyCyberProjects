## Introduction
This project was a Capture the Flag Activity(CTF) for a reverse engineering position. Since it was part of a job application I feel it important to not share some of the exact files I used, to maintain the integrity of their selection process. That being said, I found this project immensely interesting so I wanted to document how I solved this project. 

## First steps
I was asked to figure out what a rouge process on their system was doing, I was to accomplish this by analyzing a file containing network communications(.pcap).
I opened [Wireshark](https://www.wireshark.org/), my packet analyzer of choice, and opened the .pcap file inside. 

## Packet analysis
When you open Wireshark you are greeted with a view like this: 

![pcap Screenshot](./pcapScreenshot.png)

The main pane contains some data about each packet like what the source and destination IP are, the port, what protocol they use, their length, their order, and the TCP message type. 
The bottom pane contains the actual hex values of the packet selected along with their ASCII counterparts. 

This information, while helpful, did not give me the info I needed to understand what was going on from a high level. I needed to see all of the ASCII values of the packets, along with their hex counterparts, all at the same time, rather than one by one. To do this I right-clicked on one of the rows in the main pane and hit "follow" > "TCP Stream". 

In this view, there was a lot of information to chew on.(unfinished)
