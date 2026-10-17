# Active Directory Home Lab

## Goal
Build a practice Active Directory domain, join a Windows 11
client, and test signing in with a domain user.

## Status
In progress — the Windows 11 client has successfully joined
the domain. Domain-user sign-in still needs testing.

## Setup
- Virtualisation platform: VMware
- Server: Windows Server running Active Directory Domain
  Services and DNS
- Client: Windows 11
- Domain: labshandson.lan
- Domain controller IP: 192.168.1.11
- Client IP: 192.168.1.101
- Subnet mask: 255.255.255.0

## Steps completed
- Set up a Windows Server domain controller and DNS service.
- Set up a Windows 11 client.
- Tested DNS discovery of the domain controller.
- Troubleshot client internet connectivity with ChatGPT's help.
- Successfully joined the Windows 11 client to labshandson.lan.

## Verification
Ran the following command from the Windows 11 client:

```cmd
nslookup -type=SRV _ldap._tcp.dc._msdcs.labshandson.lan 192.168.1.11
