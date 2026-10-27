# BoardNet: Board Examination Communication Network

A Cisco Packet Tracer networking project that models communication between six HSC education boards in Bangladesh: Dhaka (DHK), Chattogram (CTG), Rajshahi (RAJ), Sylhet (SYL), Barishal (BAR), and Khulna (KHU).

> **Project type:** Computer Networks / Cisco Packet Tracer  
> **Group:** 2405 · **Section:** 24  
> **Base network:** `12.55.0.0/16` (derived from the student-ID digits used in the report)

## Overview

BoardNet is designed to support examination coordination and administrative communication across six regional board networks. The design includes routed inter-board connectivity, VLSM addressing, DHCP, central DNS, web servers, email servers, and redundant paths between DHK, KHU, and BAR.

## Network design

- **DHK, SYL, and RAJ** connect through a central coordination switch.
- **CTG** connects only to DHK and uses DHK as its path to the rest of the network.
- **DHK, KHU, and BAR** have direct point-to-point links forming a redundant triangle.
- **Routing:** RIPv2 between DHK/SYL/RAJ; static routes for the other boards; a default route on CTG; floating static routes provide backup paths.
- **DHCP:** DHK provides DHCP for DHK, CTG, SYL, and RAJ. KHU and BAR use dedicated local DHCP servers.
- **DNS:** Central DNS server at `12.55.0.2`.
- **Web:** `www.dhk.edu.bd` and `www.ctg.edu.bd`.
- **Email:** A local email server is provided for each board.

## Addressing plan

| Network | Network address | Prefix | Subnet mask |
|---|---|---:|---|
| DHK LAN | `12.55.0.0` | `/23` | `255.255.254.0` |
| CTG LAN | `12.55.2.0` | `/24` | `255.255.255.0` |
| RAJ LAN | `12.55.3.0` | `/24` | `255.255.255.0` |
| SYL LAN | `12.55.4.0` | `/24` | `255.255.255.0` |
| BAR LAN | `12.55.5.0` | `/25` | `255.255.255.128` |
| KHU LAN | `12.55.5.128` | `/25` | `255.255.255.128` |
| Central switch segment | `12.55.6.0` | `/29` | `255.255.255.248` |
| DHK–CTG | `12.55.6.8` | `/30` | `255.255.255.252` |
| DHK–KHU | `12.55.6.12` | `/30` | `255.255.255.252` |
| KHU–BAR | `12.55.6.16` | `/30` | `255.255.255.252` |
| BAR–DHK | `12.55.6.20` | `/30` | `255.255.255.252` |

See [`docs/BoardNet-Final-Report.pdf`](docs/BoardNet-Final-Report.pdf) for the full IP-addressing tables, router commands, service setup, and assumptions.

## Repository contents

```text
BoardNet-GitHub-Repository/
├── README.md
├── .gitignore
├── docs/
│   ├── BoardNet-Project-Brief.pdf
│   └── BoardNet-Final-Report.pdf
├── configs/
│   └── README.md
├── packet-tracer/
│   └── README.md
└── screenshots/
    └── README.md
```

### Important files to add

The uploaded materials contained the project brief and final report, but **no Cisco Packet Tracer `.pkt` topology file or separate PowerPoint presentation was included** in the files available for this repository package.

For a complete portfolio repository, add:
1. The working Packet Tracer file to `packet-tracer/BoardNet.pkt`.
2. The presentation to `docs/BoardNet-Presentation.pptx` (or PDF export).
3. Screenshots of the topology, successful DHCP leases, web access by domain name, cross-board email, and failover tests to `screenshots/`.

Only claim tests that you have actually run in Packet Tracer.

## How to review the project

1. Read the [project brief](docs/BoardNet-Project-Brief.pdf).
2. Read the [final report](docs/BoardNet-Final-Report.pdf).
3. Open `packet-tracer/BoardNet.pkt` in Cisco Packet Tracer once you add the actual file.
4. Verify connectivity and services using the checklist in [`packet-tracer/README.md`](packet-tracer/README.md).

## Validation checklist

- [ ] All six board LANs are present and addressed according to the VLSM plan.
- [ ] PCs receive addresses dynamically from the intended DHCP service.
- [ ] All boards resolve configured hostnames through the central DNS server.
- [ ] Devices across the network can access both web servers using domain names.
- [ ] Email can be sent between users on different boards.
- [ ] KHU can reach other networks through BAR if the DHK–KHU link fails.
- [ ] BAR can reach other networks through KHU if the DHK–BAR link fails.
- [ ] Screenshots and the `.pkt` file are committed to the repository.

## Notes

This repository organizes the supplied academic documentation. It does not claim that the Packet Tracer simulation has been independently executed or re-tested by the repository generator. Review and validate the topology and configurations before presenting it as a completed working simulation.
