# Node 05 — Greenhouse

## 1. Purpose

The greenhouse is a large glass structure connected to the main house and technical building by the service channel (Node 02). It serves three functions:

- **Food production** for residents, across four climate zones.
- **Heat sink** for the compute spine in summer, when the building does not need heat.
- **Solar gain** in winter, reducing the building's heating demand.

It is not a decorative conservatory. It is a working part of the building's thermal and food system.

## 2. Geometry and Structure

### 2.1 Base Case: Glass Structure on Slab

- **Footprint:** rectangular, sized by the client. Base case for the four-zone configuration: approximately 12 m × 6 m (72 m²). Can be scaled up or down.
- **Structure:** aluminium or steel frame, powder-coated for corrosion resistance. Glazing bars sized for snow load (Montana ground snow load varies by county; confirm with structural engineer).
- **Glazing:** double-wall polycarbonate (16 mm or 20 mm) for most surfaces, tempered glass for the south-facing wall if maximum light transmission is required. Polycarbonate is cheaper, lighter, and has better insulation value. Glass is better for light and aesthetics.
- **Foundation:** slab-on-grade with thickened edges, insulated underneath with XPS. The slab carries soil beds, water tanks, and the partition frames.

**Variant A:** if the client wants the greenhouse to match the colonial aesthetic of the house, use glass with a painted steel frame instead of polycarbonate. Cost change: +30–50% on glazing, but better visual integration.

**Variant B:** if the client wants maximum food production per dollar, use a polycarbonate tunnel (hoop house) instead of a rigid frame structure. Cost change: -40–60%, but shorter lifespan and less snow resistance.

### 2.2 Slab and Drainage

- Slab slopes slightly (0.5–1%) toward a central drain or toward the service channel connection.
- Drain collects irrigation runoff and condensate, routes to the water storage tanks (Node 06).
- Insulation under slab: XPS, minimum 50 mm, to prevent frost heave and reduce heat loss to ground.

**Base requirement:** the slab must be insulated and drained. An uninsulated slab in Montana will heave, crack, and lose heat continuously.

## 3. Four Climate Zones

The greenhouse is divided internally into four climate zones as defined in Node 04:

| Zone | Climate | Target temperature | Separation |
|---|---|---|---|
| Z1 | Tropical | >15°C | Polycarbonate partition |
| Z2 | Subtropical | 10–15°C | Polycarbonate partition |
| Z3 | Warm temperate | 5–10°C | Polycarbonate partition |
| Z4 | Cool temperate | 0–5°C | Polycarbonate partition |

### 3.1 Partition Design

- **Frames:** light aluminium or timber frames, anchored to the slab.
- **Panels:** 10–16 mm polycarbonate, transparent, UV-stabilized.
- **Doors:** between adjacent zones, self-closing, insulated. Allows access without mixing air excessively.
- **Height:** partitions run from slab to roof structure. No gaps at the top — warm air must not bypass the zone boundaries.

**Base requirement:** each zone must be physically separable. A single open greenhouse cannot maintain four different climates.

### 3.2 Zone Layout

- **Z1 (tropical):** closest to the heat input from the service channel. Receives heat first.
- **Z2 (subtropical):** adjacent to Z1, receives return heat.
- **Z3 (warm temperate):** middle zone, moderate heat.
- **Z4 (cool temperate):** furthest from heat input, lowest temperature, suitable for overwintering and cold-hardy crops.

**Variant C:** if the client wants fewer zones, merge Z3 and Z4 into a single cool zone. Cost change: -15–25% on partitions and zone controls, but less flexibility.

## 4. Ventilation

### 4.1 Why Ventilation Is Mandatory

- **Temperature control:** in summer, even with heat diverted to the building or ground storage, the greenhouse will overheat without ventilation. Glass/polycarbonate structures reach 40–50°C in direct sun.
- **Humidity control:** high humidity promotes fungal disease. Tropical zones need high humidity, but not stagnant air.
- **Condensation:** without air movement, condensate forms on the inside of the glazing and drips onto plants. Some dripping is acceptable in a greenhouse, but excessive condensation damages electronics and structure.

### 4.2 Base Case: Automated Roof Vents and Side Louvers

- **Roof vents:** ridge vents or continuous ridge opening, automated with wax actuators or electric actuators. Wax actuators require no power — they open when temperature rises. Electric actuators integrate with the zone controller.
- **Side louvers:** low-level inlets on the leeward side, adjustable. Allow cool air to enter low and hot air to exit high (stack effect).
- **Circulation fans:** low-voltage fans inside each zone, moving air continuously. Prevent stagnation and condensation on plants.

