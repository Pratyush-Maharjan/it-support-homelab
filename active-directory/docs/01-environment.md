# Environment and architecture

[Back to overview](../README.md)

## Inventory

| Component | Recorded configuration | Evidence / qualification |
| --- | --- | --- |
| Virtualisation | VMware Workstation | Visible in screenshots and recordings |
| Domain | `labshandson.lan` | Visible in AD Users and Computers |
| First controller | `WIN2K25-DC01` | Windows Server 2025 lab naming; existing project notes record AD DS and DNS installation |
| Second controller | `WIN2K25-DC02` | Listed alongside DC01 as a global catalog |
| Client computers | `WIN11-CL01`, `WIN11-CL02`, `WIN11-CL03` | Three computer objects visible; Windows 11 VMs visible in VMware |
| DC01 address | `192.168.1.11` | Previously recorded lab setting; current adapter settings need recapturing |
| CL01 address | `192.168.1.101`, mask `255.255.255.0` | Previously recorded lab setting; current adapter settings need recapturing |
| DC02 / other client addresses | Not yet documented | Do not infer from the course's configuration |

The lab uses one domain and two domain controllers. Both controllers appear in the head-office site in the later Sites and Services screenshot. The branch and remote site definitions do not yet demonstrate a routed multi-site deployment.

## Build progression

1. Installed AD DS and DNS on the first server and created the domain, as recorded in the original project notes.
2. Joined the first Windows 11 client and tested AD DNS discovery.
3. Added two more client computer accounts, visible in the domain's Computers container.
4. Created the custom `LHO` OU hierarchy and organised the client objects under `WorkStations`.
5. Practised departmental account and security-group administration.
6. Added a second domain controller and compared `svc_sql` on both controllers.
7. Defined location sites and their IP subnet associations.

The evidence captures milestones rather than every installation screen. Functional levels, FSMO ownership, DC02's IP configuration and exact promotion options have not been independently captured.
