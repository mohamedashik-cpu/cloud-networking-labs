# 02 — AWS VPC Basics

**Status:** Planned — complete the lab only after AWS account activation and billing safety checks.  
**Goal:** Create and understand a basic AWS VPC network without launching compute resources.

## Before You Start

- Confirm the AWS account is fully activated and identify which account plan/credits apply.
- Enable MFA and protect the root user; do not create root access keys.
- Create a zero-spend budget and billing notifications. **Alerts are not a hard spending cap.**
- Review current AWS pricing and the account's service restrictions.
- Do not proceed if you cannot confirm billing safety.

## Design

Example addressing plan:

| Component | Name | Example setting |
|---|---|---|
| VPC | `CloudNet-Lab-VPC` | `10.0.0.0/16` |
| Public subnet | `CloudNet-Public-Subnet` | `10.0.1.0/24` |
| Private subnet | `CloudNet-Private-Subnet` | `10.0.2.0/24` |
| Internet Gateway | `CloudNet-IGW` | Attach to the VPC |
| Public route table | `CloudNet-Public-RT` | Add `0.0.0.0/0` to the Internet Gateway and associate the public subnet |

Choose one Availability Zone for both subnets for this introductory exercise. This is a learning design, not a production high-availability architecture.

## Procedure

1. Open the [Amazon VPC console](https://console.aws.amazon.com/vpc/) and select the Mumbai region (`ap-south-1`).
2. Create the VPC using the example CIDR above; leave IPv6 disabled for this introductory lab unless you are specifically studying IPv6.
3. Create the public and private subnets with the listed CIDRs.
4. Create an Internet Gateway and attach it to the VPC.
5. Create a public route table. Add `0.0.0.0/0` with the Internet Gateway as target.
6. Associate the public subnet with that route table.
7. Keep the private subnet without an Internet Gateway default route. Do not create a NAT Gateway for this lab.
8. Inspect the VPC, subnet, route table, and Internet Gateway details to verify the configuration.

## Important Networking Notes

- A route to an Internet Gateway alone does not make a resource reachable from the internet. Public IPv4 addressing, security rules, and other conditions also matter.
- A subnet is not automatically public or private by its name; routing and resource configuration determine connectivity.
- Do not launch EC2 instances for this first exercise.
- Do not create NAT Gateways, load balancers, VPC endpoints, VPNs, or other paid resources as part of this lab.

## Cost Safety

VPCs, subnets, route tables, and Internet Gateways generally do not have an hourly charge by themselves, but pricing can change and other related services may incur charges. NAT Gateways, compute, public IPv4 addresses, data transfer, and other resources can cost money. **Check current pricing before creating any resource.** Do not assume a free-tier label means every usage pattern is free.

## Verification Checklist

- [ ] VPC CIDR is `10.0.0.0/16`.
- [ ] Subnets use non-overlapping `/24` CIDRs.
- [ ] Internet Gateway is attached to the intended VPC.
- [ ] Public route table has `0.0.0.0/0` pointing to the Internet Gateway.
- [ ] Public subnet is associated with the public route table.
- [ ] Private subnet has no default route to an Internet Gateway or NAT Gateway.
- [ ] No compute or other intentionally billable resources were created.
- [ ] Screenshots are sanitized before publishing.

## Cleanup

After verification, delete the route-table association if needed, then delete the route table, detach and delete the Internet Gateway, delete the subnets, and finally delete the VPC. AWS may require dependent resources or associations to be removed first. Confirm the console shows no lab resources remaining.

## Lab Results

Fill this section only after performing the lab:

- Date completed:
- Region:
- What I verified:
- Issue encountered and fix:
- Cleanup verified:
