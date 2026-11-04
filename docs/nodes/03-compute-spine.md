# Node 03 — Compute Spine

## 1. Purpose

The compute spine is a modular, liquid-cooled cluster of CPUs/GPUs mounted along the **blind north wall** of the main building. It provides local compute for residents and sellable compute to external clients. Its waste heat is the primary heat source for the building and greenhouse.

The spine is not a data center room. It is a **linear service corridor** integrated into the building envelope. It must be serviceable, isolated from living space, and protected from moisture, fire, and unauthorized access.

## 2. Geometry

- **Location:** along the north wall, full length of the building.
- **Width:** 1.2–1.5 m clear access corridor in front of the racks.
- **Height:** full storey height (2.7–3.0 m) to allow vertical airflow and service access.
- **Wall:** the north wall is solid, insulated, no windows. The spine corridor is on the inside face of this wall.
- **Separation from living space:** a fire-rated, acoustically insulated partition between the spine and the nearest apartment. Minimum 1-hour fire rating. Acoustic target: ≤35 dB(A) in the adjacent living room at full load.

**Variant A:** if the building is a single-family home, the spine may be a dedicated room rather than a full-length corridor. Cost change: -20–30% on partition and access, but limits future expansion.

## 3. Rack and Module Design

### 3.1 Base Case: Open Frame Rack with Flexible Liquid Loops

- Standard 19-inch or 21-inch open frame racks, floor-mounted, anchored to the slab.
- Each compute module (CPU/GPU node) has its own **liquid cooling cold plate** or **radiator block**.
- Flexible tubing (EPDM or silicone, rated for the coolant temperature) connects each module to the rack manifold.
- Quick-disconnect couplings at each module: **hot-swap without draining the loop**.
- Rack manifold connects to the building's main cooling loop (Node 04).

**Key requirement:** each module's liquid loop is **independent** at the quick-disconnect. One module can be removed while the rest of the spine continues operating. This is the "swappable" principle.

**Variant B:** immersion cooling (single-phase or two-phase). Higher heat density per rack, but requires sealed tanks, compatible dielectric fluid, and a different maintenance procedure. Cost change: +30–50% capital, -20% pump energy. Only justified if rack density exceeds air/liquid cold-plate limits.

**Variant C:** direct-to-chip liquid cooling with a shared manifold per rack (no individual quick-disconnects). Lower cost, but module swap requires shutting down the rack. Not recommended for the project's "swap without stopping" requirement.

### 3.2 Coolant

- Base case: water-glycol mix (30–50% glycol) for freeze protection during shutdowns.
- Alternative: dielectric fluid if immersion is used.
- Filtration: 50-micron inline filter on the return line to each rack. Replaceable without shutting down the loop.

## 4. Heat Capture and Delivery

- Each module's cold plate absorbs heat from the processor.
- Coolant exits the module at 45–65°C (depending on load and coolant flow).
- Rack manifold collects all module returns into a single supply to the building heat exchanger (Node 04).
- The heat exchanger transfers heat to the building heating loop (underfloor, radiators, hot water) and to the greenhouse loop.

**Temperature control:** the spine controller modulates coolant flow per rack to maintain processor temperatures within vendor limits. Excess heat beyond building demand is routed to the greenhouse or to ground storage (Node 05).

## 5. Ventilation and Humidity Control

Even with liquid cooling, the spine corridor needs ventilation. Reasons:
- **Moisture:** condensate forms on cold surfaces (cold plates, tubing, manifolds). Without air movement, humidity rises and condensation spreads to electronics.
- **Heat leakage:** some heat is radiated from tubing and manifolds into the corridor air. Without ventilation, the corridor overheats.
- **Air quality:** dust and lint accumulate. A sealed corridor with no air exchange becomes a dust trap.

