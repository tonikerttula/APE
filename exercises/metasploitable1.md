# Custom Excercise with Metasploitable 2 (editing in progress)

You'll need to set up Metasploitable 2 for this exercise, you can do so by following this [guide](https://github.com/tonikerttula/APE/blob/main/installs/metasploitable2installation.md)

#### WARNING! Remember to make sure you only scan and attack machines and IP-addresses that you own, and that are on your own system. Scanning systems over the internet without permission is against the law (double check the correct ip-address when using nmap, or other tools). Make sure you have both Kali and Metasploitable in "Host-only adapter" setting in VirtualBox, you can test this by pinging 8.8.8.8 in Kali, if the network is unreachable, you are not connected to the internet.

We can use many different tactics when attacking Metasploitable 2. In this excercise, we are going to use from the Att&ck the following tactics and techniques:

1. Discovery: Network Sniffing
2. Reconnaissance: Active Scanning - Vulnerability Scanning
3. Credential Access: Brute Force - Credential Stuffing
4. Collection: Data from Local System
5. Exfiltration
6. Impact: Account Access Removal

Start up Kali and Metasploitable in the same network by making sure they are both set to Host-only adapter in the Network tab in the Virtual Box Manager Settings. ___Your task is to:___

1. Discover IP-address for the target machine.
2. Find vulnerabilities in the Metasploitable machine, which you could use to get access. 
3. Get in the Machine
4. Find something interesting (for example /etc/shadow/)
5. Extract the finding
6. Remove the original user's access to the machine.

_Hints:_ Nmap is a useful tool, metasploit in Kali is a great resource (open by using the command __msfconsole__). Google is helpful when trying to brainstorm an idea. See the tactics and techniques listed above.

[My solution](https://github.com/tonikerttula/APE/blob/main/solutions/Excercise1solution.md)
