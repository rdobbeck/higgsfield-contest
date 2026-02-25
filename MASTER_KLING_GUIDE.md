# THE GLITCH - Master Kling Production Guide

## STEP 0: COMPRESS ALL IMAGES (DO THIS FIRST)

Kling requires images **under 35MB**. Your Midjourney PNGs are likely 50-80MB.

### Option A: Mac Terminal (fastest)
```bash
# Run this for EACH image:
sips -s format jpeg -s formatOptions 80 "input.png" --out "input-compressed.jpg"
```

### Option B: Squoosh.app (browser)
1. Go to squoosh.app
2. Drag image in
3. Set format to JPEG, quality 80%
4. Download -- will be 2-5MB (perfectly fine for Kling)

### Option C: Mac Preview
1. Open image in Preview
2. File > Export
3. Format: JPEG
4. Quality slider: ~80%
5. Save

**Do this for all 7 images before uploading to Kling.**

---

## SHOT ORDER & HERO FRAME MAPPING

| Shot | Name | Hero Frame | Description |
|------|------|-----------|-------------|
| 1 | The Repeat | **Wind-up stance** (both fighters squared up, fists raised) | NEW - replaces old mid-punch frame |
| 2 | The Notice | Eye close-up with reflection | Extreme close-up, realization moment |
| 3 | The Test | High kick from opponent | Wide shot dodge sequence |
| 4 | The Counter | Palm strike impact | Protagonist lands the hit |
| 5 | The Break | Flying kick with cyan energy | Glitch/money shot |
| 6 | The Reveal | VR lab "AI TRAINING COMPLETE" | The twist ending |

---

## SHOT 1: "THE REPEAT" (0:00-0:04)

### Hero Frame
**USE:** The wind-up stance image (both fighters squared up in fighting stances, fists raised, white dojo, nobody has thrown a punch yet)

**WHY THIS FRAME:** Kling needs a clear starting position. If the punch is already mid-swing, Kling doesn't know where the motion started and invents weird movement. Starting from a ready stance gives Kling a clean start → punch animation arc.

### Kling 3.0 Settings
- **Duration:** 5 seconds (trim to 4s in edit)
- **Quality:** Professional mode
- **Camera movement:** Locked (no camera movement)
- **Motion intensity:** Medium

### Kling Motion Prompt
```
Camera locked, static frame. Both fighters face each other in fighting stances. Opponent in black on the right suddenly explodes forward throwing a powerful straight right punch toward fighter in white on the left. Punch extends in slow motion with natural motion blur on the fist. Fighter in white shifts weight backward slightly, eyes widening in surprise and confusion. Smooth realistic martial arts motion, both fighters maintain clean anatomy throughout. No morphing on hands or faces. Motion intensity: Medium.
```

### What to Look For
- **GOOD:** Smooth punch trajectory from stance to extension, clean hands, protagonist's reaction visible
- **REJECT IF:** Punch warps/morphs, extra fingers, fighters drift closer/farther, clothing changes

### Post-Production (DaVinci Resolve)
The rewind effect is added in post -- DO NOT try to get Kling to do it:
1. Find the punch at ~2 second mark
2. Duplicate that 0.5s section
3. Reverse the duplicate (time remap)
4. Add RGB split glitch (2px offset) during the reverse
5. Let the punch play forward again
6. Add scan line overlay on the rewind moment
7. Sync glitch sound effect to the rewind

### Generate
**3-5 takes.** Pick the cleanest punch trajectory.

### Extract Last Frame
```bash
ffmpeg -sseof -0.04 -i shot-1-best.mp4 -frames:v 1 shot-1-lastframe.png
```
Use this as reference for Shot 2 continuity (or just use the eye close-up hero frame).

---

## SHOT 2: "THE NOTICE" (0:04-0:08)

### Hero Frame
**USE:** The extreme close-up of eyes (dark brown eyes, intense expression, fist/movement reflected in iris, cool cyan tones)

### Kling 3.0 Settings
- **Duration:** 5 seconds (trim to 4s in edit)
- **Quality:** Professional mode
- **Camera movement:** Locked, minimal organic shake
- **Motion intensity:** Low

### Kling Motion Prompt
```
Camera locked, extreme close-up on eyes. Subtle eye movement, pupils dilate slightly as realization dawns. Eyes dart left then right, tracking predictable movement pattern. Slight blink midway through. Expression shifts from confusion to understanding. Shallow breathing visible. Background stays soft bokeh, minimal movement. Smooth natural eye motion, no morphing or warping on skin or iris. Motion intensity: Low.
```

### What to Look For
- **GOOD:** Natural eye movement (not robotic), iris stays crisp, emotion reads clearly, subtle pupil dilation
- **REJECT IF:** Eye morphs/warps, skin texture glitches, robotic blinking, iris loses focus

