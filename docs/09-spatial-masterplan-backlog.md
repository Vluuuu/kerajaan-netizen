# DUNIAJOKO.ID — Kingdom Spatial Masterplan & Placement Quality

> **Status: APPROVED DIRECTION / DESIGN BACKLOG — NOT IMPLEMENTED.** Owner approved the need for a mature, coherent kingdom layout. Specific zoning geometry, road alignment, district boundaries and implementations below remain **PROPOSALS** pending code audit, map review and owner approval. Recorded 2026-11-09.

## Why this exists

After Episode 2 was published, the owner identified that the **three new houses sit near/in front of the castle approach** and that future additions must not be scattered wherever there is empty terrain. A kingdom needs readable spatial hierarchy, plausible roads, an evolving settlement, and consistency across video and website. This is **infrastructure/art direction for future content**, not a mandate to invent Episode 3.

## Canonical constraints — preserve history

- Episode 1 (published): a large landscape, **one castle**, Joko is world creator (not king), no citizens.
- Episode 2 (published per owner): **nine selected citizen NPCs and three first houses**, with @KertonAlamaktvpula's attributed comment about housing. The original first houses now form the historical **Kampung Pelopor** / first settlement.
- Keep canonical entity IDs and authoritative positions from **the actual current source code/world snapshot**, not from this drawing, proposal, old documentation or an agent's guesses. IDs reported in the Episode 2 build include `building:castle-origin` and `building:house-01..03`; verify against the current branch.
- **No silent relocation, deletion, scale change, or teleportation** of anything that appears in an already-published episode. If an existing building genuinely blocks the castle road, propose alternatives with an explicit tradeoff; moving it must be a creator-approved, narrated, versioned, in-world event, never a retroactive rewrite.
- The website and the Remotion scenes derive from **one canonical world state**, gated by publication events. Planned zones/ghost placements are **editor-only/noncanonical** until chosen and published.
- Preserve 9 citizens, home ownership/occupancy relationships, paths, spawn positions, and historical episode replay as applicable; do not reset or migrate them casually.
- Followers / **Calon Warga Kerajaan** are distinct from official NPC residents.

## Proposed spatial hierarchy

This is a flexible **logical** zoning scheme, **not final coordinates or a mandate to construct buildings**.

1. **Citadel / Castle Core** — existing castle, defensible elevated terrain, accessible approach, unobstructed hero sightline.
2. **Castle Forecourt + Main Gate Axis** — public open space at entry; preserve space for movement, crowds, ceremonies and camera wide shots. No random housing directly on the gate axis.
3. **Civic Square / Alun-alun Reserve** — potential future gathering place, subject to actual audience comments and creator approval.
4. **Kampung Pelopor** — existing three Episode 2 homes, with believable footpaths, small yards, and possible side-street access; preserve the historical positions unless a later story explicitly relocates them.
5. **Future Residential Expansion** — clustered blocks, not rows of identical houses or random individual placements; reserve connection to the primary street network.
6. **Market & Craft Reserve** — future trade/craft placement near accessible roads but separated from castle forecourt and home frontage as appropriate.
7. **Agriculture / River Corridor** — protect riverbanks and floodplain; any bridge, farm, mill or fishing structure only added after a selected audience comment.
8. **Green & Scenic Reserves** — forest, terrain silhouettes, hills and view corridors to keep the ultra-low-poly world beautiful and geographically large.

**Important:** The zone names are spatial planning placeholders, not already-constructed markets, farms, government buildings or story commitments.

## Required design process BEFORE any further new building

1. **Audit the actual world:** render-free inventory of castle, all 3 house footprints, roads/paths, river shape and bank buffers, terrain heights/slopes, NPC navigation routes; identify orientation and coordinate system.
2. **Establish a consistent map overlay:** north reference, grid/scale, known permanent buildings, areas protected from construction, potential districts and the castle view cone. No arbitrary coordinates copied from a stylized sketch.
3. **Evaluate at least two layout scenarios:** (A) retain homes, route future road/districts around them (preferred first), (B) candidate future in-story redesign/relocation only if physical conflicts cannot be resolved, requiring explicit owner approval and an episode event.
4. **Review with creator:** show plan in editor-only overlay/top-down plan; **do not mutate world canon by approving a visualization alone**.
5. **Only then** implement a shared placement service and reserve future locations. Actual buildings appear only through selected real comments, with controlled event activation when the associated video is published.

