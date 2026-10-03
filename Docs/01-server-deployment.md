\# DC01 - Windows Server 2025 Deployment



\## Objective



Deploy and configure the first Windows Server in a virtual enterprise lab. DC01 will eventually provide Active Directory Domain Services (AD DS) and DNS services for the lab environment.



\## Virtual Machine Configuration



| Setting | Configuration |

|---|---|

| Hypervisor | Oracle VirtualBox |

| Operating System | Windows Server 2025 Standard Evaluation |

| Installation Type | Desktop Experience |

| Memory | 4 GB |

| Virtual CPUs | 2 |

| Virtual Disk | 80 GB dynamically allocated |

| Network Adapter 1 | NAT |

| Network Adapter 2 | Internal Network (SYSADMIN-LAN) |



\## Network Design



DC01 uses two virtual network interfaces.



\### NAT-INTERNET



The NAT interface provides outbound network and Internet connectivity through VirtualBox.



The interface receives its IPv4 configuration through VirtualBox DHCP.



\### SYSADMIN-LAN



The SYSADMIN-LAN interface connects DC01 to the isolated internal lab network.



Configuration:



\- Network: `10.10.10.0/24`

\- DC01 IPv4 address: `10.10.10.10`

\- Subnet prefix: `/24`

\- Default gateway: None



A default gateway was intentionally not configured on SYSADMIN-LAN because outbound connectivity is provided by the separate NAT-INTERNET interface.



\## Interface Identification



The Windows network interfaces were mapped to their corresponding VirtualBox adapters by comparing MAC addresses.



The interfaces were then renamed from the default Windows names to:



\- `NAT-INTERNET`

\- `SYSADMIN-LAN`



Meaningful interface names make administration and troubleshooting easier, particularly on systems with multiple network adapters.



\## Connectivity Verification



Connectivity was tested in stages:



1\. VirtualBox NAT gateway connectivity

2\. External IPv4 connectivity

3\. DNS name resolution



Commands used:



```powershell

ping 10.0.2.2

ping 8.8.8.8

Resolve-DnsName microsoft.com

