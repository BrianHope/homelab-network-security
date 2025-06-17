Lab Finding #1: Why OPNsense could not block the SSH brute force attack

Setup:
Attacker - Ubuntu VM1
Target - Ubuntu VM2
Firewall - OPNsense with NAT WAN and internal LAN

Attack Summary:
- Used Hydra to simulate an SSH brute force attack going from VM1 to VM2
Command - hydra -l ubuntu -P rockyou.txt ssh://192.168.1.X
- Approximately 315 loign attempts over 3 minutes (105 attempts per minute)
- Captured traffic on the other end using tcpdump

Defense Solution:
- Confifure firewall to block all traffic between VMs

Solution Result:
- Despite the firewall rule being applied, the attack continuted on

Root Cause:
- Due to both machines being on the same LAN their traffic was being switched internally at Layer 2. 
The traffic was able to flow directly between the machines without passing through the firewall.
Becuase the firewall is only able to see traffic that crosses interfaces, the traffic was not stopped.

Key Learning:
In order to control traffic between to VMs, they must be placed on sepreate LAN/VLANs so the traffic is routed through the firewall.

Next Steps:
- Plan a segmented network design (LAN or VLAN)
- Apply the firewall rules once again
