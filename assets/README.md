# Character Forge - Sprite Asset Guide

This folder contains the layered sprite assets used by Character Forge. Each asset is a grayscale PNG sprite sheet that gets tinted with the user's selected colors.

## Folder Structure

```
assets/
├── bodies/          # Base body types
├── hair/            # Hair styles
├── outfits/         # Clothing/armor
└── accessories/     # Capes, helmets, auras, etc.
```

## Sprite Sheet Format

**All sprite sheets must follow this exact format:**

```
Canvas Size: 1024 x 1536 pixels
Grid: 4 columns x 6 rows
Frame Size: 256 x 256 pixels per frame
Background: Transparent (PNG with alpha)
Color: GRAYSCALE ONLY (will be tinted programmatically)
Direction: Character faces RIGHT
```

### Row Layout (top to bottom)

| Row | Animation | Description |
|-----|-----------|-------------|
| 0 | Idle | Standing still, subtle breathing (4 frames) |
| 1 | Walk | Walking cycle to the right (4 frames) |
| 2 | Ranged Attack | Shooting/casting projectile (4 frames) |
| 3 | Melee Attack | Sword swing or punch (4 frames) |
| 4 | Hurt | Recoiling from damage (4 frames) |
| 5 | Special | Power-up or ability activation (4 frames) |

### Visual Guide

```
┌─────┬─────┬─────┬─────┐
│ I-1 │ I-2 │ I-3 │ I-4 │  Row 0: Idle
├─────┼─────┼─────┼─────┤
│ W-1 │ W-2 │ W-3 │ W-4 │  Row 1: Walk
├─────┼─────┼─────┼─────┤
│ R-1 │ R-2 │ R-3 │ R-4 │  Row 2: Ranged Attack
├─────┼─────┼─────┼─────┤
│ M-1 │ M-2 │ M-3 │ M-4 │  Row 3: Melee Attack
├─────┼─────┼─────┼─────┤
│ H-1 │ H-2 │ H-3 │ H-4 │  Row 4: Hurt
├─────┼─────┼─────┼─────┤
│ S-1 │ S-2 │ S-3 │ S-4 │  Row 5: Special
└─────┴─────┴─────┴─────┘
  256   256   256   256  (pixels)
```

---

## Required Assets

### Bodies (assets/bodies/)

| Filename | Description |
|----------|-------------|
| athletic.png | Standard athletic build |
| slim.png | Thinner, lighter frame |
| bulky.png | Muscular, heavy build |
| petite.png | Smaller, compact frame |

