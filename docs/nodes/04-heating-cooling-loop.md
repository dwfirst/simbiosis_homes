# Node 04 — Heating & Cooling Loop

## 1. Purpose

The loop transfers heat from the compute spine (Node 03) to the building, the greenhouse, and the domestic hot water. It also provides cooling for the compute spine when outdoor conditions allow, and it manages backup heat from a solid-fuel boiler when compute heat is insufficient.

## 2. Primary Loop (Compute-to-Heat-Exchanger)

- **Fluid:** water-glycol mix (30–50% glycol) for freeze protection during shutdowns.
- **Supply temperature from compute spine:** 45–65°C, depending on load.
- **Return temperature:** 35–45°C, depending on heat extraction.
- **Piping:** insulated steel or PEX-AL-PEX, sized by flow rate and pressure drop. Main lines run in the service channel (Node 02).
- **Pumps:** two parallel pumps (duty/standby), variable-speed, controlled by differential pressure. Automatic switchover on pump failure.
- **Heat exchanger:** plate heat exchanger between the compute loop and the building heating loop. Sized for peak compute heat output plus 20% margin.

**Base requirement:** the compute loop must be able to reject heat even when the building does not need it. This means a bypass to the greenhouse, ground storage, or dry cooler is mandatory. Without a heat sink, the compute loop overheats and the spine shuts down.

## 3. Building Heating Distribution

- **Underfloor heating** in all living units. Low temperature (35–45°C supply), compatible with compute loop temperatures.
- **Domestic hot water:** indirect tank heated by the compute loop via a heat exchanger. Backup electric element for periods when compute heat is insufficient.
- **Zone control:** each apartment has its own manifold and thermostat. The loop controller modulates flow to each zone based on demand.

**Base requirement:** each apartment must have an independent shutoff valve. If one apartment's system fails, the others continue operating.

## 4. Greenhouse: Four Climate Zones

The greenhouse is a large glass structure (as shown in the visualization), divided internally into **four climate zones**. Each zone has independent temperature and humidity control, but all zones share the same heat source.

### 4.1 Zone Definitions

| Zone | Climate target | Typical plants | Heat priority |
|---|---|---|---|
| Z1 | Tropical (H1a): >15°C, high humidity | Banana, papaya, mango | Highest |
| Z2 | Subtropical (H1b): 10–15°C | Citrus, passionfruit | High |
| Z3 | Warm temperate (H2): 5–10°C | Figs, olives, hardy herbs | Medium |
| Z4 | Cool temperate (H3): 0–5°C | Cold-hardy greens, overwintering | Lowest |

### 4.2 Physical Separation

- Zones separated by **polycarbonate partitions** (transparent, thermally resistant). Partitions do not need to be structural — they are light frames with polycarbonate panels.
- **Height stratification:** warm air rises. Upper tiers in Z1 and Z2, lower tiers in Z3 and Z4.
- **Air circulation:** small fans between zones prevent stagnation and distribute heat. Fans run on low voltage, backed by the battery system.

### 4.3 Heat Distribution to Zones

- Heat from the compute loop enters the greenhouse at **Z1 first** (highest temperature demand).
- After Z1, the return flow (still warm) goes to Z2, then Z3, then Z4.
- Each zone has a **motorized valve** controlled by its own thermostat. If a zone is satisfied, its valve closes and heat goes to the next zone.
- In summer, when the building does not need heat, the full compute heat output goes to the greenhouse. Z1 and Z2 absorb most of it; excess goes to Z3/Z4 or to ground storage/dry cooler.

**Base requirement:** Z1 and Z2 must never drop below their minimum temperatures. If compute heat is insufficient, the solid-fuel boiler (Section 5) takes over for these zones first.

## 5. Backup Heat: Solid-Fuel Gasification Boiler

### 5.1 Why a Gasification Boiler

A conventional wood stove or boiler runs in cycles (hot when fired, cold when burned out) and has 50–60% efficiency. A **gasification boiler** burns pyrolysis gases at high temperature and achieves **85–90% efficiency**. It produces more usable heat per unit of wood and less creosote.

**Regulatory note:** in Montana nonattainment areas (Flathead, Missoula), new wood heaters must be **EPA NSPS 2020+ certified**. Confirm the selected boiler carries the EPA label before purchase.

### 5.2 Buffer Tank

A gasification boiler produces high heat output in a short burn cycle. Without a buffer, that heat has nowhere to go and the boiler runs inefficiently. A **buffer tank of 500–1000 gallons** (1900–3800 L), insulated to R-24 or better, stores the heat and releases it gradually.

- Buffer location: technical building, adjacent to the main heat exchanger.
- Buffer connection: the boiler charges the buffer; the buffer feeds the building and greenhouse loops via a mixing valve.

### 5.3 Integration with Compute Loop

