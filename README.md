# TryHackMe Robot CTF Walkthrough

This repository contains a detailed walkthrough of the Robot CTF challenge on TryHackMe. Below are the steps and commands used to complete the challenge.

## Table of Contents
1. [Configuration](#configuration)
2. [Initial Enumeration](#initial-enumeration)
3. [Finding the First Key](#finding-the-first-key)
4. [Gaining Access](#gaining-access)
5. [Finding the Second Key](#finding-the-second-key)
6. [Privilege Escalation](#privilege-escalation)
7. [Finding the Third Key](#finding-the-third-key)

## Initial Enumeration

![Nmap Scan]
![1](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/2dbbac54-05bb-44f4-8ba5-48f4286cc602)

In this scan, we performed an Nmap scan on the IP address `10.10.196.19` with the following options:
- `-Pn` to skip the host discovery
- `-A` to enable OS detection, version detection, script scanning, and traceroute

The scan results show the open ports, services, and versions running on the target machine. It highlights common services such as HTTP and HTTPS running on Apache, along with details about the SSL certificate and HTTP server headers.

# gobuster 
Using gobuster for directory enumeration to find hidden directories and files.
![WhatsApp Image 2024-07-11 at 16 06 30 (14)](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/d97caf09-4bf9-4829-88f9-e52468532efc)

