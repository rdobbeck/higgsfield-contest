# Shot 1: "The Repeat" - Kling Animation Prompt

## Hero Frame
**File:** `/Users/uni/higgsfield-contest/hero-frames/shot-1-the-repeat.jpeg`

**Description:** Wide shot of white-clad fighter in defensive stance on left, black tactical opponent throwing straight punch from right, minimalist white dojo with geometric doorways.

---

## Kling 3.0 Settings

**Duration:** 5 seconds (will trim to 4s in edit)
**Quality:** Professional mode
**Camera movement:** Locked (no camera movement)
**Motion intensity:** Medium

---

## Motion Prompt (Upload to Kling)

```
Camera locked, static frame. Opponent in black throws straight punch from right side toward fighter in white on left side, punch moves forward in slow motion with motion blur. Fighter in white tenses body slightly, eyes widen in confusion. After 2 seconds, VIDEO REWINDS 0.5 seconds with slight digital glitch effect, then punch comes forward again in exact same trajectory. Minimal background movement. Realistic martial arts motion. Motion intensity: Medium.
```

---

## Alternative Prompt (If rewind doesn't work in Kling)

Generate the punch motion cleanly, then add rewind effect in post-production:

```
Camera locked. Opponent in black tactical gear throws powerful straight punch from right toward fighter in white on left, punch extends forward in slow motion (240fps feel) with natural motion blur, punch stops just before contact. Fighter in white reacts with subtle defensive movement, eyes showing confusion and surprise. Smooth, realistic martial arts choreography. Motion intensity: Medium.
```

**Then in DaVinci Resolve:**
1. Duplicate the punch section at ~2 second mark
2. Time remap to reverse 0.5 seconds
3. Add RGB split glitch effect during rewind
4. Loop punch forward again

---

## What to Look For in Generation

### ✅ GOOD:
- Smooth punch trajectory (no warping/morphing)
- Protagonist's facial expression changes (confusion visible)
- Clean environment (white walls stay white, no artifacts)
- Motion blur looks natural (not excessive)
- Both fighters maintain consistent anatomy (no extra limbs)
- Spatial relationship maintained (distance between fighters consistent)

### ❌ REJECT IF:
- Punch warps/morphs mid-motion
- Protagonist's face becomes distorted
- Environment glitches excessively (unless intentional for rewind)
- Fighters drift closer/farther (spatial inconsistency)
- Clothing/gear changes appearance mid-shot
- Major anatomical issues (fingers melt together, etc.)

---

## Generate Multiple Takes

**Generate at least 3 variations:**
1. First take with rewind prompt
2. Second take with rewind prompt (different seed)
3. Third take with clean punch (no rewind - add in post)

**Pick the best based on:**
- Smoothest motion
- Best facial expression
- Cleanest environment
- Most cinematic feel

---

## Next Steps After Generation

1. **Download best take** from Kling
2. **Save to:** `/Users/uni/higgsfield-contest/raw-footage/shot-1-take-[number].mp4`
3. **Upscale** (if needed): Kling upscaler or Topaz Video AI
4. **Review** timing: Should be ~4 seconds of usable footage
5. **Move to Shot 2** hero frame generation

---

## Technical Notes

- **Frame rate:** Accept whatever Kling outputs (likely 24 or 30fps)
- **Resolution:** Should be 1080p minimum from Kling
- **File size:** Expect 50-200MB per 5-second clip
- **Processing time:** ~5-10 minutes per generation in Kling 3.0
- **Cost:** ~$1-3 per generation (if using credits)

---

## Backup Plan

If Kling 3.0 struggles with this complex rewind motion:

1. **Simplify:** Generate just the forward punch (no rewind)
2. **Add rewind in post:** Much easier to control in DaVinci Resolve
3. **This is actually BETTER:** More control over timing and glitch effect intensity

The rewind is a post-production effect anyway - don't stress if Kling can't do it natively.

---

## Ready to Upload to Kling?

Upload the hero frame + use the "Alternative Prompt" (without rewind) for most predictable results. Add the rewind effect in editing for perfect control.
