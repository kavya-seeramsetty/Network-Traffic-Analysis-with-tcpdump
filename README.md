# Network Traffic Analysis with tcpdump

## Description
This project demonstrates how to capture, filter, and analyze network traffic using the `tcpdump` tool. By employing a series of `tcpdump` commands, this project allows for the observation of various network protocols, including HTTP, FTP, and ICMP, providing insights into how data is transmitted over the network.

## Utilities and Tools Used
- **tcpdump**: A powerful command-line packet analyzer for capturing network traffic.
- **wget**: A command-line utility for fetching content from web servers, used here to trigger HTTP requests for analysis.

## Commands Overview

### Command 1: Capturing HTTP Traffic
```bash
sudo tcpdump -nn -s 0 -A -v port 80
```
<p align="center"> <br/> <img src="https://imgur.com/vtApS9V.png"/><br /> </p>

### Command 2: Capturing DNS Traffic
```bash
sudo tcpdump -nn -s 0 -A -v port 53
```
<p align="center"> <br/> <img src="https://imgur.com/9iMMxmI.png"/><br /> </p>
<p align="center"> <br/> <img src="https://imgur.com/vHqE0bc.png"/><br /> </p>

### Command 3: Capturing HTTP Host Data
```bash
tcpdump -nn -A -s 1500 -l | grep "Host:"
```
<p align="center"> <br/> <img src="https://imgur.com/GlRfI6S.png"/><br /> </p>

### Command 4: Capturing Traffic to a File
```bash
sudo tcpdump -w capture.pcap
```
<p align="center"> <br/> <img src="https://imgur.com/5EVqmZp.png"/><br /> </p>

### Command 5: Capturing HTTP GET Requests
```bash
sudo tcpdump -s 0 -A -vv 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x47455420'
```
<p align="center"> <br/> <img src="https://imgur.com/M8hOTaN
.png"/><br /> </p>
