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


