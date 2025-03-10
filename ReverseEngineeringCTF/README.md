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
The bottom pane contains the actual hex values of the packet selected along with their ASCII counterparts. From this, I only knew that this was a conversation from two ports(1234 and 39280) on the same IP address. Clicking through each PSH packet I would find some bits of text that appeared to be code but I wasn't getting a clear picture. I needed to see every PSH packet all together, in order. To do this I right-clicked on one of the entries in the main pane and hit "follow" > "TCP Stream". 

Selecting this view shows the whole conversation in chronological order. There are also two other views available, one showing p:1234 -> p:39280, and the other showing p:1234 -> p:39280. 

![The three views](./conversationView.png)

Notice the difference in size, one contains much more data than the other. Additionally, 1234 -> 39280(the smaller of the two) contained only human readable ascii values, while the other contained a fair bit of nonsense with some code interlaced. 

![image of the ascii in 1234 to 39280](./1234to39280.png)

![image of the ascii in 39280 to 1234](./39280to1234.png)

From the first screenshot, it seemed to me that this contains a filename(flag.txt) and a key of some sort(Prestidigitation). But it was hard to know what to do with it without understanding what the code on the other side of the conversation did. Just to be sure I tried to enter Prestidigitation as the flag but it didn't work. 

# File conversion and reverse engineering


