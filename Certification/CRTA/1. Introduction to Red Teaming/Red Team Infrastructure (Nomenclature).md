# C2 Server

These are used by attackers to maintain communications with compromised systems within a target network.

# Payload Server

This is a dedicated server hosting all the malicious scripts, executable and this is accessible from both attacker and victim network.

# Redirector Server

A redirector is a system that proxies all traffic to your command and control server. Threat actors doesn't use one system to launch attacks and get shells. They setup multiple systems to act as pivot points (redirectors) back to their C2 Server.

These prevent the client from being able to see our actual C2, and should be easy to spin up and tear down. It sits between victim environment and attacker network, listens for connection from the target machine and forward it back to the attacker.

It protects the original location of the team server.

# Adversary Emulation

Is mimicking of someone or something else. Based on threat intelligence, you determine FIN10 group is most likely to target an organization.

Example:
- To emulate this adversary, you mimic the TTPs they use and test those in your environment. You behave exactly like they would.

# Adversary Simulation

You want make it look like a real attack is happening while there is no real adversary. You make use of TTPs that work in the environment at hand, irrespective of which APT actually uses them.

# Advanced Persistent Threat (APT)

An advanced persistent threat is a stealthy threat actor, typically a nation state or state-sponsored group, which gains unauthorized access to a computer network and remains undetected for an extended period.

# Exploit

It is the actual code through which can attacker take advantage of a particular loop-hole.

# Vulnerability

- The loop-hole existing in a particular software or hardware can be called as vulnerability.
- It can also be understood as a weakest link which allows an attacker to compromise the system.

# De-Militarized Zone Network (DMZ Network)

It is a network (physical or logical) used to connect hosts that provide an interface to an untrusted external network. The system that are most vulnerable to attack are those that provide services to users outside of the local area network, such as email, Web, and Domain Name System (DNS) servers are present inside a DMZ.

The ultimate goal of a DMZ is to allow access to resources from untrusted networks while keeping the private network secured.

# Militarized Zone Network (MZ network)

Zone having maximum security and is one of the most secure segment in the environment. Contains critical information about the organization, etc. All operations in the organization is managed from Militarized network.

# Tactics, Techniques and Procedures (TTPs)

TTPs explains how threat actors orchestrate and manage cyber-attacks. It explains the methods associated with a specific threat actors or a group of threat actors.

A "Tactic" is the highest-level description of threat actor behavior.

"Techniques" gives a more detailed description of behavior in the context of a tactic.

"Procedures" an even lower-level, highly detailed description in the context of a technique.

# Listener

Listener waits for an incoming connection from the target machine. In our lab scenario, we will listen on our kali machine and the target machine can connect back to our machine after successful exploitation.

Basically listening means opening a port and waiting for connection from the target machine. Tools like netcat is one of the best example available for both windows and linux platforms. 

# Exploitation

Exploitation is phase to be performed after proper identification of a vulnerability. A service running on a system, a Web application, software are the primary target for exploitation.

Improper identification of the vulnerability with various incompatibility issues may crash the vulnerable/target service or software. Hence the targets must be intensely enumerated before entering in this phase.

Basically, in this phase the attacker enters the target system after taking advantage of the existing vulnerability in the product. The access can be physical or remote, but we will demonstrate in a remote situation. If the exploit succeed, the actual code of the payload runs.

Scenario specific example:

![[Pasted image 20251215172653.png]]

### Singles

These are self-contained payload assigned to do a specific task that is, create a user, or a bind shell.

Example: payload/windows/adduser

### Stagers

These type are payload are used to download large payload to the target machine from the attacker machine.

Creates a network connection between attacker & compromised machine.

Example: payload/windows/shell/bind_tcp

### Stages

These are large payload downloaded by the stagers & then executed. Assigned to do complex tasks like Remote Desktop, meterpreter, etc.

Example: payload/windows/shell/bind_tcp

### Shells

Are non-GUI interaction with the system, one can interact & manage the environment of the system through shell.

It is used for administration purposes & at times described fruitful compared to GUI.

Examples:
- In Windows:
	- Command Prompt
	- Power Shell
- In Linux
	- Bash shell
	- sh shell

# Reverse Shells

Here, the target machine connects back to the attacker box. All communication goes through specific TCP ports. 

We need to have listener active on the attacker machine. 

We will take example of the Swiss army knife tool (aka netcat).

### Overview of reverse shell

![[Pasted image 20251215173618.png]]

# Bind Shells

Here the attacker machine connects to the victim system. The attacker opens a TCP port on the victim machine & host a shell.

That means anyone who connect to the target machine & on a specific port will be presented with a shell.

The shell can then be used to spread the compromise.

### Overview of Bind Shell

![[Pasted image 20251215173802.png]]