### Generate
**3 takes.** This is a simple shot -- pick the most emotionally expressive one.

---

## SHOT 3: "THE TEST" (0:08-0:15)

### Hero Frame
**USE:** The high kick image (opponent throwing kick, protagonist in defensive stance, white dojo)

### Kling 3.0 Settings
- **Duration:** 5 seconds (trim to ~7s with speed ramping in post)
- **Quality:** Professional mode
- **Camera movement:** Locked wide
- **Motion intensity:** Medium

### Strategy
The spinning/high kick is the HARDEST motion for AI video. Keep the prompt focused on the DODGE, not the kick mechanics.

### Kling Motion Prompt
```
Camera locked, wide shot. Fighter in white on the left leans torso backward in a smooth dramatic evasive movement, dodging cleanly as opponent in black executes a powerful high kick that sweeps past just above the protagonist's chest. Heavy motion blur on the kicking leg, protagonist stays crystal clear and composed with a knowing expression. White minimalist dojo environment, reflective floor. Smooth continuous motion, no warping on limbs. Motion intensity: Medium.
```

### Alternative Prompt (if kick looks bad)
```
Camera locked, wide shot. Opponent in black launches aggressive attack combination from the right, protagonist in white on the left dodges each strike with perfect timing, leaning and weaving with effortless precision, never getting touched. Protagonist appears calm and confident, reading every move before it happens. White minimalist dojo, reflective floor. Smooth martial arts choreography. Motion intensity: Medium.
```

### What to Look For
- **GOOD:** Clean dodge timing, spatial relationship maintained, motion blur on attacker, protagonist sharp
- **REJECT IF:** Limbs warp, extra limbs appear during rotation, fighters merge/overlap

### Generate
**4-5 takes.** Action shots need more options. Pick the one with the cleanest dodge.

---

## SHOT 4: "THE COUNTER" (0:15-0:20)

### Hero Frame
**USE:** The palm strike impact image (protagonist landing strike on opponent, impact particles/energy visible)

### Kling 3.0 Settings
- **Duration:** 5 seconds
- **Quality:** Professional mode
- **Camera movement:** Dynamic tracking (follows protagonist)
- **Motion intensity:** High

### Kling Motion Prompt
```
Dynamic camera follows protagonist in white as he drives forward with a powerful palm strike into opponent's chest. Impact moment creates visible force, opponent's body reacts and staggers backward from the hit. Camera tracks with protagonist's aggressive forward movement. Powerful decisive martial arts strike with realistic body mechanics. Slight dust or particles at point of contact. Motion intensity: High.
```

### What to Look For
- **GOOD:** Impact looks powerful and decisive, camera tracking feels intentional, opponent reacts convincingly
- **REJECT IF:** Palm morphs into opponent's body, camera movement is chaotic, fighters clip through each other

### Post-Production
1. Add speed ramp: slow-mo 0.5s before impact → normal speed on hit
2. Add 2-frame freeze on contact (impact frame)
3. Add subtle radial blur from impact point
4. Add digital glitch on opponent at moment of impact (foreshadows reveal)
5. Sync impact sound effect

### Generate
**4 takes.** Pick the most powerful-looking impact.

---

## SHOT 5: "THE BREAK" (0:20-0:25)

### Hero Frame
**USE:** The flying kick with cyan energy image (opponent mid-air, protagonist stepping back, cyan/teal digital effects visible)

### Kling 3.0 Settings
- **Duration:** 5 seconds
- **Quality:** Professional mode
- **Camera movement:** Locked (add subtle zoom in post)
- **Motion intensity:** Medium

### Kling Motion Prompt
```
Camera locked. Opponent in black frozen mid-air in attack pose, body begins glitching with digital artifacts spreading across their form. Scan lines and distortion ripple outward from opponent. White dojo environment starts flickering and revealing blue digital grid underneath. Protagonist in white steps backward in shock, looking around as reality breaks apart. Cyberpunk digital dissolution effect. Motion intensity: Medium.
```

### Alternative Prompt (clean version, add ALL VFX in post)
```
Camera locked. Opponent in black frozen impossibly mid-air in attack pose, completely still and suspended. Protagonist in white steps backward slowly in shock and disbelief, hands raised, looking at the frozen opponent and then around the room. Surreal stillness, time has stopped for the opponent. White minimalist dojo, subtle blue light beginning to appear. Motion intensity: Low.
```

### What to Look For
- **GOOD:** Opponent convincingly frozen/suspended, protagonist's shocked reaction reads clearly, environment transformation visible
- **REJECT IF:** Opponent moves when they should be frozen, glitch effects look random/ugly

