# Finance — Cost, ROI, and the Beverly Hills Comparison

## 1. Purpose

This node provides order-of-magnitude cost estimates for the project, the operating economics of selling compute externally, and a comparison to the alternative: buying a conventional luxury home in a high-cost market. All figures are 2026 estimates. Actual bids will vary by county, site conditions, and finish level.

## 2. The Beverly Hills Comparison

A median home in Beverly Hills costs roughly $2.36 million (January 2026). For that price you get:

- A house in a crowded, expensive, politically strained state.
- Zero compute autonomy. You rent cloud capacity or you do not compute.
- High state income tax, high property tax, and ongoing wildfire insurance risk.
- A backyard, not a mountain range.

The same capital invested in this project buys:

- A home in Montana with zero heating cost (heat is a byproduct of compute).
- Local compute capacity that you own, not rent.
- Revenue from selling surplus compute while you sleep.
- Food from the greenhouse, water from condensate, power from the roof.
- A 2-hour flight from Helena to Miami when you want a beach. The difference is you come back to a building that pays for itself.

The narrative: Beverly Hills is a consumption asset. It consumes capital, consumes taxes, consumes insurance. This project is a productive asset. It produces heat, food, compute, and revenue. The cold climate is not a bug; it is the engine that makes the heat recovery valuable.

## 3. Capital Cost (Order of Magnitude)

### 3.1 Construction

Montana construction costs vary widely by location. Whitefish (resort market) runs $350–$600+/sq ft. Statewide baseline is lower, but the project includes seismic engineering, columns, a service channel, and a greenhouse — none of which are standard.

| Component | Base Case (4 units, ~1200 m2 house + technical + greenhouse) | Notes |
|---|---|---|
| Main house (columns, 4 units, double-frame walls) | $2.5M–$4.5M | $350–$600/sq ft on ~1200 m2, plus seismic and acoustic |
| Technical building | $300K–$600K | Smaller footprint, but dense with equipment |
| Greenhouse (4 zones, glass) | $200K–$500K | Size and glazing choice drive the range |
| Service channel (front + rear) | $100K–$250K | Shallow, insulated, with redundancy |
| Subtotal (structure) | $3.1M–$5.85M | Before compute hardware |

### 3.2 Energy and Water Systems

| Component | Estimate | Notes |
|---|---|---|
| Solar (roof + terrace) | $80K–$200K | Depends on kW and roof complexity |
| Battery (100–200 kWh for 48–72h critical load) | $120K–$240K | At ~$1,221/kWh installed in Montana |
| Generator + propane (two 500-gal tanks) | $15K–$40K | Generator, tanks, setbacks |
| Boiler + buffer tank | $15K–$35K | Gasification boiler, 500–1000 gal buffer |
| Water system (tanks, treatment, pumps) | $15K–$40K | Two tanks, filtration, UV, mineralization |
| EV chargers (8 spaces, load-managed) | $8K–$25K | ~$2,193 per Level 2 install, plus EMS |
| Subtotal (systems) | $253K–$580K | |

### 3.3 Compute Spine (Equipment)

| Component | Estimate | Notes |
|---|---|---|
| Racks, manifolds, quick-disconnects | $20K–$50K | Depends on rack count |
| Compute nodes (CPUs/GPUs) | $100K–$500K+ | Highly variable. Entry: used/consumer. High-end: 8xH100 class. |
| Cooling loop hardware (pumps, heat exchangers, cold plates) | $30K–$80K | |
| Network (fiber, switches, Starlink) | $15K–$40K | Starlink: $156/mo for 1TB |
| Subtotal (compute) | $165K–$670K+ | The high end is real — but it buys revenue capacity |

### 3.4 Total Capital Cost (Base Case)

Low estimate: ~$3.5M (structure on the lower end, modest compute, 2 units instead of 4).

High estimate: ~$7.1M (Whitefish-level finishes, 4 units, high-end compute, full redundancy).

