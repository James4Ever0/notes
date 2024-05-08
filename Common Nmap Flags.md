---
title: Common Nmap Flags
created: '2024-05-08T15:08:01.700Z'
modified: '2024-05-08T15:11:29.719Z'
---

# Common Nmap Flags

Typically, if one wants to detect port somehow dropped by cloud service providers like AWS, the flag `-sS` or SYN stealth scan shall be enough.

Further info can be collected once the port has been confirmed to be open.

---

1. **-sS (TCP SYN Scan)**:
   - This flag instructs Nmap to perform a TCP SYN scan, also known as a half-open scan. It sends SYN packets to the target ports and analyzes the responses to determine which ports are open, closed, or filtered.

2. **-sT (TCP Connect Scan)**:
   - This flag tells Nmap to perform a TCP connect scan, in which Nmap completes the full TCP three-way handshake to determine the state of the target ports.

3. **-sU (UDP Scan)**:
   - This flag enables Nmap to perform a UDP scan, used to identify open UDP ports on the target system. UDP scans can be slower than TCP scans due to the stateless nature of the UDP protocol.

4. **-p (Port Specification)**:
   - The `-p` flag allows you to specify which ports to scan. You can specify individual ports, ranges of ports, or combination of both. For example, `-p 1-1000` scans ports 1 through 1000.

5. **-A (Aggressive Scan)**:
   - The `-A` flag enables OS detection, version detection, script scanning, and traceroute. It's a comprehensive option that provides detailed information about the target.

6. **-O (Enable OS Detection)**:
   - This flag instructs Nmap to attempt to determine the operating system running on the target host based on various characteristics observed during the scan.

7. **-v (Verbose Output)**:
   - The `-v` flag increases the verbosity of Nmap's output, providing more detailed information about the scan process.

8. **-T (Timing Template)**:
   - The `-T` flag allows you to specify the timing template for the scan. Options range from 0 (paranoid) to 5 (insane), affecting the speed and aggressiveness of the scan.

9. **-O (Output to File)**:
   - The `-o` flag allows you to specify the output format and destination for the scan results. For example, `-oN scan_results.txt` saves the output in normal format to a file named `scan_results.txt`.