### Post-Production (This is the MONEY SHOT - heavy VFX)
Layer these in DaVinci Resolve Fusion:
1. Base video (frozen opponent)
2. Scan lines overlay (horizontal, scrolling)
3. RGB channel split (animate 2px → 8px separation)
4. Digital noise (20% opacity)
5. Blue neon grid floor (fade in over 2 seconds)
6. Wireframe overlay on opponent (fade in)
7. Particle dissolve on opponent's edges
8. Bass drop sound synced to the glitch peak

### Generate
**5 takes.** This is the thumbnail/money shot. Use the "Alternative Prompt" (clean version) if Kling struggles with VFX -- you'll add better effects in post anyway.

---

## SHOT 6: "THE REVEAL" (0:25-0:30)

### Hero Frame
**USE:** The VR lab image (man in black mocap suit removing VR headset, dark room with blue LEDs, monitors showing "AI TRAINING COMPLETE")

### Kling 3.0 Settings
- **Duration:** 5 seconds
- **Quality:** Professional mode
- **Camera movement:** Slow pullback/reveal
- **Motion intensity:** Medium

### Kling Motion Prompt
```
Camera slowly pulls back revealing full VR motion capture lab environment. Man in black haptic suit reaches up and removes VR headset, pulling it up and off his head with both hands. He is sweating and breathing heavily, exhausted from intense physical effort. He looks toward a computer screen, expression shifting to a slight ambiguous smile. Realistic natural movement, practical blue LED lighting, authentic lab environment. Motion intensity: Medium.
```

### What to Look For
- **GOOD:** Natural headset removal motion, camera pullback smooth, exhausted expression reads, environment stays stable
- **REJECT IF:** Headset morphs/warps during removal, hands clip through headset, camera movement jerky, monitors glitch out

### Post-Production
1. Track "AI TRAINING COMPLETE" text onto monitor screens (corner pin in Fusion)
2. Add subtle CRT flicker to screens
3. Add terminal-style text animation:
   ```
   AI TRAINING COMPLETE
   COMBAT MODEL v3.7
   ACCURACY: 99.8%
   DATASET: 10,000 SPARRING SESSIONS
   ```
4. Font: Roboto Mono, Color: Cyan (#00E5FF)
5. Fade out music, ambient lab sounds fade in
6. Single contemplative piano note at the end

### Generate
**4 takes.** Pick the most natural headset removal with the best facial expression.

---

## KLING UPLOAD CHECKLIST

Before each upload to Kling:

- [ ] Image is JPEG format
- [ ] File size is under 35MB
- [ ] Prompt is copied and ready
- [ ] Settings: Duration 5s, Professional mode
- [ ] Camera movement set correctly for this shot
- [ ] Motion intensity set correctly for this shot

---

## GENERATION ORDER (RECOMMENDED)

Start with the easiest shots to build confidence, then tackle the hard ones:

1. **Shot 2** (Eyes) -- simplest motion, quick win
2. **Shot 6** (VR Lab) -- different environment, independent
3. **Shot 1** (Wind-up → Punch) -- medium difficulty
4. **Shot 4** (Palm Strike) -- medium difficulty
5. **Shot 3** (High Kick Dodge) -- hard, complex motion
6. **Shot 5** (Glitch Break) -- hardest, most VFX

---

## TRANSITION PLAN (for editing)

| Transition | Type | Details |
|-----------|------|---------|
| Shot 1→2 | Hard cut on action | Cut when punch is closest to landing + impact sound |
| Shot 2→3 | Hard cut + audio pre-lap | Start whoosh 3 frames before visual cut |
| Shot 3→4 | Cut on direction reversal | Lean-back → lunge-forward + speed ramp |
| Shot 4→5 | Glitch transition | 2-frame freeze → RGB split → scan line → Shot 5 |
| Shot 5→6 | White flash dissolve | Brightness ramp → cross-dissolve → lab reveal |

---

## FILE NAMING

Save compressed hero frames as:
```
hero-frames/
├── shot-1-windup-compressed.jpg
├── shot-2-eyes-compressed.jpg
├── shot-3-highkick-compressed.jpg
├── shot-4-palmstrike-compressed.jpg
├── shot-5-glitchbreak-compressed.jpg
└── shot-6-vrlab-compressed.jpg
```

Save Kling outputs as:
```
raw-footage/
├── shot-1-take-1.mp4
├── shot-1-take-2.mp4
├── shot-1-take-3.mp4
├── shot-2-take-1.mp4
...etc
```

Save best takes as:
```
best-takes/
├── shot-1-best.mp4
├── shot-2-best.mp4
├── shot-3-best.mp4
├── shot-4-best.mp4
├── shot-5-best.mp4
└── shot-6-best.mp4
```
