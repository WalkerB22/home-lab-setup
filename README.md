# home-lab-setup
A virtual lab for practicing attack simulations and log analysis.

## Network Diagram

<img width="637" height="582" alt="home_lab_diagram" src="https://github.com/user-attachments/assets/ff024938-5f02-4df5-b667-1de88c56cb68" />


## Lab Environment

- Hypervisor: VirtualBox on Windows
  
- Network: Nat Network, 10.0.2.0/24

  Host Name   | OS           | Role     | IP       |
  
  Kali,         Kali Linux,      Attacker,   10.0.2.2

  ubuntu-srvr,  Ubuntu Server,   Target,      10.0.2.3

  win-client,   Windows 10,      Target,      10.0.2.4

  ## Setup Notes

 ## 1. Virutal Network

 
Created a NAT Network in VirtualBox so the VMs can reach each other and download upadtes

- File -> Tools -> Network Manager -> NAT Networks -> Create
  
- Name: Labnet, IPv4 prefix: 10.0.2.0/24, DHCP enabled

- Each VM: Settings -> Network -> Adapter 1 -> Nat Network -> LabNet

## 2. Kali Linux (attacker)

- Installed ISO file from kali.org

- Machine -> Add -> selected the ISO file

- Do the installation process

## 3. Ubuntu Server (target)

- Installed OpenSSH so Kali can connect

- Confirmed the IP with ip a

## 4. Windows (target / endpoint)

- Confirmed IP with ipconfig

## 5. Connectivity Test

- Pinged between every pair of VMs to confirm the network works
  ## Troubleshooting

  ## Exercises
