# ICMP-Packet-Analysis
Analyzing Internet Control Message Protocol (ICMP) traffic between two virtual machines using Wireshark,
focusing on echo requests and replies to better understand packet behavior, timing, and potential security implicants.

**Objective**
- Establishing a Host-Only network connection between a Kali Linux and an Ubuntu virtual machine.
  - Launch Wireshark on the Ubuntu VM to monitor incoming network traffic.
    - Sent ICMP echo requests from the Kali Machine to the Ubuntu VM's Ip address.
      - Apply icmp display filter in Wireshark to isolate ICMP packets for analysis.
        - Examine captured ICMP packets, focusing on types, codes, TTL, and source/destination information.

**Tools Used**
- Kali Linux (Attacker (Ip: 192.168.37.128))
  - Ubuntu (Victim (Ip: 192.168.37.130))
    - Wireshark
      - VMware Workstation Pro
        - VirutalBox Host-Only Adapter (VMnet1)
          - Google

      **Lab Report**
  
  **Steps Taken**

**Configured Host-Only Network**
- Ensuring both VMs were assigned Ips in the same subnet via Host-Only adapter.

**Packet Capture**
- Launching Wireshark on the Ubuntu VM.
  - Set capture filtre to interface traffic. (Default Settings)

**Initiated ICMP Echo Requests**
- Kali Linux, ran **ping** command targetting **192.168.37.130**.

**Filtered ICMP Traffic**
- Applied display filter: **icmp** in Wireshark to isolate echo requests and replies.

**Inspected Packet Details**
- ICMP types, TTL, Sequence Numbers, Identifiers, and Response times.

**Packet Behvaior Observation**
- Traffic Direction
  - Request: From Kali (192.168.37.128) --> Ubuntu (192.168.37.130)
    - Reply: From Ubuntu (192.168.37.130) --> Kali (192.168.37.128)

**ICMP Packet Types**
- Type **8** = **Echo Request**
  - Type **0** = **Echo Reply**

**Identifiers & Sequence Numbers**
- All packets used **id=0x0002**, most likely the default from ping utility.
  - Sequence numbers incremented by one per request, allowing for round-trip time tracking.

**TTL (Time To Live)**
- All packets show **TTL=64**, default for Linux Systems.

**Round-Trip Indicators**
- Wireshark showed "reply in #X" and "request in #Y" (#X, #Y are Referring to Numbers), confirming the bidirectional ICMP communication with matching pairs.

**No Packet Loss**
- All echo requests were answered with replies, indicating that there were no packet loss.

**Screenshot**
- <img width="1230" height="763" alt="image" src="https://github.com/user-attachments/assets/a476f5ba-47af-4242-bb23-57b97fdf34bb" />
  - <img width="1475" height="929" alt="image" src="https://github.com/user-attachments/assets/dd6a6266-6b3b-47a3-8e14-543fa3f8016c" />
