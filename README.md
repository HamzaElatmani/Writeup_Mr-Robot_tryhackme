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

## Configuration

The initial configuration setup involved setting email notifications, alert levels, and logging format in the Wazuh configuration file.

```xml
<global>
  <email_notification>yes</email_notification>
  <smtp_server>localhost</smtp_server>
  <email_from>wazuh1337@gmail.com</email_from>
  <email_to>wazuh1337@gmail.com</email_to>
  <email_maxperhour>12</email_maxperhour>
  <email_log_source>alerts.log</email_log_source>
  <agents_disconnection_time>10m</agents_disconnection_time>
  <agents_disconnection_alert_time>0</agents_disconnection_alert_time>
  <update_check>yes</update_check>
</global>

<alerts>
  <log_alert_level>3</log_alert_level>
  <email_alert_level>3</email_alert_level>
</alerts>

<logging>
  <log_format>plain</log_format>
</logging>