Per unit (4 units): $875K–$1.78M per owner. For a Beverly Hills median home, you get one house. Here you get a unit, a share of the compute, a share of the greenhouse, and a revenue stream.

The cosmic caveat: if compute hardware alone reaches $500K–$1M, the project total can exceed $8M. At that point the comparison changes: you are not buying a home, you are buying a micro data center with living quarters. The ROI case must be evaluated on compute revenue, not on real estate appreciation.

## 4. Operating Economics

### 4.1 Operating Costs

| Item | Monthly Estimate | Notes |
|---|---|---|
| Electricity (compute + building, net of solar) | $500–$2,000 | Varies with compute load and local rate |
| Starlink Business (1TB) | $156 | Plus secondary channel |
| Propane (backup, winter only) | $100–$300 | Depends on boiler use |
| Maintenance (hardware, filters, service) | $300–$800 | Includes compute hardware reserve |
| Total monthly | ~$1,050–$3,250 | Before compute revenue |

Key point: heating is near-zero. In a conventional Montana home, winter heating alone can run $300–$600/month. Here, it is a byproduct.

### 4.2 Revenue from Compute Sales

Compute revenue is not guaranteed. It depends on hardware, utilization, and market rates. But the model is:

- Residents use their base quota first (governance document).
- Surplus is sold to external clients at market rate (or below, to attract demand).
- Revenue covers electricity, maintenance, and a hardware replacement reserve, then distributes to units.

Scenario (moderate): a $200K compute investment (e.g., 4–8 high-end GPUs) running at 60% external utilization can generate $2K–$6K/month gross, depending on market rates. This is not a guarantee. It is the reason the project is a productive asset, not a consumption asset.

Scenario (conservative): zero external revenue. The project still saves $300–$600/month on heating, produces some food, and provides compute autonomy for residents. The ROI is then measured in resilience, not cash.

## 5. Variants and Cost Sensitivity

| Variant | Change | Cost Impact | ROI Impact |
|---|---|---|---|
| 1 unit instead of 4 | No double-frame walls, single owner, simpler systems | -30–40% on structure | No external sale (unless owner chooses) |
| 2 units | Partial separation, shared systems | -15–20% | Modest external sale possible |
| Grid-connected (no battery) | Remove 100–200 kWh battery | -$120K–$240K | Loss of autonomy during outages |
| InfiniBand fabric | Higher switch cost | +$15K–$40K | Higher training performance, better external sale rate |
| Ethernet fabric | Lower switch cost | -$10K–$20K vs InfiniBand | Lower peak training, adequate for inference |
| No greenhouse | Remove glass structure, zones | -$200K–$500K | Less food, less heat sink in summer |
| Pre-owned compute | Used/consumer GPUs | -50–70% on compute | Lower performance, higher failure rate |

## 6. Flexibility Clause

Every number in this document is an estimate, not a quote. The following principles must be preserved:

- The project must be evaluated as a productive asset, not a consumption asset.
- Heating cost must remain near-zero in normal operation (compute heat reuse).
- Compute revenue must never come at the expense of resident base quota.
- If the total cost exceeds $8M, the project must be justified on compute revenue, not on real estate.

## 7. Open Items

- Obtain local contractor bids for the specific county (Whitefish vs. Bozeman vs. rural).
- Confirm compute hardware selection and market rate for external sale.
- Confirm battery capacity requirement based on actual critical load list.
- Confirm whether the technical building will be classified as commercial (affects permits and taxes).

## 8. Related Documents

- [Concept Overview](../concept/00-overview.md)
- [Governance](../concept/01-governance.md)
- [Node 01 — Site & Foundation](../nodes/01-site-foundation.md)
- [Node 07 — Energy](../nodes/07-energy.md)
- [Node 09 — Network](../nodes/09-network-connectivity.md)
- [Node 10 — Legal & Permitting](../legal/01-zoning-permits.md)
