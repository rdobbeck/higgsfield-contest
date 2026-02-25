# Shot 3: "THE TEST" - Updated Hero Frame Prompts

Shot 3 is split into two sub-clips to handle the spinning back kick. Each sub-clip needs its own hero frame.

**Character Reference:**
- Protagonist: Asian male, short dark hair, athletic build, clean-shaven, white compression shirt + white tactical pants with black belt
- Opponent: Black tactical gear with helmet/mask (face obscured)
- Environment: Ultra-minimalist white dojo, geometric doorways, glossy reflective floor

---

## FRAME 3A: "THE WIND-UP" (Opponent Begins to Pivot)

This frame captures the moment just before the spin -- the opponent has planted their front foot and is beginning to rotate. The protagonist is reading the telegraphed move.

### Primary Prompt (Copy/Paste to Midjourney):

```
cinematic wide shot martial arts sparring, ultra minimalist white dojo with geometric doorways and glossy reflective floor, opponent in full black tactical gear with helmet planting front foot and beginning hip rotation to the left with shoulders turning away, early phase of spinning kick wind-up, weight shifting onto front leg, athletic Asian male in white compression shirt and tactical pants standing in relaxed defensive stance on the left side watching opponent's movement with knowing expression, spatial gap between fighters, volumetric overhead lighting, low camera angle emphasizing power, shot on ARRI Alexa 65 with Zeiss Supreme Prime 24mm lens, professional action movie cinematography, desaturated color grading with cyan highlights, photorealistic 8K --ar 9:16 --style raw --v 6.1 --q 2
```

### Alternative (If pivot pose is unclear):

```
wide angle martial arts scene in sleek white minimalist training facility with geometric architecture and reflective floor, fighter in black tactical gear and helmet mid-pivot with back partially turned toward camera initiating a spinning technique, weight on front foot, rear foot beginning to lift, Asian male fighter in white compression shirt and tactical pants standing at distance in calm defensive ready position watching the opponent, clear spatial separation between fighters, professional overhead volumetric lighting, cinematic composition with both full bodies visible, desaturated cool color grading, photorealistic, shot on ARRI Alexa 65 24mm lens --ar 9:16 --style raw --v 6.1 --q 2
```

### What You're Looking For:
- ✅ Opponent clearly beginning a rotation (shoulders turning, hips pivoting)
- ✅ Protagonist calm and reading the move (not reacting yet)
- ✅ Full bodies visible in wide shot
- ✅ Clear spatial gap (they need room for the kick to travel)
- ✅ Same white dojo, same outfits, same lighting as Shot 1
- ❌ Reject if: opponent looks static/standing still, protagonist is too close, weird limb positions

### Save as: `shot-3a-windup.jpeg`

---

## FRAME 3B: "THE DODGE" (Kick Extended, Protagonist Leaning Back)

This is the hero frame for the key moment -- the opponent's leg is fully extended at chest height, and the protagonist has leaned back just enough to avoid it. This is the frame that sells the entire shot.

### Primary Prompt (Copy/Paste to Midjourney):

```
cinematic wide shot martial arts dodge moment, ultra minimalist white dojo with geometric doorways and glossy reflective floor, opponent in full black tactical gear with helmet executing powerful spinning back kick with rear leg fully extended horizontally at chest height, heavy motion blur on kicking leg, athletic Asian male in white compression shirt and tactical pants leaning torso backward narrowly avoiding the kick with inches to spare, protagonist crystal clear and in sharp focus while attacker has motion blur, dynamic tension between fighters, the kick sweeping just past the protagonist's chest, volumetric overhead lighting with dramatic shadows, low camera angle, shot on ARRI Alexa 65 with Zeiss Supreme Prime 24mm lens, professional action movie cinematography like John Wick, desaturated color grading with cyan highlights, photorealistic 8K --ar 9:16 --style raw --v 6.1 --q 2
```

### Alternative A (Focus on the dodge, simplify the kick):

```
cinematic wide shot martial arts evasion, sleek white minimalist dojo with geometric architecture and reflective floor, athletic Asian male in white compression shirt and tactical pants leaning his upper body backward in a smooth fluid dodge, calm confident expression, a black tactical boot with heavy motion blur sweeping horizontally past his chest at close range, near-miss moment, protagonist perfectly crisp and in focus, attacker's extended leg blurred from speed, clear spatial relationship showing the narrow gap between kick and body, volumetric overhead lighting, professional action cinematography, shot on ARRI Alexa 65 24mm wide lens, desaturated cool color grading with cyan accents, photorealistic 8K --ar 9:16 --style raw --v 6.1 --q 2
```

### Alternative B (Side kick instead of spinning -- use if spinning kick keeps looking wrong):

```
cinematic wide shot martial arts dodge, ultra minimalist white dojo with geometric doorways and glossy reflective floor, opponent in full black tactical gear executing powerful side kick with leg extended horizontally toward protagonist at chest height, heavy motion blur on kicking leg, athletic Asian male in white compression shirt and tactical pants leaning backward gracefully avoiding the kick by inches, protagonist sharp and in focus with composed expression, attacker blurred from speed, dramatic near-miss moment, volumetric overhead lighting, low angle cinematic composition, shot on ARRI Alexa 65 with 24mm lens, professional action movie lighting, desaturated color grading with cyan highlights, photorealistic 8K --ar 9:16 --style raw --v 6.1 --q 2
```

### What You're Looking For:
- ✅ Protagonist leaning back with clear "near miss" gap visible between kick and body
- ✅ Protagonist SHARP and in focus, opponent's kick has motion blur
- ✅ Kick at chest height (not head, not legs -- chest sells the danger without looking impossible)
- ✅ Full bodies visible
- ✅ Protagonist's expression is calm/confident (not scared -- he KNOWS this move is coming)
- ✅ Same white dojo environment
- ❌ Reject if: kick makes contact, protagonist looks panicked, limbs are distorted, spatial relationship is unclear

### Save as: `shot-3b-dodge.jpeg`

---

## GENERATION ORDER

1. **Generate Frame 3B first** (the dodge) -- this is the more important frame and the harder one to get right. Get this locked before spending time on 3A.
2. **Generate Frame 3A second** (the wind-up) -- this is simpler and more forgiving.
3. Generate 5+ variations of each -- action poses need more options.

## CHARACTER CONSISTENCY

Add to all prompts if the face drifts from Shot 1:
```
--cref [URL of shot-1-the-repeat.jpeg] --cw 75
```

## DECISION POINT: SPINNING VS. SIDE KICK

After generating 5 variations of Frame 3B Primary Prompt:
- If 2+ variations have a clean spinning kick → use spinning kick
- If all variations look distorted → switch to Alternative B (side kick)
- The side kick reads just as powerfully on screen and is much easier for both Midjourney and Kling to handle

## WHAT HAPPENS NEXT

Once you have both hero frames:
1. Upload Frame 3A → Kling 3.0 with the wind-up motion prompt from the production plan
2. Extract last frame of the 3A video clip
3. Upload that last frame (NOT Frame 3B) → Kling 3.0 with the dodge motion prompt
4. This chaining ensures the two sub-clips connect seamlessly
5. Cut them together at the peak of the spin
