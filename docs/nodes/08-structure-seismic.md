# Node 08 — Structure & Seismic

## 1. Purpose

This node defines the structural system for the three buildings (main house, technical building, greenhouse) and the connections between them. It covers foundations, columns, seismic isolation, sound isolation between units, the open parking structure under the house, and the EV charging infrastructure integrated into the parking area.

## 2. Why Columns (Not a Design Choice)

The house and technical building are raised on columns. This is **not an aesthetic decision**. It is a response to the site conditions in Montana and similar cold, windy, seismic regions.

**Seismic:** Most of western Montana is Seismic Design Category D. Bozeman design criteria confirm Category D with wind speeds up to 115 mph for residential structures [citation:2][citation:14]. A building on columns with engineered isolators can move independently of the ground during a seismic event, reducing forces on the superstructure.

**Wind:** Montana wind is not uniform. Bozeman lists 90–115 mph depending on the code path [citation:2][citation:14]. Raising the building allows wind to pass under and around, rather than hitting a solid wall at grade. This reduces uplift and lateral pressure on the envelope.

**Frost and snow:** Columns lift the building above drifting snow and frost heave. The underfloor space also becomes the service entry zone (Node 02) and the open parking area.

**Base requirement:** column footings must be designed by a licensed structural engineer using the geotech report (Node 01) and the site-specific seismic and wind loads. No prescriptive solution.

**Variant A:** if the geotech report shows shallow bedrock, columns can be shorter and founded directly on rock. Cost change: -10–15% on foundation. If soil is deep alluvium, longer piles or larger footings are required. Cost change: +15–25%.

## 3. Open Parking Structure Under the House

The space between the columns under the house is an **open parking structure**, not a closed garage.

- **No walls between columns.** The parking area is open on all sides. Natural ventilation is sufficient. No mechanical exhaust system is required for the parking volume.
- **Slab with slope and drainage.** The parking slab slopes to perimeter drains. Snowmelt and wash water do not pool under the house.
- **Exhaust canopy.** Even in an open structure, vehicle exhaust can collect under the floor above. A local exhaust canopy or directed fan over the parking zone prevents exhaust from rising into living space through gaps.
- **1-hour fire barrier** between the parking level and the residential floor above. This is a standard requirement for vehicle storage under living space.
- **Lighting** for driveways and pedestrian paths. Montana winter daylight is short; the parking area needs illumination even if it is open.
- **Ice protection.** Slope, drainage, and (if needed) local slab heating in the parking zone prevent ice buildup. Slab heating can be fed from the compute loop (Node 04) during cold periods.

**Base requirement:** the parking structure must remain open (no enclosing walls) so that natural ventilation is maintained. If the client later encloses it, mechanical ventilation and a fire-rated separation become mandatory.

**Variant B:** if the site is in a high-snow area, add a snow-melt system on the parking slab (hydronic, fed from the compute loop) to prevent ice. Cost change: +$3,000–$8,000, but reduces slip risk and slab damage.

## 4. Sound Isolation Between Units

The target occupants are high-performance specialists working at different hours. Sound isolation is a **functional requirement**, not a luxury.

- **Separate frames between units.** Each unit has its own wall frame. No shared studs between units. This is the only reliable way to isolate impact and low-frequency noise.
- **Air gap and acoustic insulation** between the two frames.
- **Floating floors** in units above the parking level and above the technical building. This isolates footfall and equipment vibration.
- **Vibration isolators** under compute racks (Node 03) and under pumps (Node 04).
- **Flexible connectors** on every pipe and duct that crosses a unit boundary. A rigid pipe is a sound bridge.

**Base requirement:** no rigid structural connection between units. Fire separation and sound separation are achieved by the same double-frame wall.

**Variant C:** if the budget does not allow full double-frame walls, use a single frame with resilient channels and acoustic insulation. Cost change: -30–40% on partition cost, but lower isolation performance. Acceptable only if the units are occupied by the same owner or family.

## 5. EV Charging in the Open Parking Structure

