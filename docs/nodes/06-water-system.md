# Node 06 — Water System

## 1. Purpose

The water system collects, stores, treats, and distributes water for the building and greenhouse. Its primary source is **condensate** from the compute spine and service channel, supplemented by **roof catchment** and, as backup, an **external water connection** (municipal supply or well).

The system is designed for **gravity distribution** where possible, to reduce pump energy and to keep water available during power failures.

## 2. Water Sources

### 2.1 Primary: Condensate Recovery

- Condensate from the compute spine (Node 03) and service channel (Node 02) drains to collection sumps.
- From sumps, a small pump lifts condensate to the storage tanks.
- Condensate is low in minerals (it is distilled water) and requires **mineralization** before use as drinking water or irrigation for certain plants.

### 2.2 Secondary: Roof Catchment

- Rain and snowmelt from the main house roof and greenhouse roof are collected via gutters and downspouts.
- First-flush diverter discards the initial runoff (which carries dust and bird droppings).
- After first flush, water routes to the storage tanks via a filter.

### 2.3 Backup: External Water Connection

- A single connection point to municipal water or a well.
- Normally isolated by a valve. Opened only when storage tanks are depleted and condensate/catchment is insufficient.
- Backflow preventer required by plumbing code to protect the external supply.

**Base requirement:** the external connection must be physically isolated from the stored water system by a backflow preventer. Contamination of the external supply is a code violation and a health hazard.

## 3. Storage Tanks

### 3.1 Two Tanks, Two Locations

- **Tank A:** in the main building, behind the blind north wall (adjacent to the compute spine). This tank is tempered by waste heat from the spine, so it does not freeze.
- **Tank B:** in the greenhouse, at the rear. This tank is in the warmest part of the greenhouse and also does not freeze.

**Why two tanks:**
- Redundancy: if one tank or its distribution line fails, the other continues supplying water.
- Proximity: Tank A serves the house; Tank B serves the greenhouse. Shorter distribution runs, less pumping.
- Thermal buffering: both tanks act as thermal mass, stabilizing temperature in their respective spaces.

### 3.2 Tank Construction

- **Material:** food-grade polyethylene or stainless steel. Polyethylene is cheaper and adequate for non-potable use; stainless steel is required if the water is intended for drinking.
- **Insulation:** external insulation (XPS or spray foam) on all exposed surfaces, R-24 minimum.
- **Elevation:** tanks are mounted on a raised platform or mezzanine, high enough to provide gravity pressure to the distribution points below. Minimum elevation: 3 m above the highest fixture.
- **Access:** each tank has a locked access hatch for cleaning and inspection.

**Variant A:** if gravity pressure is insufficient for the highest fixtures, add a small booster pump on the distribution line. Cost change: +$500–$1,500, but eliminates the need for a taller platform.

**Variant B:** if only one tank is affordable initially, build Tank A first, leave space and connections for Tank B. Cost change: -40% on tank cost, but loses redundancy.

## 4. Treatment

### 4.1 Base Case: Filtration + UV + Mineralization

- **Sediment filter:** 5-micron, removes particulates.
- **Carbon filter:** removes organic compounds and taste/odor.
- **UV sterilizer:** kills bacteria and viruses. Required if water is used for drinking or food preparation.
- **Mineralization cartridge:** adds calcium and magnesium to condensate (which is otherwise mineral-free and corrosive to pipes).

**Base requirement:** if water is used for drinking or irrigation of edible plants, UV sterilization and mineralization are mandatory. Condensate alone is not potable.

### 4.2 Variant: Rainwater-Only Treatment

If condensate volume is low and rainwater is the primary source, a more robust treatment train is needed:
- First-flush diverter (already in catchment).
- Sediment + carbon filtration.
- UV sterilization.
- Optional: reverse osmosis if dissolved solids are high.

**Cost change:** +$1,000–$2,500 for RO, but necessary if rainwater is the main source and water quality is uncertain.

