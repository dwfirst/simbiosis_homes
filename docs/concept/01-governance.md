# Multi-Owner Governance & Compute Allocation

## 1. Purpose

This document defines the operational rules for a building with 1 to 4 owners. It covers compute allocation, greenhouse use, EV charging, sale of a unit, and dispute resolution. It is referenced from Node 08 (Structure & Seismic).

The structure enforces physical separation (double-frame walls, floating floors, flexible connections). This document enforces social and operational separation.

## 2. Compute Allocation

The compute spine (Node 03) is a shared resource. Allocation follows three principles:

- **Base quota per unit.** Each unit has a guaranteed share of the total compute capacity. With 4 units, the base quota is 25% each. With 2 units, 50% each. With 1 unit, 100%.
- **Priority within quota.** A unit can use its full quota at any time. The controller schedules jobs so that no unit is starved.
- **Surplus allocation.** If a unit does not use its full quota, the unused capacity is available to other units first, then to external clients. Revenue from external clients is distributed proportionally to the units that contributed the surplus.

**Technical implementation:** the primary controller (Node 04) enforces quotas via job scheduling weights. No unit can exceed its quota without buying surplus from another unit. The charter defines the default weights; owners can adjust them by unanimous agreement.

**Variant A:** if all owners agree, quotas can be pooled into a single shared pool with no individual limits. This simplifies scheduling but removes the guarantee. Suitable only for owners who trust each other and have similar usage patterns.

**Variant B:** if one owner needs a large dedicated block (e.g., for a training run), they can rent quota from other owners for a defined period. The rental rate is set by the charter or negotiated case by case.

## 3. Sale of External Compute

- Only **surplus** capacity is sold externally. The base quota of each unit is never sold without that unit explicit consent.
- External clients are billed at a rate set by the charter. The rate covers electricity, maintenance, and a margin.
- Revenue is distributed: first to cover operating costs (electricity, maintenance, reserve fund), then proportionally to the units that contributed surplus.
- **Reserve fund:** a fixed percentage of external revenue is set aside for hardware replacement (Node 03 states 3–4 year hardware lifecycle).

**Base requirement:** no external sale may reduce a unit below its base quota. If external demand exceeds surplus, external clients are queued, not prioritized over residents.

## 4. Greenhouse Use

The greenhouse (Node 05) has four climate zones. It is a shared resource with shared labor and shared harvest.

- **Rotation of responsibility.** Each zone is assigned to one unit for a defined period (e.g., one month). The assigned unit is responsible for watering, pruning, and reporting issues.
- **Shared harvest.** Produce is available to all units. No unit owns a specific plant or bed.
- **Absence.** If a unit is away, its rotation passes to the next unit in sequence. The charter defines the sequence.
- **Major decisions** (change of crops, new equipment, structural changes to partitions) require unanimous agreement.

**Variant C:** if owners prefer individual plots, zones can be subdivided into private beds with shared infrastructure (heat, water, ventilation). Cost change: none on structure, but requires physical dividers within zones.

## 5. EV Charging

- **Resident charging** is submetered per unit. Each unit pays for its own energy.
- **Guest charging** uses app-based payment at a rate set by the charter. Revenue covers electricity and a small maintenance margin.
- **V2H (Vehicle-to-Home)** is optional. If a resident installs a bidirectional charger, the vehicle battery can back up that unit only, not the whole building, unless the charter explicitly allows shared V2H.
- **Load management** (Node 08) is mandatory. No unit can override the EMS to draw more than its share during peak building load.

## 6. Sale of a Unit

- A unit may be sold to a new owner. The sale is **encumbered by this charter**. The new owner accepts the charter automatically as a condition of purchase.
- Existing owners have **no right of first refusal** unless the charter is amended to include one. This keeps the unit liquid and avoids deadlock.
- The new owner inherits the unit base quota, the greenhouse rotation position, and the EV charging allocation.

**Variant D:** if owners want control over who joins, add a right of first refusal with a defined response window (e.g., 30 days). This slows sales but preserves community fit.

## 7. Quiet Hours and Sound Expectations

- The structure provides acoustic separation (Node 08). The charter defines behavioral expectations that the structure cannot enforce.
- **Quiet hours:** defined by unanimous agreement. Default: 22:00–07:00 for impact noise (music, power tools, heavy equipment). Continuous low-level noise (fans, pumps) is handled by the structure, not by behavior.
- **Compute noise:** the compute spine is isolated (Node 03). Residents are not expected to hear it. If they do, it is a maintenance issue, not a behavioral one.

## 8. Decision Making and Disputes

- **Routine decisions** (greenhouse rotation, guest charging rate) are made by simple majority.
- **Structural or financial decisions** (quota changes, new equipment, charter amendments) require unanimous agreement.
- **Disputes** are first addressed directly between the parties. If unresolved, a neutral third party (mediator) is engaged. The charter defines the mediator selection process.

## 9. Flexibility Clause

Every parameter in this document can be changed by unanimous agreement of the owners. However, the following must be preserved:

- Every unit has a defined base quota of compute.
- External sale never reduces a unit below its base quota.
- Greenhouse labor and harvest are shared, not privately owned (unless Variant C is adopted).
- A new owner accepts the charter automatically.
- Disputes have a defined resolution path.

## 10. Related Documents

- [Node 03 — Compute Spine](../nodes/03-compute-spine.md)
- [Node 04 — Heating & Cooling Loop](../nodes/04-heating-cooling-loop.md)
- [Node 05 — Greenhouse](../nodes/05-greenhouse.md)
- [Node 08 — Structure & Seismic](../nodes/08-structure-seismic.md)
