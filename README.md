# XR Teardown — What if….? - An immersive Story

**5025231067 — Sinta Probondari Wardani** · S1 Informatics · Individual Assignment 1

|                          |                                                                    |
| ------------------------ | ------------------------------------------------------------------ |
| Subject                  | What if....? - An Immersive Story                                  |
| Publisher / manufacturer | Developed by ILM Immersive (LucasFilm) in collaboration with Marvel|
|                          |   Studios, published via Disney+ as an interactive app.            |
| Release or major update  | May 30, 2024                                                       |
| Platform(s)              | visionOS                                                           |
| How I examined it        | Documentation |
| Hands-on date(s)         | 9 September 2026    |

> **My claim in one sentence.** What If...? – An Immersive Story proves that spatial narrative can achieve AAA cinematic presence, but relying exclusively on unassisted hand gestures and eye tracking creates an ergonomic bottleneck that limits high-speed combat gameplay.

---

## 1. Device class

What if....? - An Immersive Story targets an optical-passthrough standalone spatial computer, specifically the Apple Vision Pro (visionOS). The physical device features twin micro-OLED panels delivering 23 million pixels across both eyes, powered by a dual-chip architecture (M2 for system compute and R1 for low-latency sensor processing).

The application spans a dynamic segment of Milgram's Reality-Virtuality Continuum. It begins in Mixed Reality (MR) via video passthrough, where the local physical room geometry is scanned and integrated into the scene. Mystic portals and narrative characters anchor relative to real-world surface planes (tables, floors, and walls). During interactive combat sequences, the experience smoothly scaled transparency toward Virtual Reality (VR), fully occluding the pass-through feed with rendered 3D environments like the Astra plane or the cosmic Multiverse realms.

What this class forces on the design:

**1. Vergence-Accommodation Conflict (VAC) Constraints:** Because the display focal distance is fixed (around 1.3 meters), interactive UI and magical spell runes cannot be placed too close to the user's face without causing severe eye strain. Spells must be projected outward into the room space.

**2. Thermal & Power Budgets**: Running real-time stereoscopic rendering alongside 12-camera optical sensor fusion limits sustained high-polygon mesh rendering. To compensate, the developers rely on stylized cel-shaded shaders mirroring the animated Disney+ series rather than photorealistic ray tracing.

**3. Sensor Field-of-View (FoV) Bounds**: Interaction mechanics depend on the lower-facing cameras detecting the user's hands. Dropping hands below the lap causes tracking loss, requiring explicit user prompt feedback.

![Caption that makes a point, not "screenshot of the app"](assets/fig1.png)

> **One of your three figures must be your own** — a photo or capture of your own hands-on session on a lab headset, or your own measurement, with a visible date. Mark it clearly in the figure credits below.

## 2. Input modality

**What the user does:** The application relies on a controller-free spatial input schema: a combination of foveated eye-gaze selection and skeletal hand-tracking micro/macro gestures.

- Primary Targeting: The user's eye-gaze position acts as the primary cursor ray. Looking directly at an enemy, a narrative choice, or an interactive spell target selects it.

- Spell Activation & Kinematics: To cast mystic spells, the user performs macro hand gestures like crossing wrists, forming circular gestures, or thrusting open palms forward.


**Why this and not that:** The developers chose a controller-free input system over standard 6DoF spatial motion controllers.

- What it bought: Eliminating hardware controllers removes friction for non-gamer audiences, matches the media-first identity of the Apply Vision Pro platform, and allows organic physical pose transformations (like crossing wrists to cast a shiel or thrusting open palms forward) that mirror the superhero power fantasy from the What If...? series without holding plastic grips.
- What it gave up: the design completely sacrifices physical haptic feedback, deterministic button clicks, and zero-latency tracking. In fast combat, players lose the tactile confirmation of blocking an attack or firing an energy beam, relying entirely on visual particle effects and spatial audio.

**Where it fails:** This can be broken down across three distinct failure modes:
- Self-Occlusion during Kinematics Gestures: Doctor Strange-style spell casting requires crossing wrists or holding hands in complex layered geometry. When one hand presses directly in front of another, the Vision Pro's downward-facing tracking cameras lose line-of-sight on the rear fingers, causing joint tracking to drop or freeze mid-cast.
- "Midas Touch" & Saccadic Fatigue: Forcing-eye tacking to serve as a continuous spatial aiming reticle during combat created severe ocular fatigue. Because human eyes make involuntary jumpy movements, precision aiming at moving multiversal targets causes twitcy targeting and unintended activations.
- Camera Field-of-View Boundaries & Arm Fatigue: If a player lowers their hands into their lap while sitting or moves their arms too quickly during combat, the hands drop out of tracking volume, causing gestures to fail. Conversely, forcing extended mid-air macro gestures leads directly to "gorilla arm" physical fatigue within 15-20 minutes.

**What I would change:** I would implement *Magnetic Gaze-Target Auto-Snapping paired with Low-Amplitude Micro-Gesticulation**. The reason as to why I think this would work is because instead of requiring point-exact gaze vector alignment during rapid combat, eye tracking should define a forgiving 5-degree target region that auto-snaps to the nearest enemy or portal slot. Simultaneously, macro full-arm motions (like wide circular portal sweeps) should be mapped to small, low-effort micro-gestures (such as index-thumb pinches with subtle wrist rotation) executed down in the lap. This preserves high tracking stability by keeping hands within the primary camera cone, mitigates arm fatigue, and eliminates ocular strain caused by aggressive eye aiming.