**Notes:**
- Draw the full body silhouette including legs
- Use medium gray (#888888) as the base
- Add lighter gray (#CCCCCC) for highlights
- Add darker gray (#444444) for shadows
- Arms should be at sides for idle, animated for attacks

### Hair (assets/hair/)

| Filename | Description |
|----------|-------------|
| short.png | Short cropped hair |
| long.png | Long flowing hair past shoulders |
| spiky.png | Spiky anime-style hair |
| ponytail.png | Hair tied back in ponytail |
| bald.png | No hair (can be empty/minimal) |
| hooded.png | Hood covering head |

**Notes:**
- Position hair relative to where head would be
- Hair should animate slightly with movement
- Long hair should flow during walk/attack animations

### Outfits (assets/outfits/)

| Filename | Description |
|----------|-------------|
| pajamas.png | Casual sleepwear |
| knight.png | Plate armor with helmet |
| ninja.png | Dark stealth suit |
| army.png | Military fatigues |
| superhero.png | Spandex hero costume |
| robot.png | Mechanical armor |
| wizard.png | Robes and pointed hat |
| casual.png | T-shirt and pants |

**Notes:**
- Outfit covers the body layer
- Use 2-3 distinct gray values for color regions:
  - Light gray (#DDDDDD) = Primary color region
  - Medium gray (#888888) = Secondary color region
  - Dark gray (#333333) = Shadows/details
- Leave skin areas transparent

### Accessories (assets/accessories/)

| Filename | Description |
|----------|-------------|
| none.png | Empty/transparent (required) |
| cape.png | Flowing cape behind character |
| helmet.png | Head armor/helmet |
| aura.png | Glowing energy effect |
| eyepatch.png | Eye patch with strap |
| shoulder_armor.png | Pauldrons on shoulders |

**Notes:**
- Accessories layer on top of everything
- Capes should flow with movement
- Aura effects can use lighter grays for glow

---

## AI Generation Prompts

### For ChatGPT/DALL-E or Midjourney:

```
Create a pixel art sprite sheet for a [LAYER TYPE] in a top-down action game style similar to Vampire Survivors.

SPECIFICATIONS:
- Canvas size: 1024x1536 pixels (4 columns x 6 rows)
- Each frame: 256x256 pixels
- Background: Transparent
- Style: 16-bit pixel art, clean edges, good silhouette
- Color: GRAYSCALE ONLY (white to black, no colors)
- Character should face RIGHT in all frames

ROW LAYOUT (top to bottom):
- Row 1: Idle animation (4 frames) - subtle breathing/movement
- Row 2: Walk cycle (4 frames) - walking to the right
- Row 3: Ranged attack (4 frames) - shooting/casting projectile
- Row 4: Melee attack (4 frames) - sword swing or punch
- Row 5: Hurt/damage (4 frames) - recoiling from hit
- Row 6: Special ability (4 frames) - power-up or special move

LAYER TYPE: [body/hair/outfit/accessory]
SPECIFIC ITEM: [e.g., "knight armor", "spiky hair", "flowing cape"]

Important:
- Keep the character centered in each 256x256 frame
- Maintain consistent proportions across all frames
- Use clear pixel boundaries (no anti-aliasing blur)
- Design as a LAYER that will be composited with other layers
- Use grayscale values for shading (will be recolored in app)
```

### For Gemini (with image generation):

```
Generate a pixel art sprite sheet. Specifications:
- Size: 1024x1536 pixels
- Grid: 4 columns, 6 rows
- Frame size: 256x256 each
- Style: 16-bit retro game sprites like Vampire Survivors
- Colors: GRAYSCALE ONLY (black, white, grays)
- Transparent background

Content: [DESCRIBE THE SPECIFIC LAYER]
- Row 1: Idle stance (4 frames, subtle movement)
- Row 2: Walk cycle (4 frames)
- Row 3: Ranged attack (4 frames)
- Row 4: Melee attack (4 frames)
- Row 5: Taking damage (4 frames)
- Row 6: Special ability (4 frames)

Character faces RIGHT. Clean pixel edges, no blur.
```

---

## Manual Creation Guide

### Using Aseprite, Photoshop, or Pixilart:

1. **Create canvas**: 1024 x 1536 pixels
2. **Enable grid**: View > Grid > 256x256 cells
3. **Set color mode**: Grayscale or limit palette to grays
4. **Draw in layers**:
   - Keep each body part on separate layers
   - Export combined as single PNG

### Grayscale Palette:

```
#FFFFFF - Pure white (highlights, glow effects)
#DDDDDD - Light gray (primary color region)
#AAAAAA - Medium-light gray (secondary highlights)
#888888 - Medium gray (base/neutral)
#555555 - Medium-dark gray (secondary shadows)
#333333 - Dark gray (shadows, outlines)
#000000 - Pure black (deep shadows, outlines)
```

### Tips:

1. **Consistency**: All layers must have the character in the same position across frames
2. **Centering**: Character should be centered in each 256x256 frame
3. **Animation timing**:
   - Idle: Very subtle movement (1-2 pixel shifts)
   - Walk: Clear 4-step cycle
   - Attacks: Wind-up → Strike → Follow-through → Recovery
4. **Layering order**: Body → Outfit → Hair → Accessories
5. **Transparency**: Use PNG format, ensure background is fully transparent

---

## Testing Your Assets

1. Place your PNG files in the appropriate folders
2. Open Character Forge in your browser
3. Select your new options from the dropdowns
4. The canvas will automatically composite and tint your layers

**Note**: The app currently uses placeholder graphics. Once you add real sprite sheets, update the `layers` object in `index.html` to load them.

---

## Export Formats

When you "Push to Game", Character Forge composites all layers and exports in the target game's format:

### House Survivors Format:
- 1024 x 1024 pixels (4x4 grid)
- Row 0: Walk, Row 1: Shoot, Row 2: Aim Up, Row 3: Idle

### Merge TD Format:
- 512 x 256 pixels (4x2 grid)
- Row 0: Idle, Row 1: Attack
