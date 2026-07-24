# Suspicious Connections Analysis Report

**Author:** Mubarak Bashr

**Project:** Suspicious Connections Analysis

**Environment:** Kali Linux, Ubuntu Server, Wireshark

**Date:** July 2026

---

# Abstract

This report documents a Suspicious Connections Analysis performed in an isolated virtual laboratory using Kali Linux, Ubuntu Server, and Wireshark. The objective was to generate, capture, and analyze different types of network connections that may appear suspicious from a Security Operations Center (SOC) perspective. The investigation focused on repeated HTTP requests, SSH communication, DNS queries, failed DNS lookups, and rejected TCP connection attempts to commonly targeted ports. The captured traffic was analyzed using Wireshark to identify communication patterns, endpoints, conversations, protocol distribution, and potential Indicators of Compromise (IOCs).

---

# Objectives

* Build a realistic SOC investigation scenario.
* Generate suspicious HTTP traffic.
* Generate SSH communication between systems.
* Investigate DNS activity.
* Detect typosquatting domains.
* Identify failed TCP connection attempts.
* Analyze captured packets using Wireshark.
* Document Indicators of Compromise (IOCs).
* Produce a professional incident investigation report.

---

# Lab Environment

| Component        | Description        |
| ---------------- | ------------------ |
| Attacker Machine | Kali Linux         |
| Target Machine   | Ubuntu Server      |
| Packet Analyzer  | Wireshark          |
| Web Server       | Apache2            |
| SSH Server       | OpenSSH            |
| Network          | VMware NAT Network |

---

# Scenario

A SOC analyst receives an alert indicating abnormal communication between two internal systems. The objective is to investigate whether the observed traffic represents legitimate administrative activity or suspicious behavior. During the investigation, repeated HTTP requests, SSH sessions, DNS lookups, and multiple connection attempts to sensitive ports are generated and analyzed to understand the communication patterns.

---

# Methodology

The investigation followed these stages:

1. Preparing the laboratory environment.
2. Verifying Apache and SSH services.
3. Capturing live traffic using Wireshark.
4. Generating HTTP requests.
5. Performing DNS lookups.
6. Establishing an SSH session.
7. Testing suspicious TCP ports.
8. Saving the packet capture.
9. Analyzing captured traffic.
10. Extracting Indicators of Compromise.

---

# Investigation Activities

## System Preparation

Both virtual machines were updated before the investigation. Apache2 and OpenSSH services were verified on Ubuntu Server to ensure the target services were operational.

---

## HTTP Activity

HTTP requests were generated from Kali Linux using curl.

A loop generated ten consecutive requests to simulate repetitive automated activity frequently observed during scripted reconnaissance or monitoring.

The Apache server successfully responded to every request.

---

## DNS Investigation

DNS resolution was tested using both a legitimate domain and a suspicious typo domain.

Successful query:

* bitpluss.com

Failed query:

* ubunyu.com

The failed lookup generated an NXDOMAIN response, demonstrating how typosquatting attempts can be identified during DNS monitoring.

---

## SSH Investigation

A successful SSH session was established from Kali Linux to Ubuntu Server.

The analyst authenticated successfully and executed basic commands including:

* pwd
* ls
* exit

The session generated a large amount of encrypted SSH traffic that became the dominant protocol inside the packet capture.

---

## TCP Connection Investigation

Several connection attempts were made toward ports commonly associated with administrative services or attacker infrastructure.

Ports tested:

* 4444
* 9999
* 21
* 23

Every connection attempt resulted in a TCP Reset (Connection Refused), indicating that no services were listening on those ports.

---

# Wireshark Analysis

## Capture File Properties

The packet capture contained:

* Total Packets: 1374
* Capture Duration: 7 minutes 38 seconds
* Average Rate: 3 packets/second
* File Size: 345 KB

The capture successfully documented the complete investigation.

---

## Protocol Hierarchy

The protocol hierarchy revealed that TCP dominated the capture.

Major observations included:

* IPv4 represented approximately 95% of traffic.
* TCP represented over 86% of captured packets.
* SSH generated the largest percentage of traffic.
* HTTP represented only a small portion.
* DNS activity represented a very small percentage.

---

## Endpoints Analysis

The primary communication occurred between:

**Source**

192.168.81.128

**Destination**

192.168.81.129

These two systems exchanged the overwhelming majority of packets throughout the investigation.

---

## Conversations Analysis

Conversation statistics identified one dominant communication flow between the Kali Linux attacker machine and the Ubuntu Server.

This conversation accounted for most captured traffic and represented the primary activity requiring investigation.

---

## HTTP Analysis

HTTP filtering revealed repeated GET requests generated by curl.

Characteristics observed:

* Regular intervals.
* Automated request pattern.
* Default Apache page requested repeatedly.
* curl User-Agent identified.

This behavior resembles scripted monitoring or automated reconnaissance.

---

## SSH Analysis

SSH traffic represented the largest protocol within the capture.

The session included:

* TCP handshake.
* SSH protocol negotiation.
* Key exchange.
* Encrypted communication.
* Session termination.

Although legitimate in this laboratory, an unusually large SSH volume could warrant investigation in a production environment.

---

## DNS Analysis

DNS filtering identified both successful and failed lookups.

Successful:

* bitpluss.com

Failed:

* ubunyu.com

The failed lookup returned an NXDOMAIN response consistent with typo-domain detection.

---

## TCP Reset Analysis

TCP Reset packets documented rejected connection attempts.

Rejected ports included:

* 4444
* 9999
* 21
* 23

These results confirmed that the target machine was not exposing services on those ports.

---

## SYN Packet Analysis

SYN packet analysis identified all new connection attempts initiated during the investigation.

The captured SYN packets targeted multiple services including:

* HTTP
* SSH
* HTTPS
* FTP
* Telnet
* High-numbered ports

This provided a complete timeline of connection establishment attempts.

---

# Indicators of Compromise (IOCs)

| Type                   | Indicator                |
| ---------------------- | ------------------------ |
| Source IP              | 192.168.81.128           |
| Destination IP         | 192.168.81.129           |
| Suspicious Domain      | ubunyu.com               |
| HTTP Tool              | curl                     |
| Repeated HTTP Requests | Yes                      |
| Large SSH Session      | Yes                      |
| Failed TCP Connections | Ports 4444, 9999, 21, 23 |
| NXDOMAIN Response      | ubunyu.com               |

---

# Findings

The investigation identified several behaviors commonly monitored by Security Operations Centers.

Key findings include:

* Repetitive HTTP requests generated by automation.
* Successful SSH administrative communication.
* Detection of a typosquatting-style DNS query.
* Multiple failed TCP connection attempts to sensitive ports.
* Dominant SSH traffic within the capture.
* TCP Reset packets documenting rejected services.
* Complete visibility into communication endpoints and conversations.

---

# Conclusion

This investigation successfully demonstrated the process of identifying and analyzing suspicious network connections within an isolated laboratory environment. Wireshark provided comprehensive visibility into HTTP, SSH, DNS, and TCP communications, enabling the identification of repetitive behavior, failed connection attempts, and suspicious DNS activity.

The exercise reflects common tasks performed by SOC analysts during network investigations and strengthens practical skills in packet analysis, incident documentation, IOC identification, and network traffic interpretation.

