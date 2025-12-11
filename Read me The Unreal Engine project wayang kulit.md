# Engineering White Paper — Virtual Wayang Kulit (Unreal Engine)

Version: 1.0  
Author: Rodrigo  
Date: 2025-12-11

1. Executive summary. 

1.1 Purpose  
This white paper documents Experiment 1 of the Virtual Wayang Kulit (shadow-puppet) Unreal Engine project. It records the experiment goal, implementation details, technical constraints encountered, findings, and actionable recommendations to produce a convincing virtual shadow-puppet theatre in Unreal Engine.

1.2 Research question  
Is it possible to convincingly deploy a virtual shadow-puppet environment using procedural calls and Blueprints/Sequencer inside Unreal Engine?

1.3 Key findings (summary)  
- A convincing 2D-style shadow-puppet experience is achievable in UE5.5, but engine constraints (material blend modes, editor primitives, and rigging artifacts) reduce fidelity and complicate workflow.  
- UE5.5 translucent materials do not support specularity, preventing physically accurate back-projection on translucent screens; practical workarounds were used.  
- Quick Add rectangle/plane primitives lack configurable pivots, hindering hinge-style rigging; custom imported plane meshes with explicit pivots are recommended.  
- Inconsistent actor visibility flags across parented parts exist in some levels and pose a risk for unintended scene state.

2. Scope and objectives
2.1 Scope  
Covers Experiment 1 (procedural deployment and animation), implementation notes, level inventory, engineering findings, limitations, and prioritized recommendations.

2.2 Objectives  
- Provide a reproducible record of the experiment and results.  
- Identify constraints and propose engineering remedies.  
- Deliver a short roadmap to improve visual fidelity and robustness.

3. Background and references
3.1 Repository  
Shadow_puppet_Unreal — https://github.com/CHI-CityTech/Shadow_puppet_Unreal

3.2 Relevant engine note  
Epic Games. (2025). Material blend modes in Unreal Engine (UE 5.5) — Translucent: "Translucent materials do not currently support specularity." https://dev.epicgames.com/documentation/en-us/unreal-engine/material-blend-modes-in-unreal-engine?application_version=5.5#translucent

3.3 Zotero and bibliography file  
Create a separate Zotero bibliography file in the repo (ZOTERO_BIBLIOGRAPHY.md). Include initial references in the README and confirm with project lead (David) whether to publish the Zotero group link.

4. Experiment 1 — Setup and approach
4.1 Experimental setup  
- Project: Shadow_puppet_test (Unreal Engine).  
- Puppet construction: hierarchies of StaticMeshActors (thin rectangles/planes) parented to form limbs and body.  
- Animation: Level Blueprint procedural calls (Event BeginPlay driven) used to sequence movement in prototype.  
- Visual approach: intended back-projection onto a translucent screen; fallback used—place puppet in front of the screen and/or duplicate a mirrored actor behind the screen to fake a shadow.

4.2 Execution notes  
- Quick Add rectangles were avoided for pivot reasons on some puppets; custom imported meshes used when pivot control required.  
- Levels vary: some contain both front and back puppet copies; others contain front-only copies with back copies hidden (Visible=False, Actor Hidden In Game=True).

5. Implementation findings
5.1 Asset construction and rigging
5.1.1 Editor primitives and pivots  
- Quick Add rectangles do not allow pivot editing, complicating hinge rotations. Recommendation: author thin single-sided plane meshes in Blender/Maya with explicit pivot points and import them.

5.1.2 Orientation, scale, and normals  
- Editor primitives may import with incorrect orientation/scale. Standardize export/import transforms (apply consistent rotation/scale on export) and verify normals. Prefer single-sided geometry or explicit double-sided materials depending on visual intent.

5.1.3 Perceived thickness and culling artifacts  
- Apparent 2D puppets may retain mesh thickness or backfaces that cause disappearance at certain camera angles. Use single-sided planes with corrected normals or double-sided materials as appropriate.

5.2 Animation and Blueprints
5.2.1 Level Blueprint limitations  
- Using only Event BeginPlay for sequencing produced brittle, non-blended animations. Move animation control to Sequencer, Animation Blueprints, or an explicit state machine for repeatable and blendable playback.

5.2.2 Animation quality  
- Prototype animations are not fully seamless. Improve with keyframe timing, interpolation, Sequencer tracks, or animation montages.

