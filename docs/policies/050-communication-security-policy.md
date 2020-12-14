---
id: communication-security-policy
title: Communication security policy
description:
---

## Background

We employ a number of controls to ensure the security of networks and data in transit.

## Objectives

- Outline controls for protecting networks
- Outline controls for data transmitted over networks
- Outline legal basis for data transfer

## Scope

All managed artifacts transmitted via internal and external networks are in scope.

Management of network infrastructure is the responsibility by our cloud provider and is therefore out of scope. Ensuring cloud networking services are configured securely is our responsibility and is therefore in scope.

## Policy

### Firewalls
<Link artifactId="iso27001/A.13.1.2, iso27001/A.14.1.2" kind="implements" />

Inbound firewalls are used to detect potential distributed denial of service (DDoS) attacks. Suspected attack sources are blocked automatically.

Firewalls are configured in deny-all mode are installed on all production hosts, with HTTP, HTTPS, and SSH ports opened as necessary.

All firewalls are highly available.

New firewall rules and configuration changes are tested before being deployed to production.

Firewall and cloud security group rules are reviewed every quarter.

### Intrusion detection
<Link artifactId="iso27001/A.13.1.2" kind="implements" />

Host-based intrusion detection software is used to monitor file system integrity and logs, and sends real-time alerts when suspicious changes are made to the file system, or when suspicious activity or suspected violations are spotted in the logs.

This generates reports that are reviewed by the Security Officer on a monthly basis.

Automatic monitoring is performed to identify patterns that signify the lack of availability of services and systems.

### Network vulnerability scanning
<Link artifactId="iso27001/A.13.1.2" kind="implements" />

Network and host vulnerability scanning is performed in line with the [technical-vulnerability-management-policy].

### Network attack protection
<Link artifactId="iso27001/A.13.1.2" kind="implements" />

The use of virtual private clouds (VPCs) ensures that most systems and applications are not accessible from the public internet, and therefore cannot be targeted directly by a DDoS attack.

At the cloud infrastructure layer, our cloud provider offers controls to prevent IP spoofing, unauthorised port scanning and packet sniffing.

### Network isolation
<Link artifactId="iso27001/A.13.1.3" kind="implements" />

Development, staging and production environments are logically separated.

Separate cloud provider accounts must be used for production workloads on the one hand, and development and staging workloads on the others.

Further separation between development and staging environmetns can be achieved using network separation e.g. virtual private clouds (VPCs).

Within a VPC, all SSL/TLS endpoints reside on public subnets, and all applications and databases on private subnets.

Applications and databases within a VPC can be accessed directly over SSH via a bastion host. Remote access to services within a VPC must go via a load balancer and bastion host.

Access to the bastion host is only allowed from a known pool of VPN egress IP addresses.

### Secure network connections
<Link artifactId="iso27001/A.13.1.1, iso27001/A.13.2.3, iso27001/A.14.1.3" kind="implements" />

Production environments must be accessed only over a secure VPN. For cloud environments, security groups must be used to deny all connections except those from the VPN.

Wireless networks managed in our offices are secured with the following configurations:
- All data in transit is encrypted using WPA2 encryption
- SSIDs are not broadcast (with the exception of the guest access network)
- Passwords are rotated on a quarterly basis.

Wireless guest access is available in the our offices:
- It is logically separate to employee WiFi access.
- Guests on the network are unable to communicate with other guests as their network traffic only routes outbound and not between hosts on the same network.
- All data in transit is encrypted using WPA2 encryption
- Passwords are rotated on a quarterly basis.

Network ports in the office are generally not live, so cannot be used to connect to the network.

When working remotely:
- The company VPN should be used for all communications. This includes using authorised laptops, mobile phones and tablets.
- A polarising privacy shield should be used when in a public place or customer office, or when a private place where the device screen cannot be safely kept out of view.

#### Web communication

All web communications must happen over encrypted channels using TLS, including web and email communication, in line with the [cryptography-policy].

API communication must require an authenticated user to present a valid bearer token to identify themselves and establish a session wherever possible.

Root CA certificate bundles should be kept up-to-date with frequent browser and operating system upgrades.

Clear text communications may not be used for transmitting company data of any kind.

#### Secure Shell (SSH) communication

Communications over SSH is considered secure when the client used has appropriate protection and controls, including login password, encrypted disk volumes and anti-malware protection.

Private SSH keys must be carefully protected with appropriate disk permissions.

### Legal requirements for data transfer
<Link artifactId="iso27001/A.13.2.1, iso27001/A.13.2.2, iso27001/A.13.2.4" kind="implements" />

Contracts or confidentiality agreements with third parties (e.g. customers, suppliers) address the requirements for secure transfer of information.

Staff obligations for confidentiality are addressed in their contracts of employment.
