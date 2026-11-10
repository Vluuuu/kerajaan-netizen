# DUNIAJOKO.ID — 2D Isometric Public Game Direction

> **Status: USER-APPROVED PRODUCT DIRECTION; ARCHITECTURE/IMPLEMENTATION BACKLOG ONLY.** Confirmed 2026-11-10. Do **not** code, migrate, deploy, generate sprites, or alter the published video/world until separately authorized.
>
> Reference for the *kind of experience*: Clash of Clans-like fixed-angle world map, and the virtual city browsing concept at https://thaloriacity.com. These are references, not permission to copy source, assets, maps, UI or branding.

## Decision

**Video / creator production remains 3D** with Three.js world assets and Remotion cinematic cameras. **Public browser/game experience moves toward a 2D isometric / 2.5D top-down fixed-angle presentation**, built for phones with pan, zoom, tapping buildings, finding citizens and watching the town grow.

The project remains **ONE persistent canonical world**, not one 3D world plus an independently maintained 2D save game. The canonical state owns coordinates, stable entity IDs, buildings, roads, river, zones, citizen identities, positions, actions and events. Different renderers show the same canon.

An existing 3D website MVP can remain a **creator preview/debug viewer** or optional mode, rather than being discarded prematurely. Do not remove its code without approval.

## Product rationale

- Mobile viewers can understand the layout, search for residents, tap points of interest and see settlement activity without manipulating a free 3D camera.
- A dedicated 2D renderer using lightweight sprites and suitable culling **may** reduce GPU load; merely freezing a 3D camera does **not** confer a 2D performance benefit. Benchmark before making performance claims.
- 3D assets can remain the source for consistent visual identity, while offline-derived isometric sprites/atlases can supply a compact 2D view.
- Watchers should recognize the same castle, 3 historic houses and 9 real selected citizens from videos.

## Separation of responsibilities

**Canonical domain state**
- One spatial coordinate convention, stable IDs and versioned world snapshots/events.
- Entity transforms and placement rules from `docs/09-spatial-masterplan-backlog.md`.
- Selected user comments and resident identity mappings; follower counts are **Calon Warga**, never automatically simulated citizen NPCs.
- Publication gates: world events for a newly published episode activate only when owner explicitly triggers them, not when viewers open the website.
- NPC simulation (where implemented) runs in world coordinates and is renderer independent, not per-device 2D behavior.

**Video 3D**
- Three.js mesh builders, camera rigs, Joko acting, cinematic construction and Remotion timeline.
- Record/lock snapshots for reproducible published episodes.

**Game 2D/isometric**
- Converts shared world positions to projected isometric screen coordinates (one authoritative projection transform).
- Fixed/limited viewing angles, pan & zoom/touch, picking, depth sorting and occlusion of sprites, adaptive labels and screen-space UI.
- Tappable castle/homes/citizens, citizen search, simple profile/activity cards, construction and history detail; preserve distinctions between *live* and *historical/pending* state.
- Character visuals can be authored as 4- or 8-direction animation atlases as needed; do not promise animation scope before a prototype.

## Rendering approach (OPEN — evaluate before coding)

- **Option A — Real 2D renderer with isometric sprites** generated/offline from the existing 3D assets, with consistent pixel scale, shadow, camera pitch/azimuth and palette. Potentially best for mobile after benchmarking; requires an asset pipeline for building/character variants and animation directions.
- **Option B — Three.js orthographic isometric camera**, initially reusing existing geometry, to prototype interactions quickly; remains a **3D GPU renderer**, so do not call it a true 2D performance solution.
- **Option C — Hybrid**: terrain/large structures as pre-rendered chunks plus 2D sprites/animated citizens, if interactive layering/occlusion and memory constraints justify.

**No renderer library, sprite workflow, export command or hosting change is approved yet.** Assess bundle size, device compatibility, performance, asset pipeline complexity, scene coherence and migration cost from current code.

## Visual identity

