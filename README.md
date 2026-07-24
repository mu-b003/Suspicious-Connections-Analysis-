# Suspicious Connections Analysis

## Project Overview

This project demonstrates how a SOC analyst investigates suspicious network connections inside an isolated virtual laboratory using Ubuntu Server, Kali Linux, and Wireshark.

The objective is to identify abnormal communication patterns, repeated HTTP requests, suspicious DNS queries, rejected TCP connections, and excessive SSH traffic.

---

## Lab Environment

Kali Linux
Ubuntu Server
Wireshark
Apache2
OpenSSH

---

## Objectives

• Generate suspicious HTTP traffic

• Generate SSH communication

• Investigate DNS activity

• Detect typosquatting domains

• Analyze rejected TCP connections

• Examine Protocol Hierarchy

• Analyze Endpoints

• Analyze Conversations

• Investigate TCP Flags

---

## Tools

Wireshark

curl

nslookup

SSH

Netcat

Apache2

OpenSSH

---

## Investigation Steps

System Preparation

Traffic Generation

Packet Capture

Protocol Analysis

Conversation Analysis

IOC Extraction

Incident Summary

---

## Indicators of Compromise (IOC)

Repeated HTTP Requests

Large SSH Session

Suspicious DNS Query

Rejected Connections on Ports

4444

9999

21

23

---

## Skills Demonstrated

Network Traffic Analysis

DNS Investigation

HTTP Analysis

SSH Analysis

Packet Analysis

Wireshark Investigation

SOC Monitoring

Threat Hunting

Incident Documentation
