# Enterprise Network

Enterprise network consists of various role-assigned servers, which are given bellow:

- Web Server:
	- Its is software that understands URLs (web addresses) and HTTP (the protocol your browser uses to view webpages). An HTTP server can be accessed through the domain names of the websites it stores, and it delivers the content of these hosted websites to the end user's device.
	- Can also be through as a computer where the web content is stored. Basically web server is used to host the web sites.
	- External Web Servers are placed in DMZ network, which serves request of the clients.
	- These are generally connected to the internal environment (enterprise network).
- Mail-Server:
	- A mail server (or e-mail server) is a server that handles and delivers e-mail over a network, usually over the internet.
	- A mail server can receive e-mails from client computers and deliver them to other mail servers. A mail server can also deliver e-mails to client computers.
	- When you press the "Send" button in your e-mail program (e-mail client) the program will connect to a server on the network / Internet that is called an SMTP server. SMTP is an acronym for Simple Mail Transfer Protocol and it is a protocol that is used when e-mails are delivered from clients to servers and from servers to other servers.
	- When you download e-mails to your e-mail program the program will connect to a server on the net that is known as a POP3 server.
- Database-Server (or SQL Server):
	- Database servers are used to store and manage databases that are stored on the server and to provide data access for authorized users.
	- A database server is useful for organizations that have a lot of data to deal with on a regular basis.
	- It also allows users and applications to centrally access the data across the network.
	- Various operations like modifying data, adding and deleting data is through SQL queries.
- Bastion-Host (Jump-Server):
	- A bastion host is a special-purpose computer on a network specifically designed and configured to withstand attacks.
	- The computer generally host a single application, for example a proxy server, and all other services are removed or limited to reduce the threat to the computer.
	- They are typically accessed using SSH or RDP.
	- Once remote connectivity has been established with the bastion host, it then acts as a 'jump' server, allowing you to use SSH or RDP to log in to other instances (within private subnets).
- Automation Server:
	- Automation servers are a crucial aspect of software development workflows.
	- It helps automate the parts of software development related to building, testing, and deploying facilitating continuous integration and continuous delivery.
	- Some of the examples are:
		- Jenkins Server
		- TeamCity
		- Bamboo
- Active Directory:
	- As the name suggests, it is a directory (or database) which:
		- Manages the resources of organization like (users, computers, shares)
		- Provides Access rules that govern the relationships between these resources.
		- Stores information about objects on the network and makes it available to users and admins.
	- Product of Microsoft "Active Directory Service enables centralized, secure management of an entire network, which might span a building, a city, or multiple locations throughout the world".
	- Provides centralized management of all the organization virtual assets.

![[Pasted image 20251215175621.png]]

# Active Directory Forests/Domain

Forest is a single instance of AD. It is basically a collection of Domain Controllers that trust one another.

Domains can be thought as containers within the scope of a Forest.

Organizational Units (OU's) are logical grouping of users, computers and other resources.

Groups:
- Collection of users or other groups.
- Privileged, non-privileged.

# Active Directory Objects

The physical entities that make up an organized network.

Domain Users:
- Users account that are allowed to authenticate to machines/servers in the domain.

Domain Groups (Global Groups):
- It can be used to assign permissions to access resources in any domain.

Domain Computers:
- Machines that are connected to a domain and hence become a member of a domain.

Domain Controller:
- Server located centrally that responds to security authentication request and manage various resources like computers, users, groups.

Group Policy Objects (GPOs):
- Collection of policies that are applied to a set of user, domain, domain object.

Ticket Granting Ticket (TGT):
- Ticket used specifically for authentication.

Ticket Granting Service (TGS):
- Ticket used specifically for authorization.

![[Pasted image 20251215180336.png]]

![[Pasted image 20251215180350.png]]

# Kerberos Authentication

In the Active Directory environment, all the queries and authentication process is done through tickets. Hence, no passwords are every travel to network.

A ticket is a form of authentication and authorization token and can be categorized as follows:
- Ticket Granting Ticket (TGT) for Authentication
- Ticket Granting Service (TGS) for Authorization

The ticket (TGT and TGS) are stored in memory and can be extracted for abusing purposes as these tickets represent user credentials.

The TGS can be used for accessing a specific service of a server in the domain.

# Kerberos Delegation

It allows an authenticated domain user credentials to be re-used to access resources hosted on a different server in a domain. This utility is useful in multi-tier applications or architecture.

For example: A domain user authenticates to a Application Server and the Application Server makes a call to the Database Server. The application server can request access to resources of the Database Server as the domain user (user is impersonated) and not as Application Server service account.

The service account for Application Server must be trusted for delegation to be able to make requests as an authenticated domain user.

# Types of Kerberos Delegation

Unconstrained Delegation:
- It allows the Application Server to request access to ANY service on any server in the domain.

Unconstrained Delegation is by-default enabled on Domain Controllers.

Constrained Delegation:
- It allows the Application Server to request access to ONLY specified services on specific servers.

# Domain Trusts

Trust represents relationship between two domains or forests which allows the users/services of one domain or forest to access resources in the other domain or forest.

Type of Trust:
- Parent-Child trust relationship
- Forest to Forest Trust relationship
- Tree-root Trust relationship

Trust identifies the entities in a domain or Forest.
# Authorization in Active Directory

Authorization means if a user is specifically permitted or denied to access a resource in the AD network. AD validates access to a resources based on the user's security token.

This security token is the procedure of checking whether a user is a part of Access Control List (ACL) for the requested object.

Security token comprises of:
- User Rights
- Group SID
- Individual SID

The primary means through which a security principal is identified when trying to access any securable object is an identifier called security identifier (SID) which is unique for each user or security group.