## Placement rules (to design, test and expose to agent)

- Every building has **stable ID, kind, footprint/oriented bounds, entrance/door anchor, road connection, world-space transform, terrain clearance, canon event/source reference**.
- **Collision:** prevent intersections with castle/other buildings, roads, steps, walls, trees requiring protection, critical camera corridors and NPC activity areas; do not consider only object center distances.
- **Terrain:** validate average slope, foundation contact/support, vertical difference, cliff edges; avoid floating/intersecting houses.
- **River:** reserve water + both bank buffers/floodplain; prevent building across river or blocking water course without an intentional, authored bridge/canal event.
- **Connectivity:** require an unobstructed, reachable route from building doorway to main road/castle/civic area; account for stairs, grade, bridge requirements and NPC pathfinding.
- **Street logic:** primary gate route + secondary streets + clusters/courtyards, street widths and intersections proportionate to simple low-poly humans. Roads should look natural, not random splines/instant grids.
- **Cinematography:** protect the castle silhouette/approach, avoid buildings cropping the castle, ensure meaningful 9:16 establishing shots and construction shot clearances.
- **Growth:** reserve parcels for future expansions rather than promising that planned zones will be built; proposed parcels must remain editable and optional.
- **Performance:** shared low-poly assets, LOD/instancing where appropriate, no huge detailed region or costly pathfinding precomputation without profiling.
- **Determinism & persistence:** pure eligibility scoring/rules where feasible, seeded procedural placement, explicit override by Joko, versioned migrations and replayable events. Never let a random seed silently change already-published positions.

## Creator-only masterplan viewer (PROPOSED, not approved to code today)

- Top-down/aerial overlay of buildings, labels, zones, road graph, river buffer, NPC paths and protected castle view corridor.
- Differentiate **canonical built objects** from **proposed zone boundaries** and **future ghost placements** visibly.
- Click parcel -> show reason for allowed/blocked placement (collision, slope, floodplain, road, view, NPC nav).
- Option to preview alternative layouts locally without applying them to public world state, episode data, or published website.
- Mobile-friendly observer mode remains uncluttered; technical masterplan overlays are creator-only, not default viewer UI.

## Acceptance criteria for a future implementation PR

- [ ] Existing Episode 1 and Episode 2 snapshots/events replay without geometry/identity drift.
- [ ] Exactly 1 original castle + 3 original homes + 9 selected residents remain canonical after the planning feature; no unapproved new construction.
- [ ] A map audit establishes actual footprint, path, river and terrain coordinates from code, with owner-reviewed screenshots/maps made **manually** by owner.
- [ ] Candidate placement rejects building overlap, river/floodplain conflicts, excessive slope and unreachable entries with understandable reasons.
- [ ] Castle gate-to-world approach and at least one path to each existing house work for NPC navigation, including failure recovery.
- [ ] Editor preview never mutates/publishes canonical state; world viewer and video remain consistent with publication gating.
- [ ] Unit/integration tests validate collision, bank buffer, terrain, road connectivity, deterministic results, migration/replay and no accidental 'preview placement' persistence.
- [ ] 9:16 visual framing and mobile performance reviewed by creator on laptop/phone.
- [ ] Agent runs only approved non-render tests/builds; **creator runs preview, video render and screenshots manually**.
- [ ] No automatic GitHub push/merge, public deploy or world activation.

## Suggested execution stages (requires a later explicit go-ahead)

**Stage A — Audit + visual plan, no code changes to world.** Examine current authoritative branch and document accurate map of assets, coordinates, obstruction and 2–3 layout options. Ask owner to review.

**Stage B — Placement contract + validations.** Propose architecture for zoned placement and test it against castle/3 homes; no new structures.

**Stage C — Creator-only planning UI and roads/landscaping refinements.** Implement only approved changes, with fully reversible plan overlay and regression checks.

**Stage D — Future audience-driven construction.** Once real comments are chosen, locate and build requested facilities within zones, animate them in Remotion, then activate canon at publication.

## Scope boundary

Do not pre-create a marketplace, barracks, smithy, farm, prince/princess, battle, or Episode 3 story. User comments determine what happens next; this plan only ensures that whatever gets selected has a coherent place in the world.