## 5. Distribution

### 5.1 Gravity Distribution

- Tanks elevated; distribution lines slope downward to fixtures.
- Pressure at fixtures depends on elevation difference (approximately 0.1 bar per meter of head).
- For a 3 m elevation, pressure is approximately 0.3 bar (4.3 psi) — adequate for low-flow fixtures and drip irrigation, but not for high-flow showers.

**Base requirement:** gravity pressure must be sufficient for the fixtures it serves. If not, a booster pump is required.

### 5.2 Zones

- **House potable:** kitchen, bathroom sinks, shower. Treated water.
- **House non-potable:** toilet flushing, washing machine. Filtered but not UV-treated.
- **Greenhouse irrigation:** drip lines to each zone. Filtered, not necessarily UV-treated.
- **Technical water:** condensate sump makeup, dry cooler spray (if used). Untreated.

**Base requirement:** potable and non-potable lines must be physically separated and labeled. Cross-connection is a health hazard.

## 6. Freeze Protection

- Tanks are insulated and located in tempered spaces (house, greenhouse).
- Distribution lines in the service channel are protected by the channel's insulation and by the warm compute loop (Node 02).
- Exposed lines outside the channel are heat-traced or drained in winter.
- Tank A is additionally protected by waste heat from the compute spine.

**Base requirement:** no water line may be exposed to freezing temperatures without heat trace or drain-down capability.

## 7. Sensors and Monitoring

- **Tank level:** ultrasonic or float sensor in each tank. Low-level alert at 20%, high-level alert at 95%.
- **Water quality:** turbidity sensor after filtration; UV lamp status.
- **Flow:** totalizer on each distribution zone. Detects leaks (continuous flow when no fixtures are open).
- **Temperature:** tank temperature and distribution line temperature in the channel.
- **Leak detection:** in the tank rooms and at the service channel entries.

**Variant C:** minimal sensors (tank level only). Cost change: -$500–$1,000, but no early warning of leaks or water quality issues. Not recommended for a system that supplies drinking water.

## 8. Flexibility Clause

Every parameter in this document can be changed to reduce cost or to meet the client's specific needs. However, the following must be preserved for the system to remain functional:

- At least one storage tank must be in a tempered space.
- Condensate and roof catchment must be collected, not discharged to the ground.
- A backflow preventer must isolate the external water connection.
- Potable and non-potable lines must be physically separated.
- UV sterilization and mineralization are mandatory if water is used for drinking.
- No water line may be exposed to freezing without heat trace or drain-down.

Any deviation from the base case must be reviewed against these requirements. If a cheaper option compromises a base requirement, it is not a valid substitution — it is a different system with different performance.

## 9. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Condensate volume is low | Rely more on roof catchment; add larger roof collection area | +$1,000–$3,000 on gutters and tanks |
| External water is unreliable | Increase tank capacity; add second tank earlier | +$3,000–$8,000 |
| Gravity pressure insufficient | Add booster pump (Variant A) | +$500–$1,500 |
| Only one tank affordable | Build Tank A first, defer Tank B (Variant B) | -40% on tank cost |
| Water is for irrigation only, not drinking | Omit UV and mineralization | -$1,500–$3,000 |

## 10. Open Items

1. Confirm condensate volume from the compute spine and channel (Node 02, Node 03).
2. Confirm roof catchment area and rainfall/snowmelt data for the target county.
3. Confirm whether an external water connection is available (municipal or well).
4. Confirm tank elevation and gravity pressure at the highest fixture.
5. Confirm local plumbing code requirements for backflow prevention and potable/non-potable separation.

## 11. What This Node Does Not Cover

- Service channel drainage design (Node 02).
- Compute spine cooling (Node 03).
- Greenhouse irrigation layout (Node 05).
- Electrical supply for pumps and UV (Node 07).
- Structural support for elevated tanks (Node 08).
