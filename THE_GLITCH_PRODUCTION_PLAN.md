# "THE GLITCH" - Production Plan

## TOOL STACK

### Image Generation:
**Primary:** Midjourney (via nanobanana or direct)
**Backup:** Flux, DALL-E 3

### Video Generation:
**Primary:** Kling 3.0
**Backup:** Runway Gen-3, Pika

### Upscaling/Enhancement:
**Primary:** Topaz Video AI
**Backup:** Kling's native upscaler, Runway's upscaler

### Editing:
**Primary:** DaVinci Resolve (free)
**Backup:** CapCut (mobile-friendly), Premiere Pro

### VFX:
**Primary:** DaVinci Resolve Fusion
**Backup:** After Effects, CapCut glitch presets

### Sound:
**Music:** Uppbeat, Artlist
**SFX:** Freesound.org, Zapsplat

---

## PRODUCTION WORKFLOW

### PHASE 1: HERO FRAMES (Day 1 Morning, 2-3 hours)

Generate perfect still frames for each shot using **Midjourney/nanobanana**.

#### SHOT 1: "THE REPEAT"
**Midjourney Prompt:**
```
Cinematic martial arts scene, medium shot, modern minimalist white dojo with clean lines and reflective floor, athletic fighter in white tactical training gear in defensive stance looking confused, opponent in black tactical gear throwing a right hook mid-punch, motion blur on punch, hyper-realistic, volumetric lighting from overhead, shot on Arri Alexa, 16mm lens, shallow depth of field, professional color grading, --ar 9:16 --style raw --v 6.1
```

**Reference images to upload:**
- Minimalist Apple Store aesthetic
- Martial arts dojo (clean, modern)
- Action movie fighting stance

**Generate:** 4 variations, pick best

**Critical elements:**
- ✅ Clean white environment
- ✅ Clear body positions
- ✅ Opponent's punch mid-air
- ✅ Protagonist looking slightly confused

---

#### SHOT 2: "THE NOTICE"
**Midjourney Prompt:**
```
Extreme close-up of athletic person's eyes, intense expression, dilated pupils, eyes widening in realization, dramatic lighting, reflection of movement in eyes, cinematic bokeh background, hyper-realistic skin texture, shot on Arri Alexa, 85mm macro lens, shallow depth of field f/1.4, professional color grading with cool cyan tones, --ar 9:16 --style raw --v 6.1
```

**Reference images:**
- Close-up eye shots from films (Blade Runner, The Matrix)

**Generate:** 4 variations, pick most expressive

**Critical elements:**
- ✅ Eyes convey dawning realization
- ✅ Crisp focus on iris/pupil
- ✅ Subtle background (out of focus dojo)

---

#### SHOT 3: "THE TEST"
**Midjourney Prompt:**
```
Wide shot martial arts choreography, modern white minimalist dojo, fighter in white gear perfectly dodging a spinning back kick from opponent in black tactical gear, motion blur on attacker, crystal clear defender, dynamic action pose, volumetric lighting, reflective floor, cinematic composition, shot on Arri Alexa, 24mm lens, professional action movie lighting, --ar 9:16 --style raw --v 6.1
```

**Reference images:**
- John Wick fight choreography stills
- The Raid action scenes
- Matrix dodging sequences

**Generate:** 5 variations (action shots need more options)

**Critical elements:**
- ✅ Clear spatial relationship between fighters
- ✅ Opponent mid-kick (motion blur acceptable)
- ✅ Protagonist perfectly positioned (crisp)

---

#### SHOT 4: "THE COUNTER"
**Midjourney Prompt:**
```
Dynamic martial arts action shot, fighter in white tactical gear delivering a palm strike to opponent's chest, intense impact moment, motion lines, slight motion blur, black-clad opponent reacting to hit, modern white dojo background, dramatic lighting, shot from dynamic angle, cinematic action photography, shot on Arri Alexa with high shutter speed, professional color grading, --ar 9:16 --style raw --v 6.1
```

**Reference images:**
- Impact frames from action films
- Martial arts photography (moment of contact)

**Generate:** 5 variations

