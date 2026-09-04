# TradeUp: Visual Asset Guidelines

**Version:** 2.1 | **Purpose:** Visual consistency & production standards | **Last Updated:** 04.09.2026

---

## 🎯 Design Philosophy

TradeUp's visual presentation balances **market realism** with **premium game feel**. Assets should feel:

- **Okunabilir (Readable):** Details matter; photos should be clear enough to spot defects
- **Premium fakat Neutral:** Market, not casino. Calm colors, no flashy hype
- **Gerçek Pazara Yakın:** Ürün fotoları gerçekçi; ikon ve UI oyun estetik
- **Tek Elle Mobil:** Thumb-friendly, no tiny details that need zoom

---

## 📐 Asset Specifications

### Product Images

**Primary Product Cards**

- **Format:** PNG with transparency (RGBA)
- **Resolution:** 512×512 px (master) → 256×256 px (game use)
- **Background:** Transparent (#00000000)
- **Subject Placement:** Centered, 80% of canvas
- **Perspective:** 3/4 front view or direct front (depends on category)
- **Lighting:** Soft, no harsh shadows; suggests condition without distraction

**Thumbnails**

- **Format:** PNG with transparency
- **Resolution:** 128×128 px
- **Simplification:** Key visual only; details removed for clarity

**Variant Visuals**

When a family has variants (e.g., phone "flagship" vs "midrange"):

- Flagship: Premium finish, higher-end materials visible
- Midrange: Standard finish, clean but less premium
- Budget: Budget finish, practical appearance
- Differences should be visual (material, color tone), not just a label

### Examples

**Smartphones:**
- Flagship: Glossy bezel, premium frame, sharp display edge
- Midrange: Matte back, plastic-looking frame, slightly softer edges
- Budget: Minimal branding, durable-looking plastic

**Luxury Watches:**
- Swiss Automatic: Refined dial, visible brand, metal bracelet
- Dress Watch: Sleek, minimal dial, elegant proportions
- Sports Watch: Rugged numerals, visible tachymeter, sporty strap

---

## 🎨 Color & Theme Integration

### Standard Theme (Free)

**Primary palette:**
- Primary Blue: `#2563eb`
- Neutral Gray: `#64748b`
- Success Green: `#16a34a`
- Warning Orange: `#ea580c`
- Danger Red: `#dc2626`

**Product images:** True-to-life colors (no color grading to theme)
**UI elements (icons, overlays):** Use theme colors

### Night Market Theme (₺39.99)

**Primary palette:**
- Warm Amber: `#fbbf24`
- Deep Gray: `#1e293b`
- Mint Green: `#34d399`
- Soft Orange: `#fb923c`
- Light Red: `#f87171`

**Background:** Dark, moody. Product images appear against dark portfolio background.
**Product images:** No color shift; same RGB values, different presentation context

### Workshop Theme (₺39.99)

**Primary palette:**
- Industrial Orange: `#f97316`
- Stone Brown: `#57534e`
- Leaf Green: `#22c55e`
- Gold Yellow: `#eab308`
- Coral Red: `#ef4444`

**Background:** Textured, industrial (wood, metal). Product images on rough textures.
**Product images:** No color shift; same RGB, different surrounding aesthetic

**Rule:** Product photography is theme-independent. Themes change UI/background, not product appearance.

---

## 🛑 Overlay System

Defects and states are indicated by **SVG overlays** that layer over product images.

### Overlay Design

- **Format:** SVG (scalable, sharp at any size)
- **Placement:** Corner (top-left, top-right, bottom-right) or full-card semi-transparent
- **Opacity:** 60-80% to show defect without hiding product
- **Color:** Theme-aware (changes per theme)
- **Animation:** Subtle (1-2 sec fade in on reveal, no continuous animation)

### Overlay Examples

**Battery Warning Overlay**
- Icon: Lightning bolt + caution colors (orange/amber)
- Text (optional): "Low Battery"
- Placement: Bottom-right corner
- Triggers: battery_health < 50%

**Screen Crack Overlay**
- Icon: Broken glass pattern
- Semi-transparent red tint
- Placement: Center or top-left
- Triggers: crack defect present (visible)

**Water Damage Indicator**
- Icon: Water droplet + corrosion texture
- Placement: Bottom-left
- Color: Blue + warning (theme-aware)
- Triggers: water_damage confirmed or risk_signal present

**Authenticity Failed (Counterfeit)**
- Icon: Bold ✗ or "COUNTERFEIT"
- Full-card red overlay (60% opacity)
- Placement: Center with fade
- Triggers: authenticity = false (deal-breaker)

### Overlay Creation Checklist

- [ ] SVG format, vectorized (not rasterized)
- [ ] Readable at 256×256 px (game size)
- [ ] Color accessible (WCAG AA contrast minimum)
- [ ] No hardcoded colors; use theme variables
- [ ] Animation (if any) under 2 seconds
- [ ] File size < 20 KB
- [ ] Consistent with other overlays (same visual language)

---

## 🎭 Icon System

### UI Icons

All UI icons (Market, Portfolio, Journey, etc.) should be:

- **Format:** SVG
- **Stroke Weight:** 2 px (readable at 24×24 px)
- **Optical Center:** Slightly above true center (visual balance)
- **Color:** Mono outline (theme color fills in UI)
- **Consistency:** Aligned stroke weight, baseline, cap style

**Core Icons (11):**
- Market → Stall/shop icon
- Portfolio → Inventory/briefcase
- Watchlist → Eye or bookmarks
- Journey → Roadmap or timeline
- Compare → Side-by-side squares
- Inspect → Magnifying glass
- Negotiate → Handshake or dialog
- Prepare → Tools or wrench
- List → Document or price tag
- Cash → Wallet or banknote
- Home → House silhouette

### Icon Specs

- **Master:** 256×256 px (grid-based, 16 px increments)
- **Game size:** 24×24 px, 32×32 px, 48×48 px
- **Stroke:** 2-2.5 px consistent
- **Padding:** 4 px internal padding minimum

---

## 📏 UI Asset Dimensions

### Mobile Buttons & Touch Targets

- **Minimum hit area:** 44×44 CSS px (touch)
- **Primary CTA button:** 48×16 mm (visual), 100% width (responsive)
- **Secondary button:** 40×14 mm
- **Card:** Full width (320-430 CSS px viewport max, 8 px margin)

### Portfolio / Market Cards

- **Card height:** 120-160 px (depends on content)
- **Product image:** 80×80 px to 100×100 px
- **Text hierarchy:** Font size 12-16 px for labels, 18-20 px for prices
- **Touch spacing:** 8 px between interactive elements

### Sheet Layouts (Bottom Sheet / Modal)

- **Safe area:** 8-16 px padding top/bottom (system notch safe)
- **Max width:** 430 CSS px (landscape phone)
- **Content width:** 100% - 16 px padding
- **Z-layer:** Overlay with 40% dark scrim

---

## 🎬 Animation & Micro-Interactions

### Approval: Subtle, Not Gratuitous

| Event | Animation | Duration | Easing |
|-------|-----------|----------|--------|
| Toclif/Card Tap | Scale 0.98x + opacity | 150ms | ease-out |
| Offer Sent | Slide up + fade | 300ms | ease-in-out |
| Kâr Realized | Count-up number + pulse | 800ms | ease-out |
| Zararlı Satış | Shake (8px) + fade | 600ms | ease-in |
| İlan Kaçtı | Fade out + slide right | 500ms | ease-in |
| Milestone/Ev | Large scale + fade in | 1000ms | ease-in-out |

**Rule:** No continuous animation (spinning, pulsing indefinitely). Animations are acknowledgments, not constant noise.

---

## 🔊 Audio Guidelines

### UI Sounds

- **Navigation (tab click):** 80 ms, 40 dB (quiet)
- **Teklif gönder:** 120 ms, 50 dB (clear confirmation)
- **Satın alma başarı:** 300 ms (short melody), 60 dB
- **Zararlı satış:** 200 ms warning tone, 55 dB (educational, not scolding)
- **İlan kaçtı:** 150 ms fade, 45 dB (notification, not alarm)
- **Milestone/ev:** 2-3 sec signature sound, 70 dB

**Tool:** All sounds should have **volume normalized** and **crossfade** to avoid pops.

### Audio File Specs

- **Format:** MP3 or AAC (mobile-friendly)
- **Bitrate:** 128-192 kbps
- **Sample rate:** 44.1 kHz
- **File size:** < 100 KB per clip

### Theme-Specific Audio

- Standard: Clean, bright UI tones
- Night Market: Warmer, lo-fi aesthetic (analog tape feel)
- Workshop: Industrial sounds (metal touches, tool sounds)

---

## 🎯 Condition Visuals

### Visual Representation of Condition Grade

**Mint** (100%)
- No visible wear, pristine
- Bright, clean lighting

**Near Mint** (95%)
- Barely noticeable micro-scratches
- Professional appearance

**Excellent** (90%)
- Light use, minimal wear
- Well-maintained appearance

**Very Good** (80%)
- Moderate use, few scratches/marks
- Clean but lived-in

**Good** (70%)
- Regular use, visible wear
- Functional, cosmetics less premium

**Fair** (60%)
- Heavy use, significant cosmetic wear
- Rough, but functional

**Poor** (50% or below)
- Very heavy wear, possibly non-functional
- Distressed, parts may be missing

**Practical Implementation:**
- Don't create 7 separate product images
- Use **one clean master image** + overlay/filter adjustments in UI
- Defect overlays + condition badge convey state
- Reduce saturation slightly for lower conditions (optional, subtle)

---

## 🏠 Home Style Visuals

### Home Previews

Each home style is a **full-screen preview** shown when player reaches 100% goal and during final sequence.

**Specifications:**
- **Format:** JPG or PNG (larger file acceptable for one-time view)
- **Resolution:** 1920×1080 px (16:9)
- **Lighting:** Warm, inviting
- **Personalization:** Show player's dominant category items (books for vinyl lovers, etc.)
- **Mood:** Aspirational but achievable

**Three Styles:**

1. **Modern Minimalist** (Default)
   - Clean lines, neutral palette (white, gray, black)
   - Natural light, large windows
   - Empty surfaces, curated objects
   - Feel: Calm, accomplished, serene

2. **Cozy Traditional** (Paid)
   - Warm woods, textiles, layered lighting
   - Family photos, personal items
   - Bookshelf, comfortable furniture
   - Feel: Warm, personal, lived-in luxury

3. **Industrial Urban** (Paid)
   - Exposed brick, steel beams, skylights
   - Art gallery aesthetic, high ceilings
   - Minimal furniture, gallery walls
   - Feel: Creative, edgy, accomplished

---

## ✅ Asset Quality Checklist

Before submitting any visual asset:

- [ ] **Correct dimensions** (512×512 for products, per-type otherwise)
- [ ] **Transparent background** (if required)
- [ ] **No hardcoded text** on image (use UI layer)
- [ ] **File size optimized** (PNG: < 200 KB, SVG: < 50 KB)
- [ ] **Color-space correct** (sRGB, no profile embedding)
- [ ] **Readable at game size** (test at 256×256 and 128×128)
- [ ] **Defect overlays** align properly (test positioning)
- [ ] **Theme-agnostic** (no bleed of theme colors into product image)
- [ ] **Named consistently** (e.g., `phone_flagship.png`, not `flagship_new_v3.png`)
- [ ] **Documented** in `assetManifest.json`

---

## 📞 Asset Submission Process

1. **Create asset** per guidelines above
2. **Test at game size** (256×256, 128×128 minimum)
3. **Update assetManifest.json** with path and metadata
4. **Add localization** if new product type
5. **Create PR/commit** with clear description
6. **Code review** + asset review (check dimensions, contrast, readability)
7. **Merge** → asset live on next build

---

## 🚫 Common Mistakes to Avoid

- ❌ **Asset too small to read details** → Increase resolution or simplify
- ❌ **Hardcoded theme color in product image** → Product images theme-agnostic only
- ❌ **Text overlaid on product** → Use UI layer, not asset
- ❌ **Inconsistent icon stroke weight** → Use 2 px consistently
- ❌ **Overlay positioned off-center** → Test on different devices
- ❌ **File size > 500 KB** → Optimize; mobile-friendly sizes
- ❌ **Missing from assetManifest.json** → Asset won't load
- ❌ **Continuous animation** → Animations should be event-based, not loops

---

## 🎨 Theme Color Variables

### CSS/Design System

Use **CSS custom properties** for theme colors; never hardcode:

```css
:root {
  --color-primary: #2563eb;
  --color-secondary: #64748b;
  --color-success: #16a34a;
  --color-warning: #ea580c;
  --color-danger: #dc2626;
}

[data-theme="night_market"] {
  --color-primary: #fbbf24;
  --color-secondary: #1e293b;
  --color-success: #34d399;
  /* ... etc */
}
```

Overlays and UI elements pull from these; product images don't.

---

## 📖 Example Asset Creation

### Creating a New ProductFamily: Luxury Pens

1. **Define in productFamilies.json:**
   ```json
   {
     "id": "luxury_pens",
     "displayName": { "en": "Luxury Pens", "tr": "Lüks Kalemler" },
     "baseValue": 8500,
     "variants": [
       { "id": "fountain", "valueFactor": 1.25 },
       { "id": "rollerball", "valueFactor": 1.0 }
     ],
     "assetKey": "pen_luxury"
   }
   ```

2. **Create visuals:**
   - `pen_luxury.png` (512×512, both variants represented)
   - `pen_fountain.png` (fountain pen, 512×512)
   - `pen_rollerball.png` (rollerball pen, 512×512)
   - `pen_luxury_thumb.png` (128×128)

3. **Create overlays:**
   - `nib_damage.svg` (scratched/bent nib indicator)
   - `ink_leak.svg` (leaked ink stain)

4. **Update assetManifest.json:**
   ```json
   "pen_luxury": {
     "familyId": "luxury_pens",
     "images": {
       "default": "images/products/luxury/pen_luxury.png",
       "variant_fountain": "images/products/luxury/pen_fountain.png",
       "variant_rollerball": "images/products/luxury/pen_rollerball.png"
     }
   }
   ```

5. **Add localization** strings
6. **Commit** → asset ready for next build

---

**Asset Guidelines Ownership:** Studio Nostos Visual Team | **Last Updated:** 04.09.2026

