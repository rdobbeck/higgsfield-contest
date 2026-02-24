# Video Coherence & Transition Guide

## THE CORE PROBLEM

AI-generated video clips from tools like Kling 3.0 are each "imagined" independently. They don't share temporal context -- each clip invents its own motion, lighting drift, and spatial logic. This makes them feel disconnected when placed on a timeline, even if the hero frames look consistent.

Below are concrete techniques to fix this, organized from highest-impact to lowest.

---

## PART 1: MAKING CLIPS FEEL LIKE ONE CONTINUOUS SCENE

### 1. Use the Last Frame as the First Frame

The single most effective technique for continuity:

1. Generate Shot 1 video from its hero frame
2. **Extract the last frame** of the Shot 1 video (use `ffmpeg -sseof -0.04 -i shot1.mp4 -frames:v 1 shot1-lastframe.png`)
3. Use that extracted frame as the **hero frame input** for Shot 2's Kling generation
4. Repeat: last frame of Shot 2 becomes input for Shot 3, etc.

This creates a visual chain where each clip's starting pose matches the previous clip's ending pose. Even if the motion inside each clip is AI-generated independently, the *seams* between clips will be seamless.

**When to break the chain:** Shot 2 (eyes close-up) and Shot 6 (lab reveal) are intentional scene changes, so you can use independent hero frames for those. But Shots 1→3→4→5 should ideally chain.

### 2. Match Action Cutting

Hide the transition between clips by cutting on the moment of peak action:

- **Shot 1 → Shot 2:** Cut at the exact moment the punch would land. The eye close-up reads as a reaction cut.
- **Shot 2 → Shot 3:** Cut as the eyes finish their realization dart. The wide shot feels like we "pulled back" to see what they realized.
- **Shot 3 → Shot 4:** Cut during the protagonist's forward movement. If Shot 3 ends with the protagonist leaning back from the kick, and Shot 4 starts with them lunging forward for the palm strike, the reversal of direction creates momentum.
- **Shot 4 → Shot 5:** Cut on the sweep impact. The opponent going down in Shot 4 connects to the opponent frozen mid-air in Shot 5.

**Key rule:** Never cut on a static moment. Always cut when something is moving -- the viewer's eye is tracking the motion and doesn't notice the seam.

### 3. Consistent Color and Exposure

AI video clips often drift in brightness and color temperature across their 5-second duration. Fix this in post:

1. **In DaVinci Resolve Color tab:** Match the *last frame* of each clip to the *first frame* of the next clip
2. Apply a shared LUT or color grade across all dojo shots (Shots 1-5) so they share the same look
3. Use the Scopes (Waveform/Vectorscope) -- don't trust your eyes alone
4. Pay special attention to:
   - White dojo walls (should be the same shade of white in every clip)
   - Skin tone consistency
   - Shadow density (AI clips sometimes make shadows lighter or darker randomly)

### 4. Unified Motion Language

If clips have different "feels" to their motion (one feels floaty, another feels snappy), you can normalize this in post:

- **Speed ramping:** Slow down fast moments and speed up slow moments to create a consistent rhythm
- **Target rhythm:** The dojo shots should all feel like they're shot at the same frame rate. If Shot 1 feels like 24fps real-time and Shot 3 feels like 120fps slow-mo, the viewer will notice
- **Apply the same slight optical flow retiming** to all clips so they share a motion texture

### 5. Sound Design as the Glue

Sound is arguably more important than visuals for coherence. A continuous audio bed makes disconnected clips feel unified:

- **Continuous ambient tone:** A low synthetic hum or dojo room tone that plays under ALL dojo shots (Shots 1-5). This is the #1 audio trick for coherence.
- **Music:** A single music track across the entire 30 seconds forces the brain to perceive one continuous scene
- **Pre-lap audio:** Start the sound effect of the next shot 2-3 frames before the visual cut. Example: the whoosh of the spinning kick starts while we're still on Shot 2 (eye close-up). This bridges the gap.
- **Consistent reverb:** All sound effects should share the same reverb profile (same "room"). Use a convolution reverb of a large empty room for all dojo SFX.

