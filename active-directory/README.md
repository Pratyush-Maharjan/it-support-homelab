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
```
The lookup successfully returned the domain controller:
win2k25-dc01.labshandson.lan.

The Windows 11 client successfully joined the domain.
Signing in with a domain user has not yet been verified.

## Problems and troubleshooting

### Client showed “No Internet”
During setup, the Windows 11 client showed “No Internet”.

The client initially had both the domain controller and router
listed as DNS servers. In this lab, the client should use the
domain controller's DNS service to locate Active Directory.

### Checks performed
- Successfully queried the domain controller for the domain's
  Active Directory DNS service record.
- Ran ping 1.1.1.1 to test external connectivity without DNS.
  The request timed out.
- Investigated gateway and DNS settings with ChatGPT's help.

### Outcome and remaining uncertainty
Connectivity appeared to return after troubleshooting.
The exact setting change that resolved the issue still
needs confirmation.

The client successfully joined the domain, but that alone
does not verify internet connectivity.

## What I learned
- Active Directory DNS records help clients find a
  domain controller.
- DNS resolves names into IP addresses.
- A default gateway routes traffic to other networks.
- Domain discovery and internet connectivity are
  separate things to test.
- A failed ping alone does not establish the root cause.
- Joining a domain and signing in with a domain user
  are separate milestones.

## Next steps
- Test signing into the client with a domain user.
- Review and record the final DNS and gateway settings.
- Confirm external name resolution and internet access.
- Add screenshots with passwords and personal
  information hidden.

## Learning resources and assistance
Used ChatGPT to help troubleshoot connectivity and
interpret network settings. The exact cause of the
internet issue still needs review.
