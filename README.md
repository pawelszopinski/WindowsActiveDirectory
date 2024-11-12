# Basic Windows Active Directory Concepts and Definitions

**Active Directory (AD)** is a directory service that Microsoft developed for Windows domain networks. It's included in most Windows Server operating systems as a set of processes and services. Here are some of the key concepts and definitions:

1. **Domain**: A domain is a logical group of network objects (computers, users, devices) that share the same Active Directory database. 

2. **Tree**: A tree is a collection of one or more domains, organized in a hierarchy. All domains in a tree share a common schema and global catalog, a database that contains information about all objects in the tree.

3. **Forest**: A forest is a collection of trees that share a common global catalog, directory schema, logical structure, and directory configuration. It's the highest level of organization within Active Directory.

4. **Organizational Unit (OU)**: An organizational unit is a subdivision within an Active Directory into which you can place users, groups, computers, and other organizational units. It's the smallest unit to which you can delegate administrative tasks.

5. **Domain Controller (DC)**: A domain controller is a server that responds to security authentication requests (logging in, checking permissions, etc.) within a Windows Server domain.

6. **Group Policy**: Group Policy allows administrators to implement specific configurations for users and computers. Group Policy settings are contained in Group Policy objects (GPOs), which are linked to Active Directory containers like sites, domains, or organizational units.

7. **Lightweight Directory Access Protocol (LDAP)**: LDAP is a protocol used to access and maintain distributed directory information services over an Internet Protocol (IP) network.

8. **Schema**: The schema is the Active Directory component that defines all the objects and attributes that the directory service uses to store data.

9. **Global Catalog**: It's a distributed data repository that contains a searchable, partial representation of every object in every domain in a forest.

10. **Trusts**: Trusts are authentication pipelines that must be established between domains, so that users in one domain can access resources from another domain.

11. **Replication**: Replication is the process by which the changes to Active Directory objects are copied across DCs.

The main purpose of Active Directory is to provide central authentication and authorization services for Windows-based computers.

# Active Directory Home Lab Scenario

This scenario will guide you through setting up a basic Active Directory environment using virtual machines.

## Prerequisites

- A machine capable of running multiple virtual machines. 8GB of RAM is recommended at the minimum.
- Virtualization software (e.g., VMWare, VirtualBox).
- Windows Server ISO for creating virtual machines.

## Procedure

1. **Setup Virtual Machines**: 
   - Create three virtual machines (VMs) using your virtualization software. 
   - Install Windows Server on each VM.

2. **Setup the Domain Controller**:
   - On one of the VMs, install the Active Directory Domain Services role. 
   - Run the configuration wizard and create a new forest and domain. This VM will act as the primary Domain Controller (DC).

3. **Setup an Additional Domain Controller**:
   - On another VM, install the Active Directory Domain Services role. 
   - Run the configuration wizard, but this time, select the option to add a domain controller to an existing domain. This VM will act as a secondary DC.

4. **Setup a Member Server**:
   - The third VM will be a member server. 
   - Join this server to the domain you created earlier.

## Practice Concepts

1. **Domain**: Explore how to manage objects in your new domain, like creating and managing user accounts.

2. **Tree and Forest**: Create a new domain in your existing forest to understand the concept of a tree. If your machine has enough resources, create a new forest with a separate domain.

3. **Organizational Unit (OU)**: Create different OUs in your domain and manage objects within them.

4. **Domain Controller (DC)**: Understand the roles and features of the primary and secondary domain controllers.

5. **Group Policy**: Create Group Policy Objects (GPOs) and link them to your OUs. Test the policies by logging in from the member server.

6. **Lightweight Directory Access Protocol (LDAP)**: Use the 'ldp' utility on your member server to connect to your domain controller using LDAP.

7. **Schema**: Explore the Active Directory Schema snap-in to understand the objects and attributes in your domain.

8. **Global Catalog**: Explore the global catalog using 'ldp' or another LDAP client.

9. **Trusts**: If you created a new domain, set up a trust relationship between your two domains.

10. **Replication**: Make changes on the primary DC and observe how these changes are replicated to the secondary DC.

Remember, the goal is to learn by doing. Don't be afraid to break things in your lab environment, as it's a great opportunity to learn how to fix them.

# Specific Scenarios

My goal is to understand a basics of Windows networking and set up a basic lab that will include:
1.Domain Controller(DC) with two NICs (Internal and Internet).
One NIC will connect with the internal network(1k+ users) with one example client(Client1).Second NIC of DC will be responsible to connection to Internet.

 Elements of Lab:

 1. Virtual Box (VB)
 2. Windows 2019 server(VM)
 3. Windows 10(VM)

Manual:

1. We need to be sure our W2019VM has two network adapters. You can make it happen in VB settings > Network.
Adapter 1 : NAT
Adapter 2 : Internal Network
2.Rename adapters in System>Network Connections (W2019VM) and assign IP address.
Use the following IP address:
IP: 172.16.0.1
Subnet Mask: 255.255.255.0
Default gateway: <empty>
Use the following DNS server:
Preferred DNS server: 127.0.0.1/IP address
3.Rename computer to DC
4.Create Active Directory(AD),Domain Services
and domain

### 4.1 Configure this local server >add roles and features>Next> Active Domain Services>Add Features>Next>Install

### 4.2 Domain Services

  Post-depoyment config (yellow warning sign)
    Add a new forest - - mydomain.com
    Set a password

#### 4.2.1 Dedicated admin account

Windows Administrative Tools > Active Directory Users and Computers
Create Organizational Unit (name it)
In that group create a new user (naming convention) and make him member of admin group(Domain Names)