---

## PART 2: THE SPINNING BACK KICK (Shot 3) -- SPECIFIC FIXES

The spinning back kick is the hardest motion to generate with AI video because:

1. **360-degree rotation** -- AI models struggle with rotational body mechanics. Limbs disappear, torsos warp, the rotation axis drifts.
2. **Spatial relationship** -- The kicker needs to maintain a consistent distance from the protagonist throughout the spin, but AI tends to "teleport" characters.
3. **Motion blur ambiguity** -- Heavy motion blur during the spin hides details, and AI fills those blurred areas with nonsense.

### Strategy A: Break It Into Sub-Movements

Instead of generating one 5-second clip of the full spinning back kick, generate it as 2-3 shorter movements and cut between them:

**Clip 3A: The Wind-Up (2 seconds)**
- Hero frame: Opponent in fighting stance, beginning to pivot
- Kling prompt:
```
Camera locked. Opponent in black tactical gear plants front foot and begins to pivot, rotating shoulders away from camera, initiating spinning movement. Fighter in white stays in defensive stance watching. Smooth, realistic martial arts motion. Motion intensity: Medium.
```

**Clip 3B: The Kick Extension (2 seconds)**
- Hero frame: Opponent mid-spin with back leg extending (generate this frame in Midjourney showing the 3/4 rotation point where the kick is extending)
- Kling prompt:
```
Camera locked. Opponent in black completing spinning rotation, back leg extends into powerful kick toward fighter in white who leans backward smoothly avoiding the kick with inches to spare. Motion blur on kicking leg, protagonist stays crystal clear. Realistic martial arts timing. Motion intensity: High.
```

**Clip 3C: The Recovery (1 second)**
- Hero frame: Use last frame of Clip 3B, or generate a frame showing kick fully extended, opponent off-balance
- Kling prompt:
```
Camera locked. Opponent in black completing kick follow-through, leg retracting, slightly off balance. Fighter in white returns to upright stance, composed and confident. Brief pause. Motion intensity: Low.
```

**Cut these together at the action points** (cut on the spin, cut on the kick extension) and the viewer's brain fills in the rotation.

### Strategy B: Cheat the Kick Type

If the spinning back kick just won't generate cleanly, **change it to a visually similar but simpler kick** that AI handles better:

| Original | Replacement | Why It Works Better |
|----------|-------------|-------------------|
| Spinning back kick | **Side kick** | No rotation needed. Opponent just chambers and extends. Looks powerful on camera. |
| Spinning back kick | **Push kick / front kick** | Linear motion only. Very clean in AI generation. |
| Spinning back kick | **Jumping back kick** (without the spin) | The jump adds drama. Linear trajectory. |

The audience won't know the script called for a spinning back kick. What matters is that it *looks good* and the protagonist dodges it.

### Strategy C: Use Motion Blur and Speed Ramping to Hide Problems

If you have a generated spinning kick that's *close but not perfect*:

1. **Add radial motion blur** in DaVinci Resolve/Fusion centered on the opponent during the spin. This hides morphing artifacts.
2. **Speed ramp the spin itself:**
   - Slow before the spin (tension build)
   - Fast during the spin (2x-3x speed -- blur hides artifacts)
   - Slow on the kick extension (clear moment of danger)
   - Normal speed on the dodge
3. **Add camera shake** during the fast spin portion (1-2 pixel random offset). This sells the power of the kick and masks AI weirdness.
4. **Darken the opponent** slightly during the spin with a tracked mask. The contrast between the blurred dark opponent and the crisp light protagonist sells the story.

### Strategy D: Generate From a Different Angle

Side view of a spinning kick requires the AI to track the full 360-degree rotation. Instead:

- **Over-the-shoulder of protagonist:** We see the opponent spinning *toward us*. The kick comes at camera. Less rotation visible = easier for AI.
- **Top-down angle:** Shows the circular motion path clearly. AI handles this better because the rotation is in-plane.
- **Face-on view (opponent facing camera, then spins):** The first 180 degrees are the back turning toward camera (simple), then cut to a new clip showing the kick extending from the side.

