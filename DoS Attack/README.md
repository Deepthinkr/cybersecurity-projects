Denial of Service (DoS) Attack Analysis with Wireshark

Overview

This repository contains a Cybersecurity Incident Report detailing the analysis of a Denial of Service (DoS) attack using Wireshark. The report identifies suspicious network activity, explains the impact of a SYN Flood attack, and provides mitigation strategies.

Files in This Repository

Cybersecurity_Incident_Report_DoS.pdf – Detailed analysis of the attack, including logs and findings.
Wireshark_Capture.pcapng – Packet capture file from Wireshark showing the attack in action.
README.md – This document, providing an overview of the project.
Attack Summary

A SYN Flood DoS attack was detected, causing service disruption. The attack exploited the TCP handshake process by sending a large number of SYN requests without completing the connection. This led to resource exhaustion, preventing legitimate users from accessing the web server.

Key Findings

The server received an unusually high number of SYN packets from a single IP address.
Many half-open connections were detected, leading to connection timeouts.
The server responded with numerous RST packets, indicating it was overwhelmed.
Users experienced 504 Gateway Timeout errors, confirming service degradation.
Mitigation Steps

To prevent similar attacks in the future, the following countermeasures should be implemented:
✅ Enable SYN cookies to prevent resource exhaustion.
✅ Set connection rate limits to restrict excessive SYN requests from a single IP.
✅ Use a firewall or IDS (e.g., Snort, Suricata) to detect and block malicious traffic.
✅ Monitor network traffic using tools like Wireshark, Fail2Ban, or NetFlow for anomalies.

How to Analyze the Attack (Reproduce the Analysis)

Open Wireshark and load the provided Wireshark_Capture.pcapng file.
Use the filter:
tcp.flags.syn == 1 && tcp.flags.ack == 0
This will show all SYN packets without ACK responses.
Identify the source IP address sending excessive SYN packets.
Check the server’s response to verify if it was overwhelmed (e.g., excessive RST packets).
Confirm service impact by looking for 504 Gateway Timeout errors in the logs.
Tools Used

Wireshark – For network packet analysis.
Kali Linux – To simulate attacks (if applicable).
Firewalls/IDS – For potential mitigation testing.
License

This project is open-source and provided for educational and research purposes only. Ethical hacking and security testing should only be performed on authorized systems.