The open parking area includes EV charging for residents and guests. The design goal is **avoiding a service upgrade** while providing reliable charging.

**Base case: Level 2 chargers with load management.**
- Each parking space has a Level 2 (240V) charger or a NEMA 14-50 outlet.
- **NEC 2026 Article 625.42(B)** permits feeder sizing based on managed load, not the sum of all chargers. A 10-space garage with 40A chargers would otherwise need 400A feeder; with load management, 200A is sufficient [citation:7].
- An **Energy Management System (EMS)** monitors total building load and dynamically reduces charging current when other loads rise. This is the same principle used to avoid panel upgrades in Montana homes [citation:6][citation:15].
- **Permit note:** Level 2 chargers require an electrical permit in Montana (Bozeman, Dillon: $75–$500, ~3 weeks review). Level 1 (120V) plugged into existing outlet is exempt [citation:6][citation:10].

**Payment and allocation.**
- Each charger is **submetered per unit**. Residents pay for their own charging through the building management system.
- **Guest charging** uses a QR-code or app-based payment, billed at a rate set by the community charter (see governance document).
- **Variant D: V2H (Vehicle-to-Home).** If a resident owns a V2H-capable EV (Ford F-150 Lightning, GM Ultium, Tesla Cybertruck), a bidirectional charger can use the vehicle battery as backup for the unit. Cost: $5,500–$12,000 installed, proprietary to each manufacturer [citation:5][citation:14]. Not base case; optional for residents who already own compatible vehicles.

**Base requirement:** the electrical service must be sized for managed load, not unmanaged peak. Without load management, the feeder and service would need to be oversized, increasing cost and possibly triggering a utility service upgrade.

**Variant E:** if the budget does not allow Level 2 chargers for every space initially, install **conduit and wiring for future chargers** (EV-capable) in all spaces, and Level 2 chargers in 50% of spaces. Cost change: -40% on initial charger cost, but future installation is simpler.

## 6. Service Entries and Flexible Connections

Every pipe, duct, and cable that enters a building from the service channel (Node 02) must pass through a **flexible connection**.

- **Seismic:** the building moves independently of the channel. A rigid connection would crack or break.
- **Settlement:** even minor differential settlement between the channel and the building would stress rigid connections.
- **Sound:** flexible connectors also break sound bridges between the channel and the building.

**Base requirement:** no rigid penetration of a building envelope by any service line. Every entry uses a flexible sleeve, bellows, or elastomeric connector rated for the line type (fluid, power, data).

## 7. Multi-Owner Operation

The building is designed for 1–4 owners. Structural separation (double-frame walls, floating floors) supports privacy. Operational rules for compute allocation, greenhouse use, and EV charging are defined in the **governance document: [01-governance.md](../concept/01-governance.md)**.

**Base requirement:** no structural element shared between units without a flexible or isolated connection. The governance document defines the social and operational rules; the structure enforces them physically.

## 8. Flexibility Clause

Every parameter in this document can be changed to reduce cost or to meet the client specific needs. However, the following must be preserved:

- Column footings designed by a licensed structural engineer.
- Open parking structure with natural ventilation (no enclosing walls).
- 1-hour fire barrier between parking and living space.
- Separate frames between units (or resilient channels as Variant C).
- Flexible connections on every service entry.
- EV charging with load management to avoid service upgrade.

## 9. Reverse Engineering: If Conditions Change

| Condition | Change | Cost Direction |
|---|---|---|
| Shallow bedrock | Shorter columns, direct rock foundation | -10–15% on foundation |
| Deep alluvium | Longer piles, larger footings | +15–25% on foundation |
| High snow area | Add hydronic snow-melt on parking slab | +$3,000–$8,000 |
| Budget for double-frame walls unavailable | Single frame + resilient channels | -30–40% on partition |
| EV charger budget limited | Conduit for all, chargers in 50% | -40% on initial charger cost |
| Resident owns V2H-compatible EV | Add bidirectional charger | +$5,500–$12,000 |
