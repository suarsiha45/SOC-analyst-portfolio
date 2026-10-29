# Project 1: Cerber Ransomware Packet Analysis

## 🔍 Scenario Overview
An internal corporate asset was compromised by Cerber Ransomware via a malicious spam (malspam) campaign. As a SOC Analyst, I analyzed the network traffic capture (.pcap) using Wireshark to trace the infection lifecycle.

## 🕵️‍♂️ Executive Summary & Findings
Through network forensics and leveraging Wireshark's HTTP Object Export feature, the following malicious footprint was uncovered:

1. **Patient Zero (Victim):** Internal Host IP `10.12.22.102`
2. **Initial Redirection:** The victim hit an anomalous hostname `1saj0933.mybluemix.net` fetching the `redirector_bcc` script.
3. **Malware Delivery (The Payload):** The host was forced to download a malicious file named `71` directly from the external IP address `13.77.0.146` via raw HTTP protocol.
4. **C2 Communication:** Post-infection traffic shows beaconing to a highly suspicious top-level domain `ftaxmpdqwo...199ovv.top` using structured dynamic strings.

## 🛠️ Mitigations & Lessons Learned
* Block the identified malicious IPs (`13.77.0.146`) and flag the `.top` domain on the corporate firewall/web proxy.
* Isolate the infected host (`10.12.22.102`) from the local network immediately to prevent lateral movement of the ransomware.