- Normal operation: compute loop supplies heat; boiler is off.
- Low compute heat (low load, very cold weather): boiler fires, charges buffer, buffer supplements the loop.
- Compute loop failure or maintenance: boiler and buffer carry the full heating load.
- Emergency (power failure, controller failure): boiler runs on natural draft; buffer releases heat by gravity circulation. No electronics required for basic operation.

**Base requirement:** the boiler and buffer must be capable of maintaining Z1 and Z2 greenhouse temperatures and a minimum living temperature (e.g., 15°C) for at least 48 hours without electrical power. This determines the minimum buffer size and boiler capacity.

## 6. Cooling: Summer Mode

- When outdoor temperature is high and the building does not need heat, the compute loop must still reject heat.
- **Priority 1:** greenhouse (Z1 and Z2 absorb heat; Z3/Z4 absorb excess).
- **Priority 2:** ground storage (boreholes or horizontal loops) — heat is injected into the ground for winter recovery.
- **Priority 3:** dry cooler (air-cooled radiator) — final rejection to atmosphere.

**Base requirement:** at least two heat rejection paths must be available at all times. If the greenhouse is at capacity and ground storage is unavailable, the dry cooler must be operational.

## 7. Controls and Redundancy

### 7.1 Hot-Standby Controllers

- **Primary controller:** in the technical building. Manages pumps, valves, boiler, and heat distribution.
- **Secondary controller:** in the main building's server room. Mirrors Primary via fiber in the service channel.
- Both controllers receive all sensor data. Primary acts; Secondary monitors and is ready to take over.
- **Switchover:** automatic on Primary failure, <1 second. Manual switch also available.

### 7.2 Sensor Density

- Temperature and humidity sensors in every zone of the greenhouse, every apartment, the technical building, and the compute spine.
- Flow and pressure sensors on every pump group and every heat exchanger.
- Leak detection in the service channel and under each rack.
- Protocol: Modbus RTU or 1-Wire, wired. No wireless in critical paths.

### 7.3 Analog and Mechanical Layer

- **Mechanical thermometers** on every pump group, heat exchanger, and zone supply/return. Readable without power.
- **Mechanical pressure gauges** on every supply/return line.
- **Pump switches:** physical Auto / Manual / Off selector on each pump group. In Manual, the operator can run the pump directly, bypassing the controller.
- **Mechanical locks** on all technical doors, in addition to electronic access.
- **Kill switch:** physical disconnect for the compute spine power, located in the server room and in the technical building. Protected by a cover or key to prevent accidental activation. Complies with NIST PE-10 intent: emergency power-off must be physically accessible and protected from unauthorized activation.

**Base requirement:** every critical function must have a manual override. If all electronics fail, a person with a key must be able to keep the building and greenhouse above freezing using the boiler, buffer, and manual pump control.

## 8. Flexibility Clause

Every parameter in this document can be changed to reduce cost or to meet the client's specific needs. However, the following must be preserved for the system to remain functional:

- The compute loop must always have at least two heat rejection paths.
- Z1 and Z2 greenhouse zones must never drop below their minimum temperatures.
- The boiler and buffer must maintain minimum temperatures for at least 48 hours without electrical power.
- Every apartment must have an independent shutoff.
- Every critical function must have a manual override.
- Mechanical thermometers and pressure gauges must remain, even if electronic sensors are reduced.

Any deviation from the base case must be reviewed against these requirements. If a cheaper option compromises a base requirement, it is not a valid substitution — it is a different system with different performance.

## 9. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Compute heat is consistently sufficient, even in winter | Reduce boiler capacity and buffer size | -20–30% on backup system |
| Compute heat is insufficient most of the winter | Increase boiler and buffer; consider second boiler | +30–50% on backup system |
| Greenhouse zones can be reduced from 4 to 2 | Merge Z3/Z4 into one zone; simplify partitions and valves | -15–25% on greenhouse HVAC |
| Local code prohibits wood boilers in the area | Switch to propane or pellet boiler (higher operating cost, lower capital) | +10–20% capital, +30–50% fuel cost |
| Ground storage is not feasible (rock, groundwater) | Remove ground loop; rely on greenhouse + dry cooler | -10–15% capital, but less winter heat recovery |

## 10. Open Items

1. Confirm boiler model and EPA certification for the target county.
2. Confirm buffer tank size based on actual compute heat output and building heat load.
3. Confirm greenhouse zone partition design with the greenhouse supplier.
4. Confirm ground storage feasibility with the geotech report (Node 01).
5. Confirm controller compatibility with selected sensors and pumps.

## 11. What This Node Does Not Cover

- Compute spine cooling hardware (Node 03).
- Service channel construction (Node 02).
- Water system and condensate treatment (Node 06).
- Electrical distribution and backup power (Node 07).
- Structural design of boiler and buffer foundations (Node 08).
