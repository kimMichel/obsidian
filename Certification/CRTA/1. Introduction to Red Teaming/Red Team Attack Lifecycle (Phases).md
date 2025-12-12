High level overview of Red Team Attack lifecycle is shown below:

![[Pasted image 20251211233541.png]]

This cycle tells the beginning to end phases of an Red Team engagement in an organization.

# Extensive OSINT

This phase generally deals with gathering more and more information about the target organization. Social media sites, platforms where employees are generally active are of primary focus.

Attackers with access to tons of information available in the internet tries to find out the sensitive ones which can be used for further exploitation purposes.

# Initial Access & Execution

Initial Access consists of using various entry vectors to gain access within the internal network.

There are ways like exploitation to External Remote Services, mis-configurations in Web Applications which may lead as gateway to the internal network.

There are a lot of ways to get initial access, however it depends on the technologies used by the organization which could be identified in the previous section.

Execution is attacker-controlled code running on the target machine. For example: An adversary might use a remote access tool to run command prompt that does network discovery.

# Persistence & Privilege Escalation

Attackers always look for hidden techniques to keep access to systems across restarts, changed credentials which could cut-off attacker access.

Examples: Resetting password of a low-profile user & using it as a backdoor to network.

Privilege escalation is gaining higher-level permissions on a system or network. Common approaches are to take advantage of system weakness, misconfigurations, and vulnerabilities.

Elevated Access Accounts:
- SYSTEM/root level
- Local Administrator
- User with admin-like capabilities
- Privileged Groups, etc.

# Lateral Movement

Lateral movement is when an attacker compromises or gains control of one asset within a network and then moves on from that device to others within the same network.

Attackers might install their own remote access tools to accomplish Lateral Movement or use legitimate credentials with native network and operating system tools, which may be stealthier.

Example:

- Internal Phishing: attackers may use internal phishing to gain access to additional information or exploit other users within the same organization after they already have access to accounts or systems within the environment.
- Remote Services: Threat Attackers may used valid credentials to log into services like SSH, VNC, RDP and then perform operations.

![[Pasted image 20251211235526.png]]

# Defensive Evasion

Defensive Evasion deals with avoiding detection throughout the compromise. Attackers bypass detection by obfuscating malicious scripts, hiding in trusted processes, and disabling security software.

Defensive evasion benefits from discovery but is more related to understanding how an attacker can avoid network defenders, whether through certain processes or knowing which security tools are on a system.

Example:
- Impair Defenses: This includes disabling Firewalls and anti-virus and detection capabilities that defenders can use to audit activity and identify malicious behavior.

# Discovery

Attacker head for situational awareness where they try to figure out organization environment. These techniques help adversaries observe the environment and orient themselves before deciding how to act.

This helps a lot in gathering the whereabouts and critical assets located in the network architecture.

Example:
- File and Directory Discovery: Attackers enumerate files and directories or may search in specific locations of a host or network share for certain information within a file system.

# Data Collection

Data collection is the process of gathering and measuring information from established system. The data collected can be any sensitive information present in a system/network.

Example:
- Archive Collected Data: An adversary may compress and/or encrypt data that is collected prior to exfiltration.
- Clipboard Data: Attackers may collect data stored in the clipboard from users copying information within or between applications.

# Data Exfiltration

Once all the critical data has been identified and packed, attackers will try to steal data from the computer/network. Attackers can also compress and encrypt the collected data.

Examples:
- Automated Exfiltration: Attackers may exfiltrate data, such as sensitive documents, through the use of automated processing after being gathered during Collection.
- Exfiltration over Physical Medium: Attackers may attempt to exfiltrate data via a physical medium, such as a removable drive.

