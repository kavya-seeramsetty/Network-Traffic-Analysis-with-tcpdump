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
<p align="center"> <br/> <img src="https://imgur.com/M8hOTaN.png"/><br /> </p>

### Command 6: Sending a POST Request with Custom User-Agent
```bash
wget google.com --user-agent="Hello this is a post request" --method=post
```
<p align="center"> <br/> <img src="https://imgur.com/N1u6xej.png"/><br /> </p>

### Command 7: Capturing POST Requests in TCP Traffic
```bash
sudo tcpdump -s 0 -A -vv 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x504f5354'
```
<p align="center"> <br/> <img src="https://imgur.com/tiVSPcS.png"/><br /> </p>

### Command 8: Capturing HTTP Methods (POST/GET)
```bash
sudo tcpdump -s 0 -v -n -l | egrep -i "POST /|GET /"
```
<p align="center"> <br/> <img src="https://imgur.com/wsLgSEw.png"/><br /> </p>

### Command 9: Capturing Sensitive POST Request Data
```bash
sudo tcpdump -s 0 -A -vv 'tcp[((tcp[12:1] & 0xf0) >> 2):4] = 0x504f5354'
curl -X POST "http://www.google.com/echo/post/" -H "Content-Type: application/json" -d '{"username":"KavyaSeeramsetty", "password":"Kavya@2025"}' --user "login:password"
```
<p align="center"> <br/> <img src="https://imgur.com/AONDTks.png"/><br /> </p>
<p align="center"> <br/> <img src="https://imgur.com/IKSF2pw.png"/><br /> </p>

### Command 10: Capturing Cookie and Host Data
```bash
sudo tcpdump -nn -A -s 0 -l | egrep -i 'Set-Cookie|Host:|Cookie:'
```
<p align="center"> <br/> <img src="https://imgur.com/KRvwq9x.png"/><br /> </p>

### Command 11: Capturing ICMP Traffic
```bash
tcpdump -n icmp
```
<p align="center"> <br/> <img src="https://imgur.com/V7xeVw8.png"/><br /> </p>
<p align="center"> <br/> <img src="https://imgur.com/xscAfmz.png"/><br /> </p>

### Command 12: Monitoring SMTP Traffic
```bash
sudo tcpdump -nn -l port 25
telnet mail.google.com 25
```
<p align="center"> <br/> <img src="https://imgur.com/qjkCcTI.png"/><br /> </p>
<p align="center"> <br/> <img src="https://imgur.com/efhTfHu.png"/><br /> </p>

### Command 13: Synchronizing Time with NTP
```bash
sudo ntpdate -v pool.ntp.org
sudo tcpdump dst port 123
```
<p align="center"> <br/> <img src="https://imgur.com/dvW8hkZ.png"/><br /> </p>
<p align="center"> <br/> <img src="https://imgur.com/ECvKzeb.png"/><br /> </p>

### Command 14: SNMP Traffic Analysis
```bash
sudo tcpdump -n -s0 port 161 and udp
onesixtyone 10.10.1.10 public
```
<p align="center"> <br/> <img src="https://imgur.com/N0wirPi.png"/><br /> </p>
<p align="center"> <br/> <img src="https://imgur.com/b61by1P.png"/><br /> </p>

### Command 15: FTP Data Transfer Analysis
```bash
sudo tcpdump -nn -v port ftp or ftp-data
ftp test.rebex.net
```
<p align="center"> <br/> <img src="https://imgur.com/uSZpIS8.png"/><br /> </p>
<p align="center"> <br/> <img src="https://imgur.com/iXiSuUM.png"/><br /> </p>
