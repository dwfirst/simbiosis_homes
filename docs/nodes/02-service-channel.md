# Node 02 — Service Channel & Condensate

## 1. Purpose

The service channel connects the main house, technical building, and greenhouse. It carries:
- Liquid cooling loop (supply and return)
- Heating loop (hot water from heat exchangers)
- Electrical power (main and backup)
- Data/communication (fiber, main and backup)
- Condensate drainage

The channel is **shallow and above-ground-accessible**, not a deep tunnel. It is covered by removable decking that serves as a pedestrian path. Vehicle crossings are handled by portals or short buried sections.

## 2. Why Shallow, Not Deep

A deep tunnel in Montana's frost conditions and seismic zone D is expensive and risky. Shallow burial with insulation and heat from the compute loop is cheaper and more controllable.

**Cost reference:** utility trenching in Montana runs $20–$70 per linear foot depending on depth and soil. Shallow shared trenches in workable soil: $20–$35/ft. Deep frost-depth lines or rocky conditions: $50–$70/ft [citation:7].

**Decision:** target 18–24 inches of cover with XPS insulation, not 48–60 inches (typical frost depth in western Montana). The compute loop keeps the channel above freezing; the insulation keeps the heat in.

## 3. Channel Construction

### 3.1 Base Case: Precast Polymer Concrete Trough

- Rectangular section, factory-cast with longitudinal slope (minimum 0.5%).
- Material: polymer concrete or FRP, rated for low-temperature exposure (verify with supplier for -30°C).
- Wall thickness: pedestrian-load rating for standard sections; vehicular-load rating under crossings.
- Joints: elastic waterproofing tape (Sika Combiflex or equivalent), not rigid cement. Tape must bridge both sides of the joint by at least 50mm.
- At building entries: flexible waterproof sleeves + elastic sealant. No rigid concrete encapsulation.

**Cost placeholder:** precast trough materials and installation, $40–$80 per linear foot (estimate, confirm with local supplier).

### 3.2 Variant A: Cast-in-Place Concrete + XPS

If precast is unavailable or too expensive in the target county:
- Cast-in-place concrete base and side walls, with elastic joint tape at all cold joints.
- External XPS insulation, 50–75mm, wrapped continuously.
- Cost change: -15–25% material cost, but longer construction time (curing) and weather-dependent.

### 3.3 Variant B: Shallow Trench + Rigid Insulation Box (No Concrete)

If soil is workable and loads are light:
- Excavate shallow trench, line with XPS boards forming a box, place pipes inside, cover with removable lid.
- No structural concrete. Fastest and cheapest.
- Only suitable where no vehicle loads and groundwater is below trench bottom.
- Cost change: -30–40% vs. precast trough, but less durable and harder to seal at joints.

## 4. Frost Protection

### 4.1 Passive: XPS Insulation

- External XPS, 50–75mm, continuous around the trough.
- Joints between XPS boards taped or foamed. No gaps.
- Protective layer over XPS (membrane or gravel) to prevent UV degradation and rodent damage.
- At building entries: insulation must be continuous through the flexible joint zone. This is the most vulnerable point.

**Reference:** shallow-buried utilities protected by closed-cell XPS are a recognized approach in cold climates; 75mm panels with 1.2m of cover above are cited in engineering practice [citation:8].

### 4.2 Active: Waste Heat from Compute Loop

The liquid cooling loop carries heat from processors. This heat is the primary frost protection for the channel. The channel does not need independent heating during normal operation.

**Failure mode:** if the compute loop shuts down (maintenance, power failure), the channel temperature drops. During winter, this requires either:
- Electric heat trace (self-regulating cable) along the water lines, activated only during shutdowns, or
- Drain-down procedure: if the loop will be offline for extended periods, drain the lines and blow out with air.

**Variant C:** electric heat trace installed on all water lines in the channel. Cost: $8–$15/ft material, negligible operating cost (only active during shutdowns).

## 5. Condensate Drainage

Condensate forms on cold surfaces inside the channel (pipes, trough walls). It must be collected, not allowed to pool.

