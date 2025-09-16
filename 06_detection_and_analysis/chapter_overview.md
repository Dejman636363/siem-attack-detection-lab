## Threat Detection and Artifact Analysis Based on the Attack Scenario

In the previous chapter, a detailed course of the simulated attack in the test environment was presented.  
The next crucial step is to **verify whether the malicious activity left visible traces in the logs** and to **assess how effectively they can be detected** using the monitoring and detection systems deployed in the laboratory.

The purpose of this chapter is not only to show the traces left by the attack but to conduct a **comprehensive detection analysis**.  
It is assumed that it is **initially unknown what kind of attack occurred, which techniques were used, or which systems were compromised**. Therefore, each step of the analysis is logically connected to the previous one and is guided by discovered **clues and anomalies**. Each stage of the investigation results from observations made in the previous one — just as in a real SOC detection process, where an analyst must **connect facts, interpret logs, and make decisions independently**.

This structure allows evaluating not only the **effectiveness of the applied security mechanisms** but also the **actual defensive capabilities of the environment** and the **usefulness of individual data sources** in the incident response process.

Using data collected from the laboratory environment — including **network monitoring systems (Zeek, Suricata)**, **endpoint logs (Sysmon)**, **Windows event logs**, **registry entries**, and **File Integrity Monitoring (FIM)** mechanisms — an attempt was made to **reconstruct the entire incident**.  

The essence of this detection was to determine:

- **What happened**
- **How it was detected**
- **Which logs confirm it**
- **How earlier signs of the attack could have been noticed**

The structure of this chapter is divided into **subsections corresponding to different detection areas** — from detecting **anomalies in network traffic**, through **analysis of system logs, processes, and PowerShell commands**, to examining **persistence mechanisms, C2 agent activity**, and investigating its **reputation, static properties, and dynamic behavior** in an isolated environment.