**Base case ventilation:**
- **Supply:** filtered outdoor air, pre-conditioned (heated in winter, cooled/dehumidified in summer) via an ERV (energy recovery ventilator).
- **Exhaust:** from the high point of the corridor, to the outside.
- **Air change rate:** minimum 2 air changes per hour (ACH) during normal operation. Increase to 4 ACH if humidity sensors detect rising moisture.
- **Dehumidification:** if outdoor air is humid, the ERV's latent recovery or a small inline dehumidifier keeps corridor humidity below 60% RH.
- **Condensate from ventilation:** the ERV and dehumidifier drain to the same condensate sump as the channel (Node 02).

**Variant D:** no mechanical ventilation, rely on passive vents and the building's general exhaust. Cost change: -$2,000–$5,000, but high risk of condensation and dust. Not recommended.

**Variant E:** dedicated dehumidifier only, no ERV. Cheaper than ERV, but no heat recovery and no fresh air. Suitable only if the corridor is sealed and the building already has separate fresh-air supply.

## 6. Fire Safety

- **Detection:** smoke and heat detectors inside the spine, connected to the building alarm.
- **Suppression:** clean-agent suppression (e.g., FM-200 or Novec) for the spine volume. Water sprinklers are not appropriate for energized electronics.
- **Compartmentation:** 1-hour fire-rated partition between spine and living space. Fire-rated doors at all spine entrances.
- **Cable management:** metal conduit or metal raceway for all power cables. No exposed plastic cable trays in the spine.

**Variant F:** if clean-agent suppression is too expensive for a residential-scale project, use **pre-action dry pipe sprinkler** with early smoke detection. Lower cost, but water damage risk if activated. Acceptable only if the spine is in a separate building (technical building) rather than inside the house.

## 7. Access and Security

- **Access:** biometric or keycard entry from the service corridor, not from living space. Residents and service technicians have access; guests do not.
- **Monitoring:** camera at the spine entrance, logging access events.
- **Physical security:** racks locked to the floor; modules locked in racks. Quick-disconnect couplings are inside the locked rack enclosure.

## 8. Sensors and Monitoring

Minimum sensor set:
- **Per rack:** inlet and outlet coolant temperature, coolant flow, differential pressure.
- **Per module (where supported):** processor temperature, power draw, fan speed (if air-cooled components exist).
- **Corridor:** air temperature, relative humidity, dew point.
- **Leak detection:** tape or cable under each rack and at each manifold connection.
- **Power:** per-rack power monitoring, plus main spine feed monitoring.

Data feeds into the spine controller and the building controller. Alerts: coolant leak, temperature out of range, humidity above 60% RH, module offline, power anomaly.

**Variant G:** minimal sensors (corridor temperature and humidity only). Cost change: -$1,000–$2,000, but no early warning of module-level failures. Not recommended for a revenue-generating compute cluster.

## 9. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Rack density exceeds cold-plate capacity | Switch to immersion cooling (Variant B) | +30–50% capital |
| Corridor humidity persistently above 60% RH | Add dedicated dehumidifier or increase ERV capacity | +$1,500–$3,000 |
| Clean-agent suppression not permitted by local code | Switch to pre-action sprinkler + early detection | -20–30% suppression cost |
| Building is single-family, not multi-unit | Spine becomes a dedicated room, not full-length corridor | -20–30% |
| Compute load will be sold externally at scale | Add second spine in technical building, separate from house | +40–60% on spine cost, but isolates residential from commercial risk |

## 10. Open Items

1. Confirm coolant compatibility with selected CPU/GPU cold plates (vendor specification).
2. Confirm ERV capacity and duct routing with the HVAC engineer.
3. Confirm local code acceptance of clean-agent suppression in a residential building.
4. Confirm rack power density and cooling capacity against the selected compute hardware.
5. Confirm that the spine corridor's structural floor loading is within the building's design (racks are heavy; the structural engineer must confirm).

## 11. What This Node Does Not Cover

- Main cooling loop sizing and pump selection (Node 04).
- Heat exchanger design (Node 04).
- Greenhouse heat distribution (Node 05).
- Electrical distribution to racks (licensed electrician, Node 07).
- Structural design of the spine floor and partitions (Node 08).
