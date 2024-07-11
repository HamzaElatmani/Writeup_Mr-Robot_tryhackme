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

During the penetration test, we navigated to the `robots.txt` file to discover restricted directories and files. One of the interesting findings led us to the following key:
![key_1](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/9dd6bbaa-f227-4df4-acb4-d883fd2d2969)

# gobuster 
Using gobuster for directory enumeration to find hidden directories and files.
![1_find license](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/646dc400-e841-44d6-99f2-3251caa55f60)

### License Page Discovery

Further exploration led us to a page with a message questioning our methods and hinting at additional encrypted content:

![key2_crypté](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/3de902d6-6d55-4ef3-b3ed-7e05cfd2a2a8)


The page located at `http://10.10.196.19/license` contains a message along with a base64 encoded string, which could be a part of further challenge or information to decode.

```html
<pre style="word-wrap: break-word; white-space: pre-wrap;">
what you do just pull code from Rapid9 or some s@#% since when did you become a script kitty? do you want a password or something?
ZWxsaW900KVSMjgtMDY1Mgo= 
</pre>




