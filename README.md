# home-lab-setup
A virtual lab for practicing attack simulations and log analysis.

## Network Diagram

<img width="649" height="589" alt="image" src="https://github.com/user-attachments/assets/2a97429b-c8f6-4060-a3e7-bdb0ee2e5253" />



## Lab Environment

- Hypervisor: VirtualBox on Windows
  
- Network: Nat Network, 10.0.2.0/24

  | Hostname   | OS            | Role     | IP       |
|------------|---------------|----------|----------|
| kali       | Kali Linux    | Attacker | 10.0.2.5 |
| wbserver   | Ubuntu Server | Target   | 10.0.2.3 |
| win-client | Windows 10    | Target   | 10.0.2.6 |

  ## Setup Notes

 ### 1. Virtual Network

 
Created a NAT Network in VirtualBox so the VMs can reach each other and download updates

- File -> Tools -> Network Manager -> NAT Networks -> Create
  
- Name: LabNet, IPv4 prefix: 10.0.2.0/24, DHCP enabled

- Each VM: Settings -> Network -> Adapter 1 -> Nat Network -> LabNet

### 2. Kali Linux (attacker)

- Installed ISO file from kali.org

- Machine -> New -> selected the ISO file

- Do the installation process

### 3. Ubuntu Server (target)

- Installed OpenSSH so Kali can connect

- Confirmed the IP with ip a

### 4. Windows (target / endpoint)

- Confirmed IP with ipconfig

### 5. Connectivity Test

- Pinged all VMs from Kali to test the network

  <img width="663" height="531" alt="image" src="https://github.com/user-attachments/assets/52ee2619-ae87-46f5-a659-b7a7a092528d" />

  ## Troubleshooting

  ### 1. All VMs showed as inaccessible

- Problem: Every VM failed to load with error code D:\tinderboxa\win-7.2\src\VBox\Main\src-server\MachineImpl.cpp[999] (long __cdecl Machine::i_registeredInit(void)).

- Cause: Host drive ran out of space and the VMs .vbox setting files were truncated to 0 KB

- Fix: Cleared up cache files and storage, and restored each VM from its .vbox-prev backup

### 2. Pings to Windows VM failed
- Problem: The other VMs pings couldn't reach the Windows VM

- Cause: The VM's adapter defaulted to NAT, which isolates it, and Windows Firewall blocks inbound ICMP echo requests by default

- Fix: Moved the adapter onto the same network as the other VMs and added an inbound firewall rule allowing ICMPv4 echo requests. Screenshot of pings above prove that it works now

  ## Exercises