**Critical elements:**
- ✅ Clear impact point
- ✅ Energy/force visible
- ✅ Opponent starting to show "glitch" (we'll add in VFX later)

---

#### SHOT 5: "THE BREAK"
**Midjourney Prompt:**
```
Sci-fi glitch scene, opponent frozen mid-air with digital artifacts and scan lines, white minimalist dojo environment dissolving into digital grid, blue neon wireframe overlays, cyberpunk VFX, protagonist in white gear stepping back in shock, cinematic lighting with digital elements, hyper-realistic meets digital art, shot on Arri Alexa, professional color grading, --ar 9:16 --style raw --v 6.1
```

**Reference images:**
- Tron Legacy digital world
- Matrix code effects
- Cyberpunk glitch art

**Generate:** 5 variations (this is the "money shot")

**Critical elements:**
- ✅ Clear transition from physical to digital
- ✅ Opponent dissolving/glitching
- ✅ Protagonist's shocked expression

---

#### SHOT 6: "THE REVEAL"
**Midjourney Prompt:**
```
Cinematic wide shot, athlete in VR haptic suit and headset standing in motion capture lab, removing VR headset, sweaty and exhausted, realistic tech lab environment with blue LED lighting, computer screens showing "AI TRAINING COMPLETE" text, cables and tracking equipment, professional lighting, photorealistic, shot on Arri Alexa, 35mm lens, depth of field, moody color grading, --ar 9:16 --style raw --v 6.1
```

**Reference images:**
- VR motion capture studios (reference Meta, SteamVR setups)
- Tech lab environments
- Haptic suit reference images

**Generate:** 5 variations

**Critical elements:**
- ✅ Clear VR/tech environment (contrast to dojo)
- ✅ Screen visible with text
- ✅ Character exhausted but real

---

### PHASE 2: VIDEO GENERATION WITH KLING 3.0 (Day 1 Afternoon, 6-8 hours)

**Kling 3.0 Settings:**
- Duration: 5 seconds per shot (you'll trim in edit)
- Quality: Professional mode
- Camera movement: Specific per shot (see below)
- Motion intensity: Medium (except where noted)

#### Process per shot:
1. Upload hero frame to Kling 3.0
2. Add motion prompt
3. Generate 3-5 variations
4. Pick best take
5. **Extract last frame** of best take (`ffmpeg -sseof -0.04 -i clip.mp4 -frames:v 1 lastframe.png`)
6. Use extracted last frame as hero frame input for the NEXT shot (creates visual continuity chain)
7. Upscale if needed

**SEE ALSO:** `VIDEO_COHERENCE_GUIDE.md` for detailed transition techniques and the spinning back kick fix

---

#### SHOT 1 Generation:
**Upload:** Hero frame from Midjourney
**Kling Motion Prompt:**
```
Camera locked. Opponent's right hook moves forward toward camera in slow motion, then VIDEO REWINDS 0.5 seconds with slight glitch, then punch comes forward again. Protagonist's body tenses slightly. Minimal background movement. Motion intensity: Medium.
```

**Camera movement:** Locked (no camera movement)
**Duration:** 5 seconds (will trim to 4s)
**Generate:** 3 takes

**What to look for:**
- Smooth rewind effect (Kling's time manipulation)
- Punch trajectory consistent
- No major morphing on faces/hands

---

#### SHOT 2 Generation:
**Upload:** Hero frame (close-up eyes)
**Kling Motion Prompt:**
```
Subtle eye movement, pupils dilate slightly, eyes dart left then right tracking movement, slight blink, shallow breathing visible in iris reflection. Minimal background motion (soft bokeh). Motion intensity: Low (this is a subtle shot).
```

**Camera movement:** Locked, minimal organic shake
**Duration:** 5 seconds (will trim to 4s)
**Generate:** 3 takes

**What to look for:**
- Natural eye movement (not robotic)
- Iris stays in focus
- Emotion reads clearly

---

#### SHOT 3 Generation:

**IMPORTANT: The spinning back kick is the hardest motion for AI video. See `VIDEO_COHERENCE_GUIDE.md` Part 2 for five different strategies. Recommended approach below.**

**Split into 2-3 sub-clips (Strategy A) with dodge-focused prompting (Strategy E):**

**Clip 3A: The Wind-Up (2 seconds)**
**Upload:** Last frame of Shot 2 (or hero frame showing opponent in fighting stance beginning to pivot)
**Kling Motion Prompt:**
```
Camera locked. Opponent in black tactical gear plants front foot and begins to pivot, rotating shoulders away from camera, initiating spinning movement. Fighter in white stays in defensive stance watching. Smooth continuous motion, no morphing or warping on faces or hands. Motion intensity: Medium.
```

**Clip 3B: The Kick & Dodge (2-3 seconds)**
**Upload:** Last frame of Clip 3A (or Midjourney frame showing kick at 3/4 extension point)
**Kling Motion Prompt:**
```
Camera locked, wide shot. Fighter in white gear leans back dramatically in smooth evasive movement, a black boot sweeps past just above their torso with heavy motion blur, protagonist stays crystal clear and composed. White minimalist dojo, dramatic lighting. Smooth continuous motion. Motion intensity: Medium.
```

**Camera movement:** Locked wide
**Duration:** 2-3 seconds per sub-clip
**Generate:** 4-5 takes per sub-clip (action is complex)
**Motion intensity:** Use Medium (not High) -- speed ramp in post for energy

**Fallback:** If the spinning kick fails completely, replace with a side kick or jumping kick. The audience doesn't know the script -- what matters is it looks clean and the dodge looks effortless.

**What to look for:**
- Clean dodge timing
- Spatial relationship maintained between fighters
- Motion blur on attacker's leg, clarity on protagonist
- No limb warping or extra limbs during rotation
- Cut between sub-clips at the peak of the spin to hide the hardest rotation frames

---

#### SHOT 4 Generation:
**Upload:** Hero frame (counter-attack)
**Kling Motion Prompt:**
```
Dynamic camera follows protagonist's rapid palm strike into opponent's chest, contact creates impact frame (1 frame freeze), opponent's body reacts to hit. Camera tracks with protagonist's movement. Motion intensity: High. Slight digital glitch appears on opponent at moment of impact.
```

**Camera movement:** Dynamic tracking (follows protagonist)
**Duration:** 5 seconds (will trim to 5s)
**Generate:** 4 takes

**What to look for:**
- Impact looks powerful
- Camera movement feels intentional (not shaky)
- Glitch effect (if Kling can do it) or add in post

---

#### SHOT 5 Generation:
**Upload:** Hero frame (glitch/break)
**Kling Motion Prompt:**
```
Opponent frozen mid-air, digital scan lines and glitch effects spread across their body and environment, walls flicker and reveal blue digital grid, protagonist steps backward in shock. Heavy VFX, cyberpunk aesthetic. Motion intensity: Medium (protagonist moves, environment glitches).
```

**Camera movement:** Locked, may add subtle zoom in post
**Duration:** 5 seconds (will trim to 5s)
**Generate:** 5 takes (this is the money shot)

**What to look for:**
- Glitch effects look intentional
- Opponent convincingly "frozen"
- Environment transformation clear

**BACKUP PLAN:** If Kling struggles with heavy VFX, generate clean version (frozen opponent) and add ALL glitch effects in post-production using DaVinci Resolve Fusion.

---

#### SHOT 6 Generation:
**Upload:** Hero frame (lab reveal)
**Kling Motion Prompt:**
```
Wide camera pulls back revealing full VR lab environment, protagonist removes VR headset pulling it up and off head, heavy breathing, looks toward computer screen, slight smile, exhausted. Realistic motion, practical lighting, authentic movement. Motion intensity: Medium.
```

**Camera movement:** Slow pullback/reveal
**Duration:** 5 seconds (will trim to 5s)
**Generate:** 4 takes

**What to look for:**
- Natural headset removal motion
- Camera pullback smooth
- Screen text readable (or add in post)

---

### PHASE 3: UPSCALING (Day 1 Evening, 1-2 hours)

**Tool:** Topaz Video AI OR Kling's native upscaler

**Settings:**
- Input: Kling output (likely 720p or 1080p)
- Output: 1080p minimum (4K if possible)
- Enhancement: Artemis HQ model (Topaz) or "Quality" mode (Kling)
- Frame rate: Keep original (24fps or 30fps)

**Process:**
1. Export best take of each shot from Kling
2. Run through Topaz Video AI (batch process all 6)
3. Let it run overnight if needed

---

### PHASE 4: EDITING (Day 2 Morning, 3-4 hours)

**Tool:** DaVinci Resolve (free)

#### EDIT TIMELINE:

**Track 1 (Video):**
- Shot 1: 0:00-0:04 (4 seconds)
- Shot 2: 0:04-0:08 (4 seconds)
- Shot 3: 0:08-0:15 (7 seconds)
- Shot 4: 0:15-0:20 (5 seconds)
- Shot 5: 0:20-0:25 (5 seconds)
- Shot 6: 0:25-0:30 (5 seconds)

**Total:** 30 seconds

#### EDITING STEPS:

1. **Import all upscaled clips**
   - Create bins: "Shot 1", "Shot 2", etc.
   - Import best takes

2. **Assembly edit (30 min)**
   - Drop clips in timeline per beat sheet
   - Rough trim to timing
   - Play through - does pacing feel right?

3. **Fine-tune timing (1 hour)**
   - **Shot 1:** Add rewind effect if Kling didn't do it
     - Duplicate clip at punch moment
     - Reverse 0.5s section
     - Add glitch transition
   - **Shot 2:** Extend if needed for emotion to land
   - **Shot 3:** Cut on action (hide any AI artifacts at cut points)
   - **Shot 4:** Add impact frames
     - Freeze 2 frames on hit
     - Duplicate and offset for "impact flash"
   - **Shot 5:** Build the glitch crescendo
   - **Shot 6:** Time the pullback reveal perfectly

4. **Add transitions (see VIDEO_COHERENCE_GUIDE.md for full details)**
   - Shot 1→2: Hard cut on action (cut when punch is closest to landing) + impact sound on cut
   - Shot 2→3: Hard cut + audio pre-lap (start whoosh 3 frames before visual cut)
   - Shot 3→4: Cut on direction reversal (lean-back → lunge-forward) + speed ramp
   - Shot 4→5: Custom glitch transition (2-frame freeze → RGB split → scan line → digital noise → Shot 5)
   - Shot 5→6: Fade through white overexposure (ramp brightness → cross-dissolve → lab)

---

### PHASE 5: VFX (Day 2 Late Morning, 2 hours)

**Tool:** DaVinci Resolve Fusion (or After Effects)

#### VFX SHOTS:

**Shot 1 - Rewind Effect:**
- Add RGB split on rewind (2 pixels offset)
- Scan line overlay during rewind
- Glitch sound sync point

**Shot 4 - Impact Frames:**
- Add speed ramp (slow-mo right before impact)
- 2-frame freeze on contact
- Optional: radial blur from impact point

**Shot 5 - HEAVY GLITCH (Money Shot):**
- **Layer 1:** Base video (frozen opponent)
- **Layer 2:** Scan lines (horizontal scrolling)
- **Layer 3:** RGB channel split (animate separation)
- **Layer 4:** Digital noise overlay (20% opacity)
- **Layer 5:** Grid floor (blue neon, fade in)
- **Layer 6:** Wireframe overlay on opponent (fade in)
- **Layer 7:** Particle system (opponent dissolving)

**Free VFX assets:**
- Production Crate (glitch overlays)
- FootageCrate (scan lines, digital elements)
- RocketStock (free glitch pack)

**Shot 6 - Screen Text:**
- Create text in Fusion:
  ```
  AI TRAINING COMPLETE
  COMBAT MODEL v3.7
  ACCURACY: 99.8%
  ```
- Font: Courier New or Roboto Mono
- Color: Cyan (#00E5FF)
- Track to screen in shot (corner pin)
- Slight CRT flicker effect

---

### PHASE 6: COLOR GRADING (Day 2 Afternoon, 1 hour)

**Tool:** DaVinci Resolve Color Tab

#### COLOR STRATEGY:

**Shots 1-5 (Dojo):**
1. Primary correction: Expose properly, balance whites
2. Secondary: Cool color temp (5000K)
3. Desaturate slightly (-10%)
4. Increase contrast (lift shadows, push highlights)
5. Add cyan tint to highlights
6. LUT: "Cyberpunk Cool" or custom teal/orange

**Shot 6 (Lab):**
1. Primary correction: Expose properly
2. Warmer color temp (6000K) - "return to reality"
3. Natural saturation
4. Blue LED practical lights (secondary color correction)
5. Slight vignette

**Consistency check:**
- All dojo shots match
- Transition from cool→warm is smooth

---

### PHASE 7: SOUND DESIGN (Day 2 Afternoon, 2-3 hours)

**Tool:** DaVinci Resolve Fairlight (or Audacity free)

#### AUDIO TRACKS:

**Track 1 - Music:**
- Source: Uppbeat or Artlist
- Search: "minimal techno tension" or "cyberpunk ambient"
- Length: Full 30 seconds
- Volume: -12dB (background)

**Track 2 - SFX (Whooshes/Impacts):**
- Shot 1: Punch whoosh
- Shot 3: Kick whoosh x3
- Shot 4: Impact sounds (meaty hit) x3
- Source: Freesound.org, Zapsplat

**Track 3 - Glitch Sounds:**
- Shot 1: Subtle digital artifact (rewind)
- Shot 4: Glitch intensifies on hit
- Shot 5: MASSIVE glitch/bass drop
- Source: Freesound "glitch" tag, or generate with PaulStretch

**Track 4 - Ambience:**
- Shots 1-5: Synthetic room tone (barely audible)
- Shot 6: Lab ambience (computer fans, hum)
- Source: Freesound "lab ambience"

**Track 5 - Breathing/Organic:**
- Shot 2: Single heartbeat thump
- Shot 6: Heavy breathing (protagonist exhausted)
- Source: Record yourself or Freesound

#### MIX LEVELS:
- Music: -12dB
- SFX (impacts): -6dB
- Glitch sounds: -3dB (loudest)
- Ambience: -18dB
- Breathing: -9dB

**Master:** Compress lightly, limit to -1dB (prevent clipping)

---

### PHASE 8: FINAL POLISH (Day 2 Evening, 1 hour)

#### FINAL CHECKLIST:

**Visual:**
- [ ] Add Higgsfield watermark (lower third right)
  - Download from contest page
  - 70% opacity
  - Present throughout all 30 seconds
- [ ] Subtle vignette on all shots (draws eye to center)
- [ ] Film grain overlay (optional, 5% opacity for texture)

**Audio:**
- [ ] Normalized to -14 LUFS (broadcast standard)
- [ ] No clipping/distortion
- [ ] Music fades out smoothly at end

**Technical:**
- [ ] Total runtime: 30 seconds exactly
- [ ] Pacing feels right (not rushed)
- [ ] First 3 seconds are scroll-stopping
- [ ] Ending is satisfying

---

### PHASE 9: EXPORT (Day 2 Evening, 30 min)

**Export Settings:**

**Master File (Contest Submission):**
- Format: MP4 (H.264)
- Resolution: 1920x1080 (16:9) OR 3840x2160 (4K)
- Frame rate: 24fps or 30fps (match source)
- Bitrate: 50 Mbps (high quality)
- Audio: AAC 320kbps stereo

**Social Media - Vertical (TikTok/Reels):**
- Format: MP4 (H.264)
- Resolution: 1080x1920 (9:16)
- Frame rate: 30fps
- Bitrate: 25 Mbps
- Audio: AAC 256kbps stereo

**Social Media - Square (Instagram Feed):**
- Format: MP4
- Resolution: 1080x1080 (1:1)
- Frame rate: 30fps
- Bitrate: 25 Mbps

**Export location:**
```
/Users/uni/higgsfield-contest/exports/
├── the-glitch-master-16x9.mp4
├── the-glitch-vertical-9x16.mp4
└── the-glitch-square-1x1.mp4
```

---

### PHASE 10: DISTRIBUTION (Day 3, 2 hours)

#### POSTING STRATEGY:

**1. Higgsfield Contest (9am)**
- Upload: Master 16:9 file
- Title: "THE GLITCH"
- Description: "A martial artist realizes their opponent is repeating moves—because they're training an AI."

**2. TikTok (6pm same day)**
- Upload: Vertical 9:16
- Caption:
  ```
  POV: You realize you're not the one being trained 🤖

  Created with Midjourney + Kling 3.0 for the @Higgsfield $500k contest

  Which shot was your favorite? 👇

  Full version: [link to Higgsfield]
  #HiggsfieldAction #AIFilm #MartialArts #SciFi #AIart #ShortFilm
  ```
- Cover: Shot 5 (glitch moment)
- Post at 6-8pm (peak engagement)

**3. Instagram Reels (6:15pm same day)**
- Upload: Vertical 9:16
- Caption: (same as TikTok)
- Cover: Shot 5
- Also post to Feed as 1:1

**4. YouTube Shorts (7pm same day)**
- Upload: Vertical 9:16
- Title: "THE GLITCH | AI vs Human Short Film"
- Description: Full credits + tools used

---

## PRODUCTION TIMELINE AT A GLANCE

| Time | Task | Tool | Deliverable |
|------|------|------|-------------|
| **Day 1, 9am-12pm** | Generate hero frames | Midjourney/nanobanana | 6 perfect still images |
| **Day 1, 12pm-2pm** | Lunch + review frames | - | Approved shots |
| **Day 1, 2pm-8pm** | Generate videos | Kling 3.0 | 6 video clips (3-5 takes each) |
| **Day 1, 8pm-10pm** | Upscale best takes | Topaz Video AI | 6 HD clips |
| **Day 1, 10pm** | Let upscaling finish overnight | - | - |
| **Day 2, 9am-10am** | Assembly edit | DaVinci Resolve | Rough cut |
| **Day 2, 10am-12pm** | Fine-tune edit + VFX | DaVinci Resolve | Locked cut with effects |
| **Day 2, 12pm-1pm** | Lunch | - | - |
| **Day 2, 1pm-2pm** | Color grading | DaVinci Resolve | Final look |
| **Day 2, 2pm-5pm** | Sound design + mix | DaVinci Resolve | Complete audio |
| **Day 2, 5pm-6pm** | Final polish + watermark | DaVinci Resolve | Finished video |
| **Day 2, 6pm-7pm** | Export all versions | DaVinci Resolve | 3 files ready to post |
| **Day 3, 9am** | Submit to contest | Higgsfield website | Submitted |
| **Day 3, 6pm** | Post to social media | TikTok, IG, YouTube | Live! |
| **Day 3, 6pm-8pm** | Engage with comments | - | Community building |

---

## BACKUP PLANS

### If Kling 3.0 struggles with complex movements:
- Use Runway Gen-3 (better with consistency)
- Break complex shots into simpler movements
- Add more motion in post (speed ramping, camera push-ins)

### If glitch effects look bad in Kling:
- Generate clean versions
- Add ALL VFX in post (DaVinci Fusion)
- Use free glitch overlay packs

### If timing is too tight:
- Cut Shot 3 to 5 seconds (reduce combo moves)
- Make video 25 seconds instead of 30
- Still effective, less pressure

---

## BUDGET (If needed)

| Item | Cost | Free Alternative |
|------|------|------------------|
| Midjourney | $10/mo | Bing Image Creator (free) |
| Kling 3.0 | ~$30 credits | Pika (has free tier) |
| Topaz Video AI | $299 one-time | Kling upscaler (included) |
| Music (Artlist) | $15/mo | Uppbeat free tier |
| DaVinci Resolve | FREE | - |
| Sound effects | FREE | Freesound.org |
| **Total min:** | **$40-50** | **$0-10 possible** |

---

## READY TO START?

Next step: **Generate Shot 1 hero frame** using Midjourney/nanobanana.

Want me to refine the Midjourney prompts or help you get started with the first shot?
