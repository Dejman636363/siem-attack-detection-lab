## Attack Scenario – Implementation and Execution

This chapter presents the detailed course of the simulated attack conducted in the previously described laboratory environment.  
The objective was to emulate a **realistic scenario of compromising a user workstation** within the internal network — a fully updated **Windows 10** system with IP `192.168.3.10`, located in the test environment.

The attack was **multi-stage**, covering the **full kill chain**: from **reconnaissance** to **initial access, persistence, data exfiltration, and post-exploitation activities**.  

The attack scenario utilized the **Apollo agent** from the **Mythic C2** platform, which is a **Remote Access Trojan (RAT)**.  
Once the victim system was infected, it established communication with the **command-and-control (C2) server** and allowed the attacker to:

- execute system commands remotely,
- exfiltrate data,
- create **persistence mechanisms**,
- and perform further reconnaissance.

All activities were carried out using **open-source tools** commonly used by **red team operators**, such as **Nmap**, **Hydra**, **Mythic with Apollo agent**, and **native Windows tools (LOLBins)**.  

Instead of exploiting vulnerabilities in unpatched systems, the attack focused on **common configuration weaknesses** often found in real corporate networks.

---

### Planned Attack Stages

1. **Network reconnaissance** – scanning subnets and identifying open ports (**Nmap**)
2. **RDP brute-force attack** – using **Hydra** and wordlists from the **SecLists** package
3. **Remote login to the victim machine** – via **RDP** using **xfreerdp**
4. **Download and execute Apollo payload** – generated on the **Mythic C2** server
5. **Establish persistence** – via a scheduled task (SYSTEM) and a registry entry (user)
6. **Post-exploitation reconnaissance and data exfiltration** – using **Apollo** features (`screenshot`, `keylogger`, `download`)
7. **Testing system response to another user login** – verifying persistence mechanisms

---

Each stage of the attack is presented in the following sections, along with the techniques, tools, and commands used.