![Caption](assets/fig2.png)

## 3. Use of AI

[Go through the pipeline and report only what you can evidence. Delete the rows you find nothing for — an honest short table beats a padded one.]

| Where                | What it does                                                    | On-device or cloud |  Source + the line I am relying on |
| -------------------- | --------------------------------------------------------------- | ------------------ |  --------------------------------- |
| Perception           | Real-time skeletal hand pose estimation & 3D finger joint tracking                    | On-Device (Apple R1 Chip / Neural Engine)                    | [https://www.youtube.com/watch?v=lLk-IkPktMo] — "Fans will use their hands and eyes to interact with the world around them, becoming immersed with vivid visuals and spatial audio"   |
| Perception           | Room geometry reconstruction & spatial surface mesh generation via LiDAR processing                               | On-Device (Apple Neural Engine)                    | [https://thewaltdisneycompany.com/news/marvel-ilm-apple-vision-pro-immersive-what-if/] — "Transforms the space around them as they traverse across realms"                |
| Rendering & delivery | Eye-tracked foveated rendering (dynamically lowering render resolution in peripheral vision) | On-Device (Apple M2 GPU / R1 Core)                    | [https://apps.apple.com/us/app/what-if-an-immersive-story/id6479251303] — "Cast dynamic spells, defend your allies, and battle against villains using custom hand gestures and eye gaze."                |

> Every row needs the **quoted sentence**, not just the link. A claim with a bare URL behind it is an unsupported claim.

[Then the paragraph that actually earns the marks: what is the AI *for* here — is it load-bearing, or is it decoration? If you concluded there is no meaningful AI, this is where you show where you looked and why absence is plausible.]

## 4. Impact

**Intended benefit:** It demonstrates a production blueprint for AAA narrative transmedia, providing that linear cinematic content (Disney+ series) can be converted into interactive spatial computing where the audience transitions from passive viewers to active first-person participants.

**Privacy, security, or ethics:** The app relies on visionOS sandboxing. Raw camera feeds and raw eye-tracking vectors are never accessible to the Disney / ILM application layer. Only abstract events are passed to the application. As confirmed in the official App Store disclosure: "Data Not Collected: The developer does not collect any data from this app."

**Accessibility / human factors:** This app relies on the dual-hand physical mobility and unassisted vertical posture so users with severe motor impairments, upper-limb amputations, or restricted arm movement cannot execute macro gestures like crossing wrists or drawing wide circles in the air. Furthermore, the absence of alternative input remapping (such as single-switch or dwell-based selection alternative) created an accessibility barrier for motor impaired players.

## 5. What I take from this

What If…? – An Immersive Story shows that while XR can now deliver movie-quality visuals right in our living rooms, its controls are still holding it back. It proves that using just your eyes and hands works great for simple menus, but quickly becomes tiring and inaccurate during intense superhero combat. Overall, spatial storytelling is making huge leaps forward, but we are still stuck trying to make controller-free actions feel as precise and comfortable as traditional gaming.

---

## References

1. Apple Inc. (2024). Apple Vision Pro Technical Specifications & visionOS Architecture. Apple Developer Documentation. [https://developer.apple.com/visionos/]
2. Marvel Studios & ILM Immersive. (2024). Marvel Studios and ILM Immersive Announce "What If…? – An Immersive Story". Marvel.com Newsroom. [https://www.marvel.com/articles/culture-lifestyle/marvel-studios-ilm-immersive-what-if-an-immersive-story-apple-vision-pro-exclusive]
3. Lang, Ben. (2024). Vision Pro and Quest 3 Hand-tracking Latency Compared. Road to VR. [https://www.roadtovr.com/apple-vision-pro-meta-quest-3-hand-tracking-latency-comparison/]
4. Milgram, Paul & Kishino, Fumio. (1994). A Taxonomy of Mixed Reality Visual Displays. IEICE Transactions on Information and Systems, E77-D(12), 1321–1329. [https://www.researchgate.net/publication/220267562_A_Taxonomy_of_Mixed_Reality_Visual_Displays]

## Figure credits

- Fig. 1 — [my own screenshot, Quest 3, 8 Sep 2026 / source and licence]
- Fig. 2 — [ ]
- Fig. 3 — [ ]

## AI-assistance disclosure

**What I used, and for what.** Gemini was used to help me find sources for this assignment.


During our initial discussion, the AI assistant claimed that What If…? – An Immersive Story used cloud-based Generative AI and LLMs to create real-time, changing dialogue for characters like Wong and The Watcher. I rejected this claim because it was completely made up. After checking the official ILM Immersive press releases and the Apple App Store details, I confirmed that all character lines and story choices are actually pre-recorded 3D videos running on simple, fixed script trees. Instead of using the AI's incorrect claim, I reframed the analysis to focus on where machine learning is actually used in the app: running locally on the headset's Neural Engine to track hand movements and map room walls in real time.
