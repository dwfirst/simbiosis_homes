# Node 01 — Site & Foundation

## 1. Assumptions

This node assumes a site in **Montana**, outside incorporated city limits (unincorporated county), in a cold-climate, seismic-prone region. The site is currently empty. No structures, no utilities, no well.

Target configuration: one residential building (on columns), one technical building (on columns), one greenhouse (on slab). Connection via shallow service channel.

## 2. First Action on Site: Geotechnical Investigation

**Do not dig, pour, or order materials until the geotech report is in hand.**

Required borings:
- Minimum 3 borings: one at the main house footprint, one at the technical building, one at the greenhouse.
- Depth: to refusal or to a depth sufficient to characterize bearing strata and groundwater.
- Report must state: soil classification, bearing capacity, groundwater level, frost-susceptibility, and presence of rock.

**Why this is non-negotiable:**
- The house and technical building will sit on columns. Column footings must bear on competent strata.
- The service channel will be shallow (see Node 02). If groundwater is high, the channel design changes (membrane, sump, or raised profile).
- Montana seismic design categories (D0 or D) are calculated from site-specific soil conditions. The geotech report feeds directly into the structural engineer's seismic design [citation:2].

**Cost placeholder:** $3,000–$8,000 for a residential-scale geotech investigation in Montana. This is a fraction of the cost of re-engineering after a foundation failure.

## 3. Regulatory Context (2026)

### 3.1 Building Codes
Montana adopted the **2024 ICC codes** effective September 26, 2026. Certified jurisdictions must adopt within 90 days. Bozeman's effective date is January 1, 2027 [citation:1].

**Implication:** The project must be designed to **2024 IRC/IBC with Montana amendments**, not the older 2021 codes. Any architect or engineer engaged must confirm they are working to the 2024 edition.

### 3.2 Seismic Design
Most of western Montana falls into **Seismic Design Category D** (IBC) or D0 based on site-specific soil [citation:2]. For the column-supported house and technical building, this means:
- Column footings and anchorage must be engineered, not prescriptive.
- The connection between columns and superstructure must accommodate drift.
- The service channel must have flexible connections at building entries (see Node 02).

**For a 4-unit residential building** (our target), the project is not a single-family home under IRC. It falls under IBC. A Montana-licensed structural engineer is required for the seismic design [citation:10].

### 3.3 Permitting Pathway (Unincorporated County)
For **fewer than five dwelling units** (single-family, duplex, triplex, fourplex) that are not transient guest units:
- **State building permit:** Typically **exempt** in unincorporated counties (e.g., Gallatin County / Big Sky) [citation:3].
- **County Land Use Permit (LUP):** **Required** in most zoned districts. Submit site plan, project description, and (if on steep slope or ridgeline) geotechnical report [citation:3].

**Action:** Before design begins, confirm the specific county and zoning district. The LUP process is the primary regulatory gate, not the state building code.

### 3.4 Water (If a Well Is Needed)
If the site has no municipal water, a well may be drilled under the **groundwater permit exception**:
- Maximum 35 gallons per minute, not to exceed 10 acre-feet per year.
- File **Notice of Intent (Form 602I)** with DNRC before use.
- Driller files **Well Log (Form 603)** within 60 days.
- File **Notice of Completion (Form 602)** within 60 days of putting water to use [citation:11].

**For the project's water strategy:** The primary water source is **condensate recovery** and **roof catchment** (see Node 06). A well is backup, not primary. This keeps the project within the exemption threshold and reduces regulatory burden.

## 4. Foundation Strategy

### 4.1 Main House — Columns
- Column footings: reinforced concrete, sized by structural engineer based on geotech bearing capacity.
- Columns: steel or engineered timber, with **seismic isolators or flexible connections** at the footing and at the superstructure.
- The space under the house (between columns) serves as the **entry zone for all services** from the channel. No excavation under the house is needed for service access.

**Why columns:**
- Seismic decoupling: the house can move independently of the ground to a controlled degree.
- Service access: the underfloor space is the natural transition zone between the shallow channel and the building's internal distribution.
- Frost protection: the underfloor space can be insulated and, if needed, tempered by waste heat.

### 4.2 Technical Building — Columns
Same logic as the main house, but with **vibration isolation** added at the column-superstructure connection. Pumps and generators produce continuous low-frequency vibration. Columns with elastomeric pads or spring isolators prevent that vibration from transmitting into the ground and into the adjacent house.

### 4.3 Greenhouse — Slab
The greenhouse carries soil, water, and plants. A **slab-on-grade with thickened edges** is appropriate. Key requirements:
- **Deformation joint** at the connection to the service channel. The greenhouse slab will move differently from the channel. A flexible joint prevents cracking.
- **Insulation under the slab** (XPS or equivalent) to prevent frost heave and reduce heat loss to the ground.
- **Drainage:** the slab should slope slightly toward a collection point for condensate and irrigation runoff.

## 5. Site Layout (Conceptual)

Three buildings, connected by a shallow service channel (Node 02).

- **Main house:** oriented with the long axis east-west. The north wall is the compute spine (insulated, no windows). The south side is living space with glazing.
- **Technical building:** adjacent to the main house, connected by the shortest possible channel run. Houses pumps, heat exchangers, generators, and the water treatment system.
- **Greenhouse:** positioned to receive maximum winter sun. Connected to the technical building by the channel (heat and condensate supply).

**Channel routing:** the channel runs along the north side of the house and technical building, then turns to the greenhouse. It is shallow (see Node 02) and covered by removable decking. Vehicle and pedestrian crossings are handled by portals or bridges (Node 02).

## 6. What This Node Does Not Cover

- Structural sizing of columns and footings (requires licensed engineer with geotech data).
- Channel construction details (Node 02).
- Seismic isolation hardware selection (Node 08).
- Water rights beyond the exemption (if the project exceeds 35 gpm / 10 acre-feet, a full water right permit is required).

## 7. Open Items for Site-Specific Confirmation

1. Exact county and zoning district. This determines LUP requirements and timeline.
2. Geotech report (must be completed before design freeze).
3. Confirmation that the site is not in a floodplain or wildfire severity zone (these trigger additional studies in Montana counties) [citation:3].
4. Confirmation that the project will remain under the 5-dwelling-unit threshold for state building permit exemption, or plan for a state permit if the configuration changes.