5.3 Rendering and materials
5.3.1 Translucent screen limitation  
- UE5.5 translucency lacks specularity; projection approaches relying on surface reflections will not reproduce realistic back-projected silhouettes.

5.3.2 Workarounds and recommendations  
- Front placement: place puppet on the front surface of a translucent screen to fake a silhouette.  
- Mirrored clone: duplicate the puppet behind the screen (mirrored) to simulate a back-projected shadow — prototype planned but not completed for current milestone.  
- Alternative: use masked or opaque thin-screen materials with tuned lighting for a more convincing result when projection accuracy is required.

6. Level inventory and current state
6.1 ThirdPersonMap (Content/ThirdPerson/Maps)  
- Folder: First_Puppet_Test contains Front_of_princess and Back_of_princess (Back parented to Front). Princess puppet has front and back copies in this level.

6.2 Enclosed_Puppet_show (Content/Levels)  
- Visible: Front_of_prince (older brother) under First_Puppet_Test. Back_of_prince currently Visible=False and Actor Hidden In Game=True (see Outliner → First_Puppet_Test → Front_of_prince → Back_of_prince; check Rendering → Details).

6.3 Rigging_Enclosed_Puppet_show (Content/Levels)  
- Contains latest rigging and animation tests. A small test rectangle StaticMeshActor (Item Label: Rectangle) exists.  
- Front parts of older-brother puppet assembled, scaled, and animated.  
- A separate unused iteration in Do_Not_Use_First_Puppet__Test contains parts with inconsistent visibility and Actor Hidden In Game flags. Leave values unchanged unless using change control and versioned edits.

7. Limitations and risks
7.1 Engine limitations  
- Translucent material specularity limitation prevents realistic translucent projection.  
- Editor Quick Add primitives lack pivot control.

7.2 Project risks  
- Inconsistent actor visibility flags across parented parts may cause hidden assets or unexpected scene state. Mitigate with editor scripting checks and automated tests.

8. Recommendations and next steps
8.1 Short-term (next sprint)
- Replace Quick Add rectangles with custom single-sided plane assets that have explicit pivots.  
- Move animation control to Sequencer or Animation Blueprints; add blending and repeatable playback.  
- Implement and test mirrored clone behind the screen; compare masked/opaque thin-screen materials for fidelity.

8.2 Mid-term
- Rework puppet geometry to single-sided quads with consistent normals; minimize thickness.  
- Add editor automation to validate actor visibility, pivot positions, and hierarchy integrity.  
- Create a simple test harness level that validates front/back puppet visibility toggles and playmode behavior.

8.3 Documentation and provenance
- Add ZOTERO_BIBLIOGRAPHY.md to repo with exported APA entries. Include initial README references to Zotero and ask David if the Zotero group link should be public.

9. Action checklist (appendix)
- [ ] Create and import custom plane mesh with configured pivot.  
- [ ] Re-implement puppet rig per recommended rigging approach.  
- [ ] Migrate animations from Level Blueprint Event BeginPlay to Sequencer/Animation Blueprints.  
- [ ] Implement and test mirrored clone shadow approach and compare material options.  
- [ ] Add Zotero bibliography file and confirm sharing policy with project lead (David).  
- [ ] Add editor automation tests to validate visibility flags and hierarchy integrity.

10. References
CHI-CityTech. (n.d.). Shadow_puppet_Unreal [Repository]. GitHub. https://github.com/CHI-CityTech/Shadow_puppet_Unreal

Epic Games. (2025). Material blend modes in Unreal Engine (UE 5.5) — Translucent. Unreal Engine Documentation. https://dev.epicgames.com/documentation/en-us/unreal-engine/material-blend-modes-in-unreal-engine?application_version=5.5#translucent

11. Notes and provenance
- This document is derived from project notes and the internal "Rigging, animation work using a Blueprint, and animation engineering" document (see that document's Findings and Opinions sections).  
- For rigging and animation specifics, consult Rodrigo's rigging notes and the rigging/animation engineering document referenced in the repo.

12. Contact and review
- Link of Zotero group used for this Shadow puppet Unreal project: https://www.zotero.org/groups/5428036/blendedshadowpuppet.  
- For rigging questions, consult Rodrigo's rigging notes or the rigging/animation engineering document.

--- end of white paper ---