# Node 09 — Network & Connectivity

## 1. Purpose

This node defines the external internet connectivity and the internal network fabric for the building. It covers the two independent external channels, the optical backbone from the technical building to the compute spine and to each unit, the Wi-Fi policy, and the fabric-agnostic cabling strategy that allows either InfiniBand or Ethernet to be selected at equipment purchase time.

The network is not an afterthought. For a building whose residents sell compute externally and work with large datasets, the network is a revenue-critical system.

## 2. External Internet: Two Independent Channels

**Base case: Starlink Business Priority (Local Priority) as primary, plus a second independent channel.**

- **Primary: Starlink Business Priority.** Priority plans include prioritized network access, a public IP address, a telemetry dashboard, and priority support. Local Priority is intended for inland use within one country. Data blocks are purchased in 50GB or 500GB increments [citation:4][citation:8].
- **Sizing:** 1TB/month is the minimum for 5–10 users with average bandwidth needs. For a building with 4 units and external compute sales, 2TB/month or more is realistic. Pricing starts at $250/month for 1TB (varies by region and plan) .
- **Secondary channel: independent of Starlink.** Options: a second Starlink terminal on a separate account (if the first fails due to obstruction or regional outage), a cellular modem with a directional antenna (if coverage exists), or a local WISP (if available). The secondary channel does not need to match primary speed, only to keep critical services (monitoring, control, minimal data transfer) online during primary failure.
- **Failover:** automatic at the router level. No manual intervention required for normal failover. Manual override available for testing and for extended primary outages.

**Base requirement:** two physically independent channels. A single Starlink terminal, no matter how reliable, is a single point of failure for a revenue-generating system.

**Variant A:** if a second Starlink terminal is too expensive, use a cellular modem as secondary. Cost change: -$100–$200/month, but lower reliability and potentially data caps.

## 3. Internal Backbone: Fiber to Every Unit

- **Single-mode fiber** from the technical building to the compute spine, and from the technical building to each unit. Fiber runs in the service channel (Node 02).
- **Minimum 10G per unit**, with conduit and fiber sized for 100G future upgrade. The cost difference between 10G and 100G-capable fiber is marginal at installation time; the difference at retrofit time is large.
- **No shared Wi-Fi for workstations.** Each unit has a dedicated fiber port. Wi-Fi is for guests and mobile devices only.
- **Redundancy:** two fiber paths from the technical building to the compute spine (one front channel, one rear channel, per Node 02). If one path is damaged, the other continues.

**Base requirement:** every unit has a wired fiber connection. Wi-Fi-only units are not acceptable for the target occupants (AI developers, content creators, artists working with large files).

## 4. Compute Fabric: InfiniBand vs Ethernet

The fabric connects the compute nodes inside the spine. The choice between InfiniBand and Ethernet affects performance, cost, and vendor lock-in. The building design must not lock the owner into either.

**InfiniBand NDR (NVIDIA Quantum-2)**
- Empirical study at 16,384 GPUs: InfiniBand sustained **52.8% MFU** on Llama-3-405B pretraining, versus 34.2% for RoCEv2 under the same conditions. AllReduce was **2.41x faster** [citation:5].
- Hardware cost is roughly **3x Ethernet switch cost**. Single-vendor ecosystem (NVIDIA/Mellanox) [citation:11].
- Best for dedicated large-scale training where raw performance and predictability matter more than cost.

**Ethernet (RoCEv2 / Spectrum-X)**
- Lower baseline cost, multi-vendor ecosystem, reuses existing Ethernet operations expertise [citation:11].
- Performance gap is workload-dependent. For inference-heavy or mixed workloads, the gap narrows. For dense pretraining, it widens.
- Requires careful tuning (PFC, ECN, DCQCN) to approach InfiniBand performance. Untuned RoCEv2 can collapse below 20 GB/s [citation:15].

**Base case: fabric-agnostic cabling.**
- The building installs **optical fiber and conduit** sized for either 400G or 800G, compatible with both InfiniBand and Ethernet transceivers.
- The fabric selection (InfiniBand vs Ethernet) is made **at equipment purchase time**, based on the actual workload mix of the residents and the external clients.
- This protects against vendor lock-in and against choosing the wrong fabric before the workload is known.

**Base requirement:** the cabling infrastructure must not predetermine the fabric choice. Conduit, fiber type, and patch panel layout must be compatible with both.

**Variant B:** if the first owner knows they will run dense pretraining at scale, install InfiniBand fabric from the start. Cost change: +$15,000–$40,000 for switches and adapters, but no retrofit later.

**Variant C:** if the first owner is an inference-focused or mixed-workload user, install RoCEv2/Spectrum-X Ethernet. Cost change: -30–40% versus InfiniBand, with acceptable performance for the workload.

## 5. Redundancy and Monitoring

- **Two core switches** in the technical building, in a redundant pair. No single switch failure takes down the building.
- **Two fiber paths** from technical building to compute spine (front and rear channel).
- **Monitoring:** per-link utilization, error counters, latency. Alerts on link down, high error rate, or latency spike.
- **Analog fallback:** none required for the network itself (a network is inherently electronic). But the kill switch (Node 07) allows physical disconnection of the compute spine from the network if needed for security.

## 6. Wi-Fi Policy

- **Guest Wi-Fi:** separate SSID, separate VLAN, bandwidth-limited. No access to the compute spine or to resident networks.
- **Resident mobile devices:** can use Wi-Fi for phones and tablets. Workstations use wired fiber.
- **No Wi-Fi in the compute spine.** All compute nodes are wired.

## 7. Flexibility Clause

Every parameter in this document can be changed to reduce cost or to meet the client specific needs. However, the following must be preserved:

- Two independent external channels.
- Fiber to every unit.
- Fiber and conduit compatible with both InfiniBand and Ethernet.
- Two fiber paths from technical building to compute spine.
- No Wi-Fi in the compute spine.

## 8. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Cellular coverage is good | Use cellular modem as secondary instead of second Starlink | -$100–$200/month |
| Owner knows they will run dense pretraining | Install InfiniBand fabric from start | +$15,000–$40,000 |
| Owner is inference-focused | Install RoCEv2/Spectrum-X Ethernet | -30–40% vs InfiniBand |
| Budget for two fiber paths is tight | Single path to spine, but keep conduit for second | -20–30% on fiber install |
| Starlink obstruction at site | Move terminal, or rely on secondary channel as primary | No cost change, but primary speed may drop |

## 9. Open Items

- Confirm Starlink Business Priority availability and pricing for the specific Montana address.
- Confirm secondary channel options (cellular coverage, local WISP, second Starlink).
- Confirm fabric choice with the first owner before equipment purchase.
- Confirm conduit and fiber routing in the service channel with Node 02.

## 10. What This Node Does Not Cover

- Compute spine power and cooling (Node 03).
- Service channel construction (Node 02).
- Electrical distribution for network equipment (Node 07).
- Governance of network access and external sales (01-governance.md).
