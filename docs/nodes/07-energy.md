# Node 07 — Energy

## 1. Purpose

The energy system powers the building, the compute spine, the greenhouse, the water system, and all controls. It is designed for **grid independence as the default**, with grid connection as backup, not primary.

Primary generation: rooftop solar on the house and technical building. Secondary: battery storage. Backup: grid connection (if available) and a generator.

## 2. Generation: Solar

### 2.1 House Roof — 4-Slope Roof with Panels

- The house has a **four-slope (hip) roof**. Panels are mounted on all four slopes, not just south.
- East and west slopes capture morning and afternoon sun; north slope captures diffuse light (lower yield, but not zero in Montana's clear-sky conditions).
- **Ridge and perimeter mounting:** panels are mounted on rails above the roofing, with watertight penetrations. No direct adhesive to shingles.

**Base requirement:** roof penetrations must be flashed and sealed to the roofing manufacturer's specification. A leaking roof is a failed energy system.

### 2.2 Terrace Perimeter — Panels on the Terrace Roof

- The terrace around the house has its own roof (or pergola structure). Panels are mounted on this structure, forming a **continuous band around the house**.
- This increases total panel area without increasing the house footprint.
- The terrace panels also provide shade for the terrace below, which is useful in summer.

**Variant A:** if terrace panels are too complex or expensive, mount panels only on the main house roof and the technical building roof. Cost change: -20–30% on panel cost, but lower total generation.

### 2.3 Technical Building Roof — 4-Slope Roof with Panels

- Same approach as the house: panels on all four slopes.
- The technical building roof is smaller, but it is dedicated to energy and mechanical equipment, so panel mounting is simpler.

### 2.4 Greenhouse Roof — No Panels

- The greenhouse roof is **transparent and free of panels**. It must transmit light to the plants.
- Greenhouse energy needs (fans, vents, controls) are supplied from the house/technical building system via the service channel.

**Base requirement:** no opaque panels on the greenhouse roof. Light transmission is the greenhouse's primary function.

### 2.5 Panel Access and Cleaning

Montana snow and dust reduce panel output. Access for cleaning and snow removal is mandatory.

**Option 1: Manual Access (Base Case)**
- Fixed roof ladders or step bolts on the house and technical building, rated for safe access.
- Terrace panels accessed from the terrace itself (walkable surface).
- Cleaning: soft brush and water, manual. Snow removal: soft roof rake.
- **Cost:** low. **Labor:** seasonal, resident or maintenance staff.

**Option 2: Semi-Automated Cleaning**
- Fixed spray nozzles on the panel rails, fed from the water system (Node 06). Activated manually or on a schedule.
- Snow removal still manual.
- **Cost:** +$2,000–$5,000 for plumbing and nozzles. **Labor:** reduced for dust, unchanged for snow.

**Option 3: Fully Automated**
- Robotic cleaners on rails, or tilting panel mounts that shed snow.
- **Cost:** +$10,000–$30,000. **Labor:** minimal.
- **Not recommended for base case:** the cost is not justified for a residential-scale system in Montana, where snow is seasonal and manual removal is effective.

**Base requirement:** there must be a safe physical way to reach every panel for cleaning and snow removal. Panels that cannot be accessed will not be maintained, and unmaintained panels lose output.

## 3. Battery Storage

### 3.1 Chemistry

- **Base case:** lithium iron phosphate (LiFePO4). Safer than lithium-ion, longer cycle life, stable at low temperatures (with heating).
- **Variant B:** flooded lead-acid. Cheaper upfront, but shorter life, more maintenance, and requires vented space. Only if budget is severely constrained.

### 3.2 Capacity

- Sized to carry critical loads (controls, pumps, ventilation, refrigeration, minimum lighting) for **48–72 hours** without solar input.
- Compute spine is **not** on battery backup by default. If the grid fails and solar is insufficient, the compute spine shuts down gracefully (kill switch or controlled shutdown), and the battery carries the building.
- **Variant C:** partial compute backup (e.g., one rack) for critical local services. Cost change: +$5,000–$15,000 depending on rack power.

### 3.3 Location

- Battery room in the technical building, insulated and ventilated.
- LiFePO4 does not require active cooling in Montana's climate, but the room must stay above freezing. Waste heat from the technical building or a small heater maintains temperature.

## 4. Backup Generator

### 4.1 Fuel

- **Base case:** propane. Widely available in Montana, stores indefinitely, no degradation like gasoline or diesel.
- **Variant D:** diesel. Cheaper fuel per kWh, but requires fuel polishing and has cold-weather gelling issues.

### 4.2 Sizing

- Sized to carry critical loads plus battery charging. Not sized to carry the full compute spine.
- **Base requirement:** the generator must be able to charge the battery bank and run critical loads simultaneously.

### 4.3 Start and Control

- **Automatic start** on battery low or grid failure (if grid-connected).
- **Manual start** as backup to automatic. Physical key start, independent of the controller.
- **Kill switch:** physical disconnect between generator and building distribution. Accessible from outside the generator enclosure.

## 5. Distribution

### 5.1 Main Distribution Panel

- In the technical building. Fed by solar inverters, battery inverter, generator, and grid (if connected).
- **Manual transfer switch** between sources. Automatic transfer is optional, but the manual switch is mandatory as a fallback.

### 5.2 Sub-Panels

- House main panel: fed from technical building via the service channel.
- Compute spine panel: separate feed, with its own kill switch (Node 03).
- Greenhouse panel: fed from house or technical building, with zone controls.
- Water system panel: pumps, UV, controls.

**Base requirement:** every major load group must have its own disconnect. A single fault must not take down the entire system.

### 5.3 Kill Switch

- **Compute spine kill switch:** in the server room and in the technical building. Physical, key-operated or covered. Cuts power to all compute racks.
- **Main building kill switch:** in the technical building. Cuts all power except emergency lighting and fire alarm.
- **Manual transfer switch:** allows the operator to switch between solar, battery, generator, and grid without tools.

**Base requirement:** every kill switch must be physically accessible and protected from accidental activation. NIST PE-10 intent: emergency power-off must be reachable and secure.

## 6. Analog and Mechanical Layer

- **Voltage and current meters:** analog panel meters on the main distribution panel. Readable without power.
- **Generator gauges:** oil pressure, coolant temperature, fuel level — analog, on the generator itself.
- **Battery monitoring:** at minimum, a mechanical hydrometer for flooded lead-acid (if used); for LiFePO4, a local display on the battery management system, plus a redundant voltage meter on the main panel.
- **Manual disconnects:** every source (solar, battery, generator, grid) has a physical disconnect switch, labeled and accessible.

**Base requirement:** a person with a flashlight and a key must be able to determine the state of every power source and disconnect it manually.

## 7. Sensors and Monitoring

- **Solar:** per-string voltage and current; inverter status.
- **Battery:** state of charge, voltage, temperature, cell balance (from BMS).
- **Generator:** run status, fuel level, oil pressure, coolant temperature.
- **Distribution:** per-sub-panel power, per-critical-load status.
- **Alerts:** battery low, generator fault, inverter fault, kill switch activated.

Data feeds into the primary controller (Node 04). Secondary controller mirrors it. Analog meters provide the fallback.

## 8. Flexibility Clause

Every parameter in this document can be changed to reduce cost or to meet the client's specific needs. However, the following must be preserved for the system to remain functional:

- Every panel must have a safe physical access route for cleaning and snow removal.
- The greenhouse roof must remain transparent (no panels).
- Battery must carry critical loads for at least 48 hours.
- Generator must be able to charge the battery and run critical loads simultaneously.
- Every major load group must have its own disconnect.
- Every source must have a manual disconnect, accessible without tools.
- Kill switches must be physical and protected from accidental activation.
- Analog meters must remain, even if electronic monitoring is reduced.

Any deviation from the base case must be reviewed against these requirements. If a cheaper option compromises a base requirement, it is not a valid substitution — it is a different system with different performance.

## 9. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Grid connection is available and reliable | Reduce battery capacity; keep generator as backup | -20–30% on battery |
| Grid is not available | Increase battery and solar; generator becomes primary backup | +30–50% on battery and solar |
| Terrace panels are too complex | Panels only on house and technical building roofs (Variant A) | -20–30% on panel cost |
| Snow removal is a major burden | Add semi-automated cleaning (Option 2) | +$2,000–$5,000 |
| Compute spine must stay online during outages | Add partial compute backup (Variant C) | +$5,000–$15,000 |

## 10. Open Items

1. Confirm solar irradiance and snow load for the target county.
2. Confirm battery capacity based on actual critical load list.
3. Confirm generator fuel type and availability (propane vs. diesel).
4. Confirm roof structure can carry panel weight and wind load.
5. Confirm terrace panel mounting details with the structural engineer.

## 11. What This Node Does Not Cover

- Compute spine power distribution (Node 03).
- Heating and cooling loads (Node 04).
- Water system pumps and UV power (Node 06).
- Structural design of roof and terrace for panel loads (Node 08).
- Electrical code compliance (licensed electrician required).

## 12. Technical Building Zoning & Fuel Storage

### 12.1 Functional Zones Inside the Technical Building
The technical building is divided into three functional zones, separated by 1-hour fire-rated partitions:
**Zone A - Wet Zone:** pumps, circulators, heat exchangers, expansion tanks, buffer tank. Floor drain and leak detection. No ignition sources. No fuel storage.
**Zone B - Energy Zone:** diesel generator, battery bank (LiFePO4), inverters, main distribution panel. Separated from Zone A by 1-hour fire partition. Ventilated to the outside. Physical kill switch at the entrance.
**Zone C - Controls Zone:** primary controller, network switches, terminal blocks. Inside Zone B, in a separate locked cabinet. Secondary controller is in the main building server room.
**Base requirement:** fuel storage must never be in the same compartment as the boiler or the battery bank without a fire separation.

### 12.2 Propane Tank Placement
Propane is the backup fuel for the generator. It is never stored inside the technical building. It is an outdoor, above-ground or buried tank.
**Case 1: Site is NOT in a designated WUI (Wildland-Urban Interface).** Above-ground tank permitted. Tank size 125-500 gallons: minimum 10 feet from any building, property line, and ignition source. Tank size 501-2,000 gallons: minimum 25 feet from the same.
**Base case for the project:** two 500-gallon tanks manifolded together. Each tank keeps the 10-foot setback. This provides redundancy and avoids the 25-foot setback required for a single larger tank.
**Case 2: Site IS in a designated WUI.** Montana WUI rules require propane tanks to be buried underground, or partially covered with at least 1 foot of earth, sand, or noncombustible material. If soil or bedrock prevents burial, install in a vault or use another protective method that complies with NFPA 30 and NFPA 58.
**Base requirement:** the propane tank location must allow year-round delivery access. In Montana, a tank behind a snowbank or on a steep slope cannot be filled in February. The access path must be plowed and maintained.

### 12.3 Diesel Generator Fuel Tank
**Base case:** diesel tank is a sub-base tank under the generator, or a double-wall tank inside the technical building Energy Zone.
**Sub-base tank:** generator sits on top of a UL-listed tank.
**Indoor tank (double-wall):** permitted inside the Energy Zone if it is UL 2085 listed or has secondary containment. Capacity limit for indoor storage: confirm with local fire code.
**Vent and fill:** fill connection and vent must terminate outside the building, at least 5 feet from building openings and property lines.
**Spill containment:** required for any indoor tank.
**Base requirement:** diesel fuel degrades over time. The tank must have a drain valve at the low point and a schedule for fuel polishing or replacement (every 12-24 months in standby service).

### 12.4 Solid-Fuel Boiler Placement
Boiler is in Zone A (Wet Zone) or a dedicated boiler room adjacent to Zone A.
**Low-water cutoff:** Montana boiler safety rules require a low-water fuel cutoff for automatically fired hot water boilers. The threshold in the model code is 400,000 BTU/hr input. Below that, the cutoff may not be mandatory, but the boiler manufacturer instructions may require it.
**Base case:** select a boiler with a factory-installed low-water cutoff regardless of input size.
**Chimney:** exterior chimney, above the roof line, with a spark arrestor.

### 12.5 Sensors for Fuel and Generator
**Propane tank:** level gauge (mechanical, readable without power) plus optional electronic level sensor. Low-level alert at 20 percent.
**Diesel tank:** level gauge, water-in-fuel sensor, leak detection in the containment dike.
**Generator:** run status, fuel level, oil pressure, coolant temperature, battery voltage.
**Boiler:** water temperature, low-water cutoff status, flue temperature (optional).
All electronic sensors feed the primary controller. Mechanical gauges remain as the analog fallback.

### 12.6 Flexibility Clause (Addition)
The base requirements for this section: fuel storage must be separated from ignition sources by code-required distances or fire-rated construction. Propane tank setbacks must match the tank size and WUI status. Diesel tank must have spill containment and outdoor venting. Low-water cutoff on the boiler is mandatory. Delivery access to the propane tank must be maintained year-round. Mechanical fuel gauges must remain.

### 12.7 Variant Summary
Site is WUI: bury propane tank or use vault. Cost +3000 to +8000 USD.
1000+ gallon propane needed: two 500-gallon tanks manifolded. Cost +1500 to +3000 USD vs single tank.
Diesel tank indoors: double-wall UL 2085 tank plus containment. Cost +2000 to +5000 USD.
Boiler below 400k BTU: low-water cutoff may be omitted per code, but install anyway. Cost +500 to +1000 USD.
Delivery access difficult in winter: extend driveway, add turn-around, or move tank closer to road. Cost +2000 to +10000 USD.
