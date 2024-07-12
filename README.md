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

Further exploration led us to a page with a message questioning our methods and hinting at additional hash content:

![key2_crypté](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/3de902d6-6d55-4ef3-b3ed-7e05cfd2a2a8)


The page located at `http://10.10.196.19/license` contains a message along with a base64 encoded string, which could be a part of further challenge or information to decode.

echo ZWxsaW90OkVSMjgtMDY1Mgo= | base64 -d
![decode for login](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/374aae71-2084-4946-9552-0addb14804eb)


Login Attempt
The scan results also revealed a /wp-login page. Let’s go to the path and check what we have there.
![login](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/4d81995c-cbaa-4fad-b3e4-35fb318b7600)

We successfully logged in to the admin panel of wordpress.

 4. Navigating to the Theme Editor
- On the left-hand side menu, we navigated to `Appearance` > `Editor`.
 5. Injecting the Reverse Shell Code from pentestmonkey
- In the editor section, various PHP scripts are present. We selected a script, such as `404.php`, and injected the reverse shell code.
  ![image](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/87deb640-c3d3-4997-b656-93f4a230f4ae)

  we should replace the IP addresse of our ip addresse
![image](https://github.com/HamzaElatmani/Writeup_robots_tryhackme/assets/149976343/5939c912-6bf3-48a6-b668-0eeb9a1a606f)

click update file.
In you attacker machine make netcatlistner ready using
nc -lnvp 443 make sure to use same port.

![listening for reverse shell](https://github.com/user-attachments/assets/4b590ef6-bec1-4f8e-b710-c3d12145628e)

upgrade you shell using
![WhatsApp Image 2024-07-11 at 16 06 30 (11)](https://github.com/user-attachments/assets/e65367c0-ab88-4e87-a974-6593d7dabf1e)

we don’t have access to key-2-of-3.txt but we can read password.raw-md5
reading the password file reveals what looks like username and md5 encrypted password.

![find the key to key3](https://github.com/user-attachments/assets/7ddd6eab-7466-491f-a633-c940a31be579)

robot:c3fcd3d76192e4007dfb496cca67e13b

![find the key to key3](https://github.com/user-attachments/assets/4e662fcf-90f8-4fcd-9f05-b6a930af41f9)

lets switch user to robot

![key_2](https://github.com/user-attachments/assets/f5bec3cd-6326-4453-8c0e-1e03aca9e36f

using the interactive feature we got ourself root access.
and we can read our final key.

![key3](https://github.com/user-attachments/assets/5eb7403d-204d-42d1-ba8a-ea86448ceb3a)

During my exploration, I successfully located the third key.

