**Variant D:** powered exhaust fans with thermostatic control. More effective than passive vents, but requires power and maintenance. Cost change: +$1,500–$3,000, but better temperature control in summer.

**Variant E:** no mechanical ventilation, manual vents only. Cheapest, but requires daily attention and risks overheating on hot days. Not recommended for a greenhouse that is part of the building's thermal system.

### 4.3 Winter Ventilation

In winter, ventilation must be minimal to conserve heat. But some air exchange is still needed:
- **Crack ventilation:** small openings at the ridge, sufficient to prevent humidity buildup.
- **Heat recovery:** if the greenhouse is tightly sealed, a small ERV can recover heat from exhaust air. Optional, not base case.

## 5. Heating and Cooling

### 5.1 Heat Input

- Heat enters at Z1 from the service channel (Node 02) or from a dedicated branch of the main heating loop (Node 04).
- Each zone has a motorized valve and thermostat. Heat flows to Z1 first, then Z2, Z3, Z4 in sequence.
- If a zone is satisfied, its valve closes and heat moves to the next zone.

### 5.2 Summer Cooling

- **Priority 1:** open vents and louvers. Passive cooling.
- **Priority 2:** circulation fans. Move air through the zones.
- **Priority 3:** shade cloth or external blinds on the south roof. Reduce solar gain. Manual or automated.
- **Priority 4:** if still too hot, the compute loop's heat is diverted to ground storage or dry cooler (Node 04), not to the greenhouse.

**Base requirement:** the greenhouse must not rely on the compute loop for cooling in summer. The compute loop is a heat source; in summer, it must have an alternate sink.

### 5.3 Winter Heating

- Normal: compute loop supplies heat.
- Backup: solid-fuel boiler and buffer tank (Node 04) maintain Z1 and Z2 temperatures.
- Emergency: boiler on natural draft, buffer by gravity circulation.

## 6. Condensate and Water

- Condensate from glazing and from the service channel drains to the slab drain.
- Slab drain routes to the water storage tanks (Node 06).
- Water from tanks is filtered and used for irrigation.
- Overflow routes to a French drain or infiltration pit outside the greenhouse.

**Base requirement:** all condensate and irrigation runoff must be collected, not discharged to the ground surface. In a cold climate, surface discharge becomes ice.

## 7. Controls and Sensors

- **Per zone:** temperature sensor, humidity sensor, valve position feedback.
- **Global:** outdoor temperature, wind speed (for vent control), solar radiation (for shade control).
- **Actuators:** motorized valves, vent actuators, fan controls.
- **Manual override:** each zone has a manual valve bypass and a manual vent opener. If the controller fails, a person can open vents and adjust valves by hand.

**Base requirement:** every automated function must have a manual equivalent. A greenhouse that depends entirely on electronics is a greenhouse that fails when the electronics fail.

## 8. Flexibility Clause

Every parameter in this document can be changed to reduce cost or to meet the client's specific needs. However, the following must be preserved for the system to remain functional:

- The slab must be insulated and drained.
- Each climate zone must be physically separable.
- Ventilation must be available in every zone, with a manual override.
- Condensate and irrigation runoff must be collected.
- Z1 and Z2 must have backup heat from the boiler and buffer.
- Every automated function must have a manual equivalent.

Any deviation from the base case must be reviewed against these requirements. If a cheaper option compromises a base requirement, it is not a valid substitution — it is a different system with different performance.

## 9. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Client wants maximum food production, not aesthetics | Switch to hoop house / polycarbonate tunnel (Variant B) | -40–60% |
| Client wants colonial aesthetic | Glass + painted steel frame (Variant A) | +30–50% on glazing |
| Fewer zones acceptable | Merge Z3/Z4, reduce partitions and valves (Variant C) | -15–25% |
| Summer overheating is severe | Add powered exhaust fans and external shade (Variants D + shade) | +$2,000–$4,000 |
| Site snow load is high | Increase frame size and glazing bar density; confirm with structural engineer | +10–20% on structure |

## 10. Open Items

1. Confirm snow load for the target county with the structural engineer.
2. Confirm glazing choice (polycarbonate vs. glass) with the client.
3. Confirm zone count and partition layout with the client.
4. Confirm vent actuator type (wax vs. electric) with the HVAC engineer.
5. Confirm water storage capacity (Node 06) matches greenhouse irrigation demand.

## 11. What This Node Does Not Cover

- Heat source and loop design (Node 04).
- Water treatment and storage (Node 06).
- Service channel construction (Node 02).
- Structural design of the greenhouse frame for snow and wind (Node 08).
