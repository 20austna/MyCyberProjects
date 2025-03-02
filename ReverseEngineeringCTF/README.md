## Introduction
This project was a Capture the Flag Activity(CTF) for a reverse engineering position. Since it was part of a job application I feel it important to not share some of the exact files I used, to maintain the integrity of their selection process. That being said, I found this project immensely interesting so I wanted to document how I solved this project. 

## First steps
I was asked to figure out what a rouge process on their system was doing, I was to accomplish this by analyzing a file containing network communications(.pcap).
Knowing that this was a reverse engineering challenge, I knew the network communications likely contained a computer program within. However, to analyze that program, we would first need to analyze the network communications and extract the relevant parts.  

## Packet analysis
I opened [Wireshark](https://www.wireshark.org/), my packet analyzer of choice, and opened the .pcap file inside.
When you open Wireshark you are greeted with a view like this: 

![pcap Screenshot](./pcapScreenshot.png)

The main pane contains some data about each packet like what the source and destination IP are, the port, what protocol they use, their length, their order, and the TCP message type. 
The bottom pane contains the actual hex values of the packet selected along with their ASCII counterparts. 

This information, while helpful, did not give me the info I needed to understand what was going on from a high level. I needed to see all of the ASCII values of the packets, along with their hex counterparts, all at the same time, rather than one by one. To do this I right-clicked on one of the rows in the main pane and hit "follow" > "TCP Stream". 

This view shows the contents of the PSH packets from each service involved in the communication, shown in order. There are also two other views available to us, the first is all communications sent from port 1234 to port 39280, and the second is the inverse, from port 39280 to 1234. 

![The three views]()

Switching between these two views, we see that port one side only sent a few lines of plain text, while the other sent many lines of what appears to be code. 
