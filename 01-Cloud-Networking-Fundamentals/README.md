# 01 — Cloud Networking Fundamentals

**Status:** Planned  
**Goal:** Understand how traditional networking concepts map to cloud networks before deploying resources.

## Learning Objectives

- Explain the difference between an on-premises network and a cloud virtual network.
- Understand CIDR notation and private IPv4 address ranges.
- Plan non-overlapping network ranges and subnets.
- Explain route tables, next hops, gateways, DNS, and network segmentation.
- Describe the roles of security groups and network ACLs at a high level.

## Key Concepts

| Concept | What to understand |
|---|---|
| VPC / VNet | A logically isolated network in a cloud provider |
| CIDR | A notation for an IP network, such as `10.0.0.0/16` |
| Subnet | A smaller IP range carved from a larger network |
| Route table | Rules that select the next hop for traffic |
| Internet gateway | A cloud component that enables eligible internet connectivity for a network |
| NAT | Allows private-side resources to initiate outbound connections without accepting unsolicited inbound connections through that NAT path |
| Security group | A stateful virtual firewall associated with supported resources/interfaces |
| Network ACL | A subnet-level, stateless traffic filter in AWS |
| DNS | Resolves names to IP addresses |

## Practice — Plan a Network on Paper

Use this example only as a planning exercise; no cloud account is needed.

| Network segment | Example CIDR | Intended use |
|---|---|---|
| Overall lab network | `10.20.0.0/16` | Reserved lab address space |
| Public subnet | `10.20.1.0/24` | Future resources that require a public route |
| Private subnet | `10.20.2.0/24` | Future internal resources |

### Questions to Answer

1. Why does a `/24` subnet contain 256 total IPv4 addresses?
2. Do the two example subnets overlap?
3. What route would a public subnet need for internet-bound IPv4 traffic?
4. Why does a private subnet not become internet-accessible just because a route table exists?
5. What is the difference between routing and firewall rules?

## Verification Checklist

- [ ] Explain `/16` versus `/24` in your own words.
- [ ] Calculate the network and usable address range for a sample CIDR.
- [ ] Draw a diagram with a VPC/VNet, two subnets, and route tables.
- [ ] Explain the intended traffic path for each subnet.
- [ ] Add your own notes and mark the lab complete only after doing the exercises.

## Cost

No cloud resources are required for this lab. Complete the exercises with notes, a diagram, or a local subnet calculator.