- Fantasy medieval low-poly/isometric style consistent with DUNIAJOKO.ID 3D videos, **not a new pixel-art brand** unless approved later.
- Castle remains the main landmark; three Episode 2 houses remain historical **Kampung Pelopor**, with the logical zoning and clear main-gate/forecourt corridors planned in spatial masterplan.
- Isometric game map must reflect the actual terrain, river, roads, architecture and relative placement, not a manually composed unrelated poster or a second map.
- Avoid overcrowded HUD and unreadable username labels. Labels are context-aware (selected/focused NPC first).
- Buildings not yet selected through real comments are not placed in canonical game view; creator-only planning overlays are not public world objects.

## Public MVP experience (PROPOSED)

1. Load **current published canonical world state** (at this writing, Episode 2 has been published; verify runtime activation before public deployment).
2. Isometric view of existing castle, river, trees, Kampung Pelopor (3 houses), and 9 official citizen NPCs, with appropriate simple motion if already simulated.
3. Mouse/touch drag to pan, pinch/wheel zoom, reset camera and navigate to landmarks.
4. Tap NPC or building -> show username/role if known, housing, activity and relevant canon history/comments; do not invent occupation or private information.
5. Search by official display username (with stable IDs behind the UI), not all social-media followers.
6. Optional community/episode info panel with link to published videos, no fabricated follower metric.
7. Mobile loading progress, WebGL/canvas fallback where relevant, graceful behavior under low resources.

Not part of this MVP: multiplayer, controlling citizens directly, server-side live simulation at scale, economy, voting, NPC generative AI, pay-to-play, user registration or auto-onboarding.

## Safe delivery workflow (NOT STARTED)

**Stage 0 — Reality check and architecture review**
- Audit latest **local** Claude Code branch, because public GitHub documentation branch may not include Episode 1/2 and website implementation. Resolve current canon snapshots and active release gating before touching renderer.
- Identify integration seams in `src/world/`, `src/scene/`, `src/web/` and Remotion code. Compare rendering Options A/B/C with a technical recommendation and risks. Review current spatial masterplan.
- Confirm isometric orientation and art direction using quick, owner-reviewed mockups; do not silently migrate the world.

**Stage 1 — Tiny isolated prototype (requires explicit go-ahead)**
- Try one castle, three existing houses, river segment and 1–9 citizens from real shared snapshot with proper isometric transform, pan/zoom/pick.
- Benchmark on a mid-range phone and laptop. Measure FPS, loaded bytes, memory and draw workload vs existing 3D website. Avoid promising improved performance before results.
- Keep the 3D website and Remotion preview intact during experimentation.

**Stage 2 — Game MVP (requires approval)**
- Optimize interaction, sprite/atlas consistency, citizen labels, indexing/search and touch UI, integrate publication events, accessible loading/error handling.
- Add regression tests for coordinate mapping, ID consistency, event activation, occlusion/depth sort, picking accuracy and no cross-renderer world-state drift.

**Stage 3 — Public release (separately authorized)**
- Owner performs previews/renders, signs off visually, tests mobile interactions and approves deployment. Do not deploy automatically.

## Engineering acceptance tests for future changes

- 3D video and isometric browser map read **the same world IDs/coordinates/event history** and agree on the count/location of castle, houses and selected citizens.
- One fixed coordinate/projection mapping with correct depth sorting, hidden object handling and hit targets.
- Accurate nameplate visibility and touch targets on narrow phones.
- No change to Episode 1/2 already published snapshots or geometry locations.
- All sprite/atlas assets versioned/reproducible; no accidental copyright/IP appropriation from visual references.
- Load, interaction and FPS measured on real devices; graceful fallback and safe disposal of graphics resources.
- **Manual-only visual preview, screenshot, video rendering and deployment by project owner.** AI agent may run approved non-render automated checks only.
- No automatic GitHub push, merge or public deployment.

## Relationship to existing decisions

- Supersedes the **website renderer** portion of original D-002/D-019 (previously described as a single 3D world for both website and video) **but retains the shared single canonical world**.
- Retains the Three.js/Remotion 3D production workflow, creator/narrator Joko, selected citizen NPC identities, audience-comment-driven events and the spatial masterplan.
- This decision is **product direction, not an implementation go-ahead**.
