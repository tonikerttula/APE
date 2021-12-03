# Custom Excercise with Metasploitable 2

You'll need to set up Metasploitable 2 for this exercise, you can do so by following this [guide](https://github.com/tonikerttula/APE/blob/main/metasploitable2installation.md)

We can use many different tactics when attacking Metasploitable 2. In this excercise, we are going to use from the Att&ck the following tactics and techniques:

1. Reconnaissance: Active Scanning - Vulnerability Scanning
2. Credential Access: Brute Force - Credential Stuffing
3. Collection: Data from Local System
4. Exfiltration
5. Impact: Account Access Removal

Start up Kali and Metasploitable in the same network by making sure they are both set to Host-only adapter in the Network tab in the Virtual Box Manager Settings. Your task is to:

1. Find vulnerabilities in the Metasploitable machine, which you could use to get access.
2. Get in the Machine
3. Find something interesting (for example /etc/shadow/)
4. Extract the finding
5. Remove the original user's access to the machine.