- **Slope:** trough bottom slopes to a low point at minimum 0.5%.
- **Collection:** 500×500×500mm precast sump at the low point.
- **Pump:** small submersible pump with float switch, rated for low temperature or installed in a frost-protected sump extension. Discharge to the water storage tanks (Node 06).
- **Backup:** manual drain valve in case of pump failure.
- **Overflow:** if sump fills, overflow routes to a gravel French drain outside the channel footprint.

**Variant D:** if condensate volume is minimal (dry winter), omit the pump. Manual drain at scheduled intervals. Cost change: -$200–$500, but adds maintenance labor.

## 6. Duplication: Two Routes

Two independent channel routes: **front (south/facade)** and **rear (north/back)**.

- Front route: primary cooling loop, primary power, primary fiber. Finished as a colonnade or gallery.
- Rear route: backup cooling loop, backup power, backup fiber. Finished as a pergola or stone parapet.
- Cross-connections at the technical building and at the main house: switchover valves and automatic transfer for power.

**Failure scenario:** if the front route is damaged (vehicle impact, excavation accident), the rear route continues service. Repair can proceed without shutting down the building.

**Variant E:** if budget does not allow full duplication initially, build the rear route as empty conduit with pull-lines. Cost change: -60% of rear route cost now, but ready for cable/fiber installation later. Cooling loop duplication cannot be deferred (fluid loop requires physical pipes).

## 7. Crossings: Pedestrian and Vehicle

### 7.1 Pedestrian

- Removable decking over the channel serves as the pedestrian path.
- Decking: treated wood or composite, ventilation gaps, individual panels removable by one person (≤25 kg).
- Where the channel meets a path at a different level: wooden steps or a small bridge, matching the colonial/terrace aesthetic.

### 7.2 Vehicle

Two options:

**Option A: Portal.** The channel continues at grade, but a structural portal (two columns + crossbeam) spans it. Clearance: minimum 2.8m. Columns match the architectural language of the house.

**Option B: Short Buried Section.** The channel dips below grade for the width of the driveway, with flexible joints at both transitions. This is more expensive but preserves a flat driveway surface.

**Decision:** use portals for all vehicle crossings unless the driveway geometry makes a portal impossible. Portals are cheaper, maintainable, and visually consistent with the colonial design.

## 8. Sensors and Monitoring

Minimum sensor set:
- **Temperature/humidity** at the low point and high point of each route. Alert if temperature approaches 2°C.
- **Sump level switch.** Alert if pump fails or level rises.
- **Leak detection tape** at critical joints (building entries, sump connections).
- **Power monitoring** on both routes. Alert if backup route loses power.

Data feeds into the building controller. If channel temperature drops below threshold, the controller either increases compute load (if available) or activates heat trace (if installed).

**Variant F:** no sensors, manual inspection. Cost change: -$500–$1,000, but no early warning of freeze or leak. Not recommended for a building that must operate unattended.

## 9. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Geotech shows rock at shallow depth | Raise channel above grade on low piers; XPS box around exposed section | Excavation cost drops; insulation cost rises |
| Groundwater above trench bottom | Add membrane liner + gravel surround; raise trough if needed | +10–15% |
| Precast trough unavailable or lead time >8 weeks | Switch to Variant A (cast-in-place) | -15–25% material; +2–3 weeks schedule |
| Compute loop will be offline for weeks at a time | Add Variant C (heat trace) as standard, not option | +$8–$15/ft |
| County requires all utilities underground with no exposed channel | Full burial at frost depth; abandon shallow concept | +40–60% |

## 10. Open Items

1. Confirm local supplier for polymer concrete trough or FRP trough rated for -30°C.
2. Confirm XPS availability and thickness required by local frost depth (varies by county: 36–60 inches in Montana).
3. Confirm whether the county treats the channel as a "utility" (requiring underground placement) or as a "landscape feature" (allowing exposed construction). This determines whether Variant B or full burial is required.
4. Confirm vehicle crossing locations and clearances with the site plan.

## 11. What This Node Does Not Cover

- Sizing of the cooling loop pipes (Node 03).
- Pump selection for condensate (Node 06, water system).
- Structural design of portals (Node 08, structure).
- Electrical code compliance for the power route (licensed electrician required).
