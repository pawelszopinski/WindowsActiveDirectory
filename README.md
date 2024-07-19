# WindowsActiveDirectory

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
