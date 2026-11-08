# Hosted Private Cloud Services: What the Monthly Fee Buys, How It Differs From a VPC, and When Dedicated Hardware Wins

A hosted private cloud is a single-tenant environment running in a provider's data centre: compute, storage and network reserved for one organisation, with the provider handling maintenance, upgrades and security patching. As a managed product, it starts expensive. UpCloud's Dedicated Private Cloud, as published on its product page in September 2026, begins at **€3,190 per month**, and the page immediately invites you to ask for a personalised quote. That is the entry point for one node class, before you add storage.

That number explains why so many teams end up looking at dedicated hardware instead. If what you actually need is physical single-tenancy and a private network between your own machines, renting bare metal and building the cloud layer yourself costs a fraction of a managed contract. Spin Servers is the least expensive version of that route with verifiable published pricing: dedicated servers from **$49 to $79 a month** depending on configuration and location, with a free VPC that links your servers over a private layer-2 network at no extra charge.

Below: what the managed price includes that the cheap route doesn't, what the cheap route costs you in labour, and a straight answer on which one your team should pick.

> **Most readers building a private cloud on their own hardware should start with the $89/month Dallas configuration** — 2× E5-2630L v3 (16 cores, 32 threads), 256 GB RAM, 2× 1.6 TB SSD, 30 TB of transfer on a 10 Gbps port. RAM decides how many VMs you can pack onto a box, and 256 GB at that price is the sweet spot. Add a second identical server and the free VPC puts both on the same private network: a two-node private cloud for $178 a month, month-to-month, no setup fee.
>
> 👉 [See the Dallas and San Jose dedicated server configurations](https://bit.ly/Spinservers)

## Spin Servers dedicated server lineup and pricing

Two data centres, two price tiers. Dallas is the cheaper, centrally located facility; San Jose costs more but sits closer to West Coast and transpacific traffic.

**Dallas**

| Plan | Hardware | Network & billing | Price | Order |
| --- | --- | --- | --- | --- |
| Entry | Intel E3-1280 v5 (4 cores), 32 GB DDR4, 1 TB NVMe SSD | 10 Gbps port, 30 TB/mo, month-to-month | $49/mo | [ Order](https://bit.ly/Spinservers) |
| Standard | 2× E5-2630L v3 (16C/32T), 256 GB, 2× 1.6 TB SSD | 10 Gbps port, 30 TB/mo, month-to-month | $89/mo | [ Order](https://bit.ly/Spinservers) |
| High-core | 2× E5-2696 v3 (36 cores), 128 GB, 480 GB SSD | 10 Gbps port, 30 TB/mo, month-to-month | $139/mo | [ Order](https://bit.ly/Spinservers) |
| Flagship | AMD EPYC 7702P (64 cores), 512 GB (upgradable to 1 TB), 240 GB SSD + 7.84 TB NVMe | 10 Gbps port, 100 TB/mo, month-to-month | $449/mo | [ Order](https://bit.ly/Spinservers) |

**San Jose**

| Plan | Hardware | Network & billing | Price | Order |
| --- | --- | --- | --- | --- |
| Base | 2× E5-2630L v3 (16 cores), 64 GB, 1.6 TB SSD | 500 Mbps unmetered, month-to-month | $79/mo | [ Order](https://bit.ly/Spinservers) |
| Upgraded | 2× E5-2630L v3 (16C/32T), 256 GB, 2× 1.6 TB SSD | 1 Gbps unmetered, month-to-month | $99/mo | [ Order](https://bit.ly/Spinservers) |
| Large | 2× E5-2683 v4 (32C/64T), 512 GB, 2× 3.84 TB SSD | 10 Gbps port, 30 TB/mo, month-to-month | $239/mo | [ Order](https://bit.ly/Spinservers) |

Two things worth flagging before you read anything into those numbers. First, these figures come from public listings of the Spin Servers dedicated lineup rather than a live checkout, and entry pricing has been quoted at both $49 and $79 a month depending on configuration, location and what's in stock; confirm the figure on the order page before committing. Second, the $139 Dallas plan is the odd one out. It buys you 36 cores but drops to 128 GB of RAM and a 480 GB boot disk, which is the wrong trade for a private cloud. VM density is bound by memory far more often than by core count, so the $89 box with double the RAM and triple the storage is the better machine for this job, and it's cheaper.

Spin Servers also sells a KVM VPS line, from 2 vCPU / 2 GB RAM / 40 GB RAID-10 SSD up to 32 vCPU / 32 GB RAM / 500 GB SSD, with 4 TB to 20 TB of monthly transfer. Prices for that line weren't listed on the product page. For a private cloud build it's the wrong product anyway: a VPS is a virtual machine on a host you don't control, which is precisely what you're trying to move away from.

## Hosted private cloud, VPC, and managed private cloud: where the line actually sits

The three terms get used interchangeably in sales material, and they shouldn't be.

Google Cloud's definitions are the cleanest starting point. A private cloud is a deployment where "all cloud resources are dedicated to a single customer or user organization." A **hosted** private cloud runs that environment off-premises on a vendor's servers, and the distinguishing detail is explicit: "unlike a VPC, you don't have to share with other customers." A VPC, by contrast, "offers private resources and an isolated environment using shared public cloud resources." Your network is private. The physical hosts underneath it are not.

A **managed** private cloud adds a layer of labour transfer on top. The provider deploys, configures, manages and maintains the environment, including the software, network and operations, and may bundle identity management, storage, backup and disaster recovery.

| Model | Hardware yours alone? | Who runs the platform |
| --- | --- | --- |
| VPC | No, shared physical hosts with isolated networking | You, inside the provider's console |
| Hosted private cloud | Yes, dedicated to your organisation | Your team, or the provider if managed |
| Managed private cloud | Yes, typically single-tenant | The provider, end to end |
| Dedicated servers + private network | Yes, the physical machine is yours | Your team |

Here's the part most comparison pages skip. AWS defines an enterprise private cloud as "logically and sometimes physically separated from a cloud service provider's other customers' cloud services." Logically separated is what a VPC already is. Google's definition requires no sharing at all. Two major providers, two different bars for the same phrase, and the gap between them is the difference between a €200-a-month VPC and a €3,190-a-month contract. When a pricing page says "private cloud," ask which definition it's using before you ask for the quote.

## The monthly fee is not the monthly bill

UpCloud's €3,190 buys compute. Storage is billed separately, and the rates are published: **€0.22/GB/month** for MaxIOPS block storage, **€0.085/GB/month** for standard block storage, **€0.056/GB/month** for archive. Put 10 TB of standard block storage next to that node and you've added roughly **€870 a month**. Make it 10 TB of MaxIOPS and you've added roughly **€2,250**, which is about 70% on top of the headline price before you've run a single workload. The page also says "starting at," and the next step is a personalised quote, so the number you're quoted will move with node count and location.

That structure isn't unusual, and it isn't a criticism of one vendor. It's the reason to price your actual configuration rather than comparing entry figures. UpCloud does include one thing many providers charge for: zero egress costs, stated plainly on the product page, across 15 data centres.

Dedicated hardware inverts the problem. Storage sits inside the box, 30 TB of transfer is included on the 10 Gbps plans, billing is month-to-month with no setup fee, and the price on the page is the price you pay. What you give up is elasticity. When a $89 server runs out of room, you don't resize it; you order a second one and put it on the same private network. The free VPC is what makes that practical rather than painful, because you're extending a layer-2 network instead of rebuilding your architecture.

👉 [Check Spin Servers' month-to-month plans and included bandwidth](https://bit.ly/Spinservers)

## Who should not buy hosted private cloud services

Three groups, and it's worth being blunt about them.

**Teams without Linux and network operations capacity.** A €3,190 managed contract looks expensive until you compare it to a hire. If nobody on staff can run a hypervisor, manage a private network and handle patching, the managed premium is buying you a salary you'd otherwise pay. AWS says the quiet part out loud: private cloud environments "are more expensive than using public cloud resources, as your company essentially owns that small portion of a data center." You are paying for control, and control you can't exercise is a waste of money.

**Anyone with spiky or unpredictable load.** Fixed hardware sits idle at 3 a.m. and runs out at month-end. Provisioned capacity is a commitment, and underused capacity is the most common way private cloud budgets go wrong. AWS's own guidance on this is to watch utilisation and use cost management tooling; the simpler answer for a workload that swings 5x week to week is to not own the hardware.

**Teams that need geographic reach next quarter.** A VMware-based private cloud is limited to the data centres where the provider has deployed VMware hardware. An OCI-based offering inherits that platform's footprint, which Oracle reports as more than 50 public cloud regions across 28 countries. Dedicated-server providers are smaller still. If your roadmap includes five new countries, none of this fits.

One correction to a common assumption: a private cloud is not automatically more secure than a public one. Google's framing is accurate — single-tenancy lets you maintain the same level of security, access control and customisation you had on-premises. Whether you actually get there depends on how you configure it, and that configuration is your job unless you're paying someone else to own it.

## Five questions to ask before you sign anything

1. **Physical or logical isolation?** Get it in writing. "Private" covers everything from a dedicated chassis to a VLAN in a shared cluster.
2. **Is storage inside the monthly figure?** With UpCloud it isn't, and 10 TB of the fast tier can add 70% to the bill. With Spin Servers the disks are in the server, so the only variable is how much transfer you burn.
3. **What's the term, and what does renewal cost?** Month-to-month with no setup fee is the flexible end of the market; multi-year commitments trade flexibility for a discount you should calculate over the full term, not the first invoice.
4. **What happens when a host fails?** VMware-based private clouds typically restart VMs on a healthy host in the cluster. OCI-based offerings can live-migrate VMs during maintenance. On bare metal, failover is whatever you built, which means it's worth building before you need it.
5. **Do you get a console?** Some managed private clouds are fully managed by default, with a named support contact instead of a management console your team logs into. VMware-based offerings usually hand you the console. Dedicated servers give you IPMI/iKVM, so you have out-of-band access even if you destroy the operating system.

Question five decides more purchases than the price does. If your team expects to log in and operate the environment, a fully managed black box will frustrate you regardless of what it costs.

## What Spin Servers actually gives you, and what it doesn't

Spin Servers does not sell a managed private cloud product. It sells dedicated bare metal, and the private cloud is something you assemble on top. Being clear about that matters, because the two are priced in different categories for a reason.

What's there: full physical machines with no hypervisor imposed on you, IPMI/iKVM console access, dual 10 Gbps ports as the baseline rather than an add-on, 30-minute provisioning on in-stock inventory, and month-to-month billing with no setup fee. The VPC feature lets you place two or more servers on the same private layer-2 network with 10 Gbps between them, at no extra cost, which is the piece that turns a stack of servers into something you can architect like a cloud. The published material cites Tier III facilities in Dallas and San Jose, SOC 2, HIPAA and PCI compliance, its own ASN with multihomed transit, and carrier-grade firewalls with DDoS protection.

What isn't there: no managed control plane, no live migration, no VMware console, no one to call when your hypervisor needs patching. High-core custom configurations have quoted 3 to 6 business days for delivery rather than 30 minutes. Popular stock sells out, and IPv6 support is limited, so confirm both if either is a hard requirement.

For a team that already runs its own infrastructure, that's a coherent trade: roughly $178 a month for two 256 GB nodes on a private network, against €3,190 a month for a single managed node before storage.

👉 [Compare the full dedicated server lineup before you order](https://bit.ly/Spinservers)

## Which option fits your situation

Work backwards from what you're actually short of.

**You need network isolation and nothing more.** A VPC does this, costs a fraction of any private cloud, and requires no new skills. Don't buy hardware to solve a routing problem.

**You need physical single-tenancy, your load is predictable, and you have someone who can run a hypervisor.** Dedicated servers plus a private network, and Spin Servers is the cheapest credible version of it: $89 a month for a 256 GB node, month-to-month, with the private networking included rather than metered. Two nodes and you have redundancy you control.

**You need single-tenancy but have nobody to operate it.** Pay for managed. €3,190 plus storage at UpCloud, or a fully managed OCI-based environment where the provider handles provisioning and monitoring, is the honest price of not hiring.

**You need low latency inside your own building.** None of the above. Look at on-premises options from the major clouds, such as AWS Outposts or EC2 Dedicated Hosts, which put provider infrastructure and licensing in your facility.

Before you order anything, confirm two figures in writing: the all-in monthly cost including storage and transfer, and the price after any introductory term ends. Those two numbers, not the headline, decide whether the contract still makes sense in year two.

👉 [Confirm current stock and pricing on Spin Servers' order page](https://bit.ly/Spinservers)
