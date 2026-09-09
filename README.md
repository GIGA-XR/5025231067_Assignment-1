# XR Teardown — What if….? - An immersive Story

**5025231067 — Sinta Probondari Wardani** · S1 Informatics · Individual Assignment 1

|                          |                                                                    |
| ------------------------ | ------------------------------------------------------------------ |
| Subject                  | What if....? - An Immersive Story                                  |
| Publisher / manufacturer | Developed by ILM Immersive (LucasFilm) in collaboration with Marvel|
|                          |   Studios, published via Disney+ as an interactive app.            |
| Release or major update  | May 30, 2024                                                       |
| Platform(s)              | visionOS                                                           |
| How I examined it        | [Hands-on on a lab Quest 3 / documentation and spec sheets / both] |
| Hands-on date(s)         | [when you actually put the headset on, or "documentation only"]    |

> **My claim in one sentence.** [State the argument this teardown defends. Not a summary — a claim someone could disagree with. This is also how you open your 3-minute presentation.]

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

**What I would change:** [One substantiated remedy. Say why it would work, not just that it would be nicer.]

![Caption](assets/fig2.png)

## 3. Use of AI

[Go through the pipeline and report only what you can evidence. Delete the rows you find nothing for — an honest short table beats a padded one.]

| Where                | What it does                                                    | On-device or cloud | Cost it carries                                   | Source + the line I am relying on |
| -------------------- | --------------------------------------------------------------- | ------------------ | ------------------------------------------------- | --------------------------------- |
| Perception           | [hand/body pose, scene mesh, relocalisation]                    |                    | [latency / battery / thermal / network / privacy] | [link] — "[quote the sentence]"   |
| Content              | [text- or image-to-3D, upscaling, texture synthesis]            |                    |                                                   | [link] — "[quote]"                |
| Interaction          | [STT, TTS, LLM agent, translation]                              |                    |                                                   | [link] — "[quote]"                |
| Rendering & delivery | [foveation, frame interpolation, super-resolution, split/cloud] |                    |                                                   | [link] — "[quote]"                |

> Every row needs the **quoted sentence**, not just the link. A claim with a bare URL behind it is an unsupported claim.

[Then the paragraph that actually earns the marks: what is the AI *for* here — is it load-bearing, or is it decoration? If you concluded there is no meaningful AI, this is where you show where you looked and why absence is plausible.]

## 4. Impact

**Intended benefit:** [Concrete enough that someone could check whether it is true.]

**Privacy, security, or ethics:** [Tie this to sensor data the device really captures — hand and body pose, room scans and scene meshes, passthrough camera frames, voice. What is collected, where does it go, and who is exposed — including bystanders who never consented.]

**Accessibility / human factors:** [Who cannot use this, and why? Height, one-handed use, vision, motion sensitivity, cybersickness, language, cost.]

## 5. What I take from this

[Two or three sentences. What does this teardown tell you about where XR design is heading — or where it is stuck? Do not summarise the sections above.]

---

## References

1. [Primary source — developer documentation, specification, technical paper, or your own measurement. At least one of these is required.]
2. [Author/Publisher. (Year). *Title*. URL — accessed DD Mon 2026]
3. [ ]
4. [ ]

## Figure credits

- Fig. 1 — [my own screenshot, Quest 3, 8 Sep 2026 / source and licence]
- Fig. 2 — [ ]
- Fig. 3 — [ ]

## AI-assistance disclosure

**What I used, and for what.** [Name the tools and the tasks — e.g. "Claude to tighten the prose in §2; all sources located and read by me." If you used none, write "None."]

### What I disagreed with my AI assistant about

[One paragraph, and it is marked. Where did the tool tell you something you decided was wrong, shallow, or unsupported — and what did you do instead? Be specific: name the claim, name your reason. If you used no tools, write instead about a source you decided not to trust, and why.]