### Strategy E: Generate the Dodge, Not the Kick

Flip the priority. Instead of trying to make the kick look perfect, **focus the hero frame and prompt on the protagonist's dodge:**

```
Camera locked, wide shot. Fighter in white gear leans back dramatically in smooth evasive movement, a black boot/leg sweeps past just above their torso with heavy motion blur, protagonist's hair moves from the wind of the near-miss, white minimalist dojo, dramatic lighting. Motion intensity: Medium.
```

This works because:
- The kick is just a blurred leg sweeping through frame (simple for AI)
- The protagonist's lean-back is a straightforward motion (no rotation)
- The *impression* of a powerful kick is sold by the protagonist's reaction and the motion blur

---

## PART 3: SHOT-BY-SHOT TRANSITION PLAN

### Shot 1 → Shot 2 (Punch → Eyes)

**Transition type:** Hard cut on action

**Technique:**
- End Shot 1 on the frame where the punch is closest to landing
- Shot 2 (eye close-up) starts immediately -- reads as "we cut in to see the reaction"
- Add a single **impact sound effect** exactly on the cut point (even though the punch doesn't land, the sound bridges the gap)
- The glitch sound from Shot 1's rewind should still be ringing out into Shot 2 (let it tail off for 0.5s)

### Shot 2 → Shot 3 (Eyes → Wide Dodge)

**Transition type:** Hard cut with audio pre-lap

**Technique:**
- End Shot 2 as the eyes finish darting (the "I understand" moment)
- Start the whoosh sound of the first attack 3 frames BEFORE cutting to Shot 3
- Begin Shot 3 with the opponent already mid-first-attack (don't start from a static pose -- it'll feel like a different scene)
- If there's a spatial mismatch (eye close-up to wide shot), adding a **2-frame white flash** on the cut sells it as an intentional style choice

### Shot 3 → Shot 4 (Dodge → Counter-Attack)

**Transition type:** Cut on action (direction reversal)

**Technique:**
- End Shot 3 with the protagonist having just dodged the final kick -- body leaning away
- Begin Shot 4 with the protagonist lunging *forward* -- the direction reversal creates energy
- **Critical:** Match the protagonist's screen position. If they're on the left in Shot 3, they should be on the left at the start of Shot 4. Flip the Shot 4 clip horizontally if needed.
- Add a speed ramp: slow the last 0.5s of Shot 3 (tension) → instant cut → fast start of Shot 4 (explosion)

### Shot 4 → Shot 5 (Counter → Glitch Break)

**Transition type:** Glitch transition (custom)

**Technique:**
- This is where the "reality breaks" so the transition itself should feel broken
- End Shot 4 on the sweep impact frame
- Apply these layers on the cut:
  1. 2-frame freeze on the impact
  2. RGB channel split (offset R, G, B by 5-10 pixels)
  3. Horizontal scan line wipe (3 frames)
  4. Digital noise burst (2 frames)
  5. Shot 5 begins
- **Sound:** Bass drop + digital corruption sound at the exact moment of the glitch transition
- This glitch transition is INTENTIONAL -- it serves the story, so it won't feel like a lazy edit

### Shot 5 → Shot 6 (Glitch → Lab Reveal)

**Transition type:** Fade through white/overexposure

**Technique:**
- End Shot 5 as the glitch effects reach maximum intensity
- Ramp up the exposure/brightness of Shot 5's last 0.5 seconds until the screen is nearly white
- Cross-dissolve (0.5s) into Shot 6 which starts slightly overexposed and settles to normal
- This reads as "reality resetting" -- we went through the white void between simulation and reality
- **Sound:** All digital sounds cut to silence during the white. Lab ambience fades in as Shot 6 appears.
- **Alternative:** Use a "VR headset removal" POV -- black screen for 3-4 frames (the headset coming off blocks vision), then snap to Shot 6

---

## PART 4: EMERGENCY FIXES IF CLIPS STILL DON'T MATCH

### Fix 1: Regenerate Key Frames

If two adjacent clips refuse to match, regenerate the second clip using the last frame of the first clip as input. This is worth the extra Kling credits.

### Fix 2: Add a Reaction Cutaway

If Shot 3 (kick) doesn't connect to Shot 4 (counter), insert a 1-second cutaway:
- Close-up of protagonist's fist clenching
- Close-up of feet shifting stance
- Over-the-shoulder looking at opponent

This buys you a "scene reset" -- when you cut back to the wide shot, the viewer's spatial memory has been interrupted and they won't notice the mismatch.

### Fix 3: Mask and Composite

If the protagonist looks different between two clips (different pose, different position):
1. Export the last frame of Clip A and first frame of Clip B
2. In Fusion/After Effects, mask the protagonist from Clip B
3. Composite the masked protagonist onto a slightly modified version of Clip A's last frame
4. Use this composited frame as a 2-3 frame transition bridge

### Fix 4: Use Optical Flow Transitions

DaVinci Resolve has an optical flow transition that morphs between two clips. It works best when:
- Both clips have similar framing
- There's movement in both clips
- The transition duration is short (4-8 frames)

Apply it to the cut between problem clips. It's subtle but smooths out spatial jumps.

### Fix 5: Lean Into the Glitch Aesthetic

Your film is literally about a glitch in a simulation. If a transition feels jarring, **add glitch effects to it and it becomes intentional**. A cut that looks like a mistake becomes an artistic choice when you add:
- 2 frames of RGB split
- A quick scan line flash
- A subtle digital noise pop

This is your secret weapon. The story justifies rough transitions as part of the simulation breaking down.

---

## PART 5: KLING 3.0 PROMPT ENGINEERING FOR BETTER CONTINUITY

### Prompt Additions for Consistency

Add these phrases to ALL your Kling prompts to help maintain visual coherence:

```
consistent lighting throughout, no exposure changes, maintain exact spatial positions, smooth continuous motion, no morphing or warping on faces or hands
```

### Prompt Structure That Works Better

Instead of describing the full action, describe **start state → end state**:

```
BAD: "Opponent throws spinning back kick while protagonist dodges"
GOOD: "Starting position: opponent facing right in fighting stance. Ending position: opponent's left leg extended horizontally toward camera at chest height, protagonist leaned back 45 degrees. Smooth transition between positions."
```

Kling handles state-to-state interpolation better than interpreting complex choreography descriptions.

### Motion Intensity Guidelines

For fight scenes, "High" motion intensity often causes more artifacts. Instead:

- Use **Medium** intensity and **speed ramp in post** to add the energy
- The slower the AI generates the motion, the cleaner it looks
- You can always speed up clean footage, but you can't fix warped fast footage

---

## QUICK REFERENCE: SHOT CONNECTION MAP

```
SHOT 1 ──hard cut on action──→ SHOT 2
  (punch lands)                   (eye reaction)

SHOT 2 ──hard cut + audio pre-lap──→ SHOT 3
  (eyes dart)                          (dodge sequence)

SHOT 3 ──cut on direction reversal──→ SHOT 4
  (lean back from kick)                 (lunge forward to strike)

SHOT 4 ──glitch transition──→ SHOT 5
  (sweep impact)                (frozen opponent)

SHOT 5 ──white fade──→ SHOT 6
  (max glitch)           (lab reveal)
```

---

## TOOLS NEEDED

| Technique | Tool | Free? |
|-----------|------|-------|
| Last-frame extraction | ffmpeg (command line) | Yes |
| Color matching | DaVinci Resolve Color tab | Yes |
| Speed ramping | DaVinci Resolve Edit tab | Yes |
| Radial motion blur | DaVinci Resolve Fusion | Yes |
| RGB split / glitch | DaVinci Resolve Fusion | Yes |
| Optical flow transition | DaVinci Resolve | Yes |
| Audio pre-lap | DaVinci Resolve Fairlight | Yes |
| Camera shake | DaVinci Resolve Fusion | Yes |
