# TradeUp: Asset Bible and Content Management System

**Version:** 2.1 | **Status:** Production Candidate | **Last Updated:** 04.09.2026

---

## 📋 Overview

This document defines the complete asset management system for TradeUp: Zero to Home. All content is **data-driven and config-based**, meaning new ProductFamilies and visual assets can be added without modifying game engine code.

### Core Principle
> **System-First Architecture:** Data structure and asset manifest define what appears in the game. No hardcoded product type branches. No if/else chains on category names.

---

## 🏗️ Directory Structure

```
tradeupv0.1/
├── src/
│   ├── data/
│   │   ├── productFamilies.json          # 24 ProductFamily definitions
│   │   ├── attributeDefinitions.json     # Generic attributes (type, curve, reveal rule)
│   │   ├── evidenceDefinitions.json      # Inspection & proof system
│   │   ├── defectDefinitions.json        # Defect pool with penalties & signals
│   │   └── preparationActions.json       # Clean, Test, Complete, Light Service, Bundle
│   │
│   ├── assets/
│   │   ├── assetManifest.json           # Visual asset registry & UI elements
│   │   ├── images/
│   │   │   ├── products/
│   │   │   │   ├── electronics/         # Phone, tablet, laptop, camera, audio, watch, console
│   │   │   │   ├── fashion/             # Luxury watch, handbag, sneakers, sunglasses
│   │   │   │   ├── furniture/           # Sofa, desk, bed, shelf/cabinet
│   │   │   │   ├── media/               # Vinyl records, games, instruments
│   │   │   │   ├── vehicles/            # Bike, scooter
│   │   │   │   └── sports/              # Camping, fitness
│   │   │   ├── overlays/                # Damage, warning, condition indicators
│   │   │   ├── ui/                      # Themes, backgrounds, icons
│   │   │   ├── home/                    # Home style previews
│   │   │   └── fallback/                # Placeholder assets
│   │   │
│   │   └── audio/
│   │       ├── ui/                      # Navigation, success, failure sounds
│   │       ├── profit/                  # Profit realization sounds
│   │       └── themes/                  # Theme-specific audio
│   │
│   └── localization/
│       └── strings.json                 # All user-facing text
│
├── ASSET_BIBLE.md                        # This file
├── ASSET_GUIDELINES.md                   # Visual design standards
└── README.md
```

---

## 📦 ProductFamily System

### 24 Vertical Slice Families

| # | Category | Family | baseValue | Demand | Liquidity | Rarity |
|----|----------|--------|-----------|--------|-----------|--------|
| **Electronics** |
| 1 | Electronics | Smartphones | ₺8,500 | 0.85 | fast | common |
| 2 | Electronics | Tablets & iPads | ₺12,000 | 0.65 | medium | common |
| 3 | Electronics | Laptops | ₺18,000 | 0.75 | medium | common |
| 4 | Electronics | Digital Cameras | ₺15,000 | 0.55 | slow | uncommon |
| 5 | Electronics | Headphones & Audio | ₺3,500 | 0.90 | fast | common |
| 6 | Electronics | Smartwatches | ₺5,500 | 0.70 | medium | common |
| 7 | Electronics | Gaming Consoles | ₺22,000 | 0.80 | fast | common |
| **Fashion & Accessories** |
| 8 | Fashion | Luxury Watches | ₺45,000 | 0.65 | slow | rare |
| 9 | Fashion | Designer Handbags | ₺28,000 | 0.70 | medium | uncommon |
| 10 | Fashion | Limited Sneakers | ₺4,500 | 0.95 | fast | uncommon |
| 11 | Fashion | Designer Sunglasses | ₺8,500 | 0.75 | medium | common |
| **Home & Furniture** |
| 12 | Home | Modern Sofas | ₺12,000 | 0.60 | slow | common |
| 13 | Home | Office Desks | ₺4,500 | 0.70 | medium | common |
| 14 | Home | Bed Frames | ₺6,500 | 0.75 | medium | common |
| 15 | Home | Bookshelves & Cabinets | ₺3,500 | 0.65 | medium | common |
| **Entertainment & Media** |
| 16 | Entertainment | Vinyl Records | ₺1,200 | 0.85 | fast | rare |
| 17 | Entertainment | Game Collections | ₺2,500 | 0.80 | fast | uncommon |
| 18 | Entertainment | Musical Instruments | ₺8,000 | 0.70 | medium | uncommon |
| **Vehicles & Transport** |
| 19 | Vehicles | Road Bikes | ₺5,500 | 0.75 | medium | common |
| 20 | Vehicles | Electric Scooters | ₺3,500 | 0.80 | fast | common |
| **Sports & Outdoor** |
| 21 | Sports | Camping Equipment | ₺2,500 | 0.65 | medium | common |
| 22 | Sports | Fitness Equipment | ₺1,800 | 0.70 | medium | common |

**Total:** 24 families covering 6 major categories

---

## 🎨 Attribute System

All families use **generic attributes** with type, curve, and reveal rules. No category-specific attribute definitions.

### Attribute Types

**Numeric (Linear/Curve-Based)**
- `screen_condition` (0-100%)
- `battery_health` (exponential decline)
- `shutter_count` (logarithmic decline)
- `surface_condition` (0-100%)

**Categorical (Options with Value Factors)**
- `storage` (64GB, 128GB, 256GB, 512GB, 1TB)
- `condition_grade` (Mint → Poor)
- `sensor_condition` (Perfect → Poor)
- `material_quality` (Premium → Budget)

**Boolean (Yes/No with Penalty)**
- `water_damage` (-40%)
- `authenticity` (deal-breaker if false)
- `box_included` (+15% if true)
- `frame_integrity` (structural risk)

### Reveal Rules

- **visible_at_lv0:** Always visible (price, basic condition)
- **visible_at_lv1:** Expertise level ≥1
- **requires_inspection:** Free photo analysis reveals partial info
- **requires_paid_inspection:** Costs money/time to fully understand

---

## 🔍 Evidence & Inspection System

### 8 Evidence Types

| Evidence | Reliability | Cost | Time | Confidence | Use Case |
|----------|-------------|------|------|------------|----------|
| Photo Evidence | Medium | Free | 0s | +15% | Visual clues from seller photos |
| Seller Claim | Low | Free | 1m | +5% | Unverified seller statement |
| Quick Test | Medium | ₺250 | 2m | +35% | 1-2 critical attributes |
| Warranty Check | High | ₺200 | 1m | +30% | Verify coverage & validity |
| Service History | High | ₺300 | 2m | +40% | Maintenance & repair records |
| Detailed Inspection | High | ₺750 | 5m | +55% | Professional assessment |
| Authenticity Check | Very High | ₺1,500 | 3m | +80% | Serial, warranty, origin |
| Professional Appraisal | Very High | ₺2,500 | 10m | +90% | Expert report & valuation |

### Inspection Actions (5)

1. **Photo Analysis** (Free, instant)
   - Reveals: screen, upholstery, surface condition
   - Detects: visual inconsistencies, red flags

2. **Functional Test** (₺200-400, 1-4 min)
   - Reveals: battery, keyboard, water damage
   - Risk: 5% failure rate

3. **Cosmetic Detail** (Free-₺200, 30s-2m)
   - Reveals: condition grade, upholstery, sleeve
   - No cost variant via photo analysis

4. **Authenticity Verification** (₺500-2,000, 1-5m)
   - Reveals: authenticity (deal-breaker attribute)
   - High severity; deal-breaking if false

5. **Expert Assessment** (₺1,000-3,000, 5-10m)
   - Reveals: condition grade, sensor, rarity
   - Highest confidence; narrowest value band

---

## ⚠️ Defect System

### 28 Defined Defects

Organized by severity: **Low → Medium → High → Critical**

**Example Defects:**

| Defect | Severity | Penalty | Signal | Reveal Method |
|--------|----------|---------|--------|----------------|
| Battery Degraded | Medium | -15% | age_concern | inspection |
| Screen Crack | High | -35% | photo_inconsistency | visible |
| Water Damage | Critical | -50% | price_outlier | paid_inspection |
| Fake Detected | Critical | -100% | price_outlier | **deal-breaker** |
| Sensor Dust | Medium | -20% | photo_inconsistency | visible_in_photos |
| Keyboard Broken | High | -30% | functional_issue | inspection |
| Shutter Malfunction | Critical | -60% | functional_issue | **deal-breaker** |

### Fairness Guardrails

- ✅ **All critical defects have risk signals** → Player can see warning before purchase
- ✅ **No first-hour wipe-outs** → Defect severity ≤25% net worth in first 60 minutes
- ✅ **Recovery paths exist** → Defect can become teaching moment, not permanent loss
- ✅ **Transparency** → Result screen explains which signal player missed

---

## 🛠️ Preparation System

### 5 Value-Adding Actions

| Action | Cost | Time | Max Value | Effect | Cap |
|--------|------|------|-----------|--------|-----|
| **Clean** | ₺150 | 3m | +8% | Cosmetic appeal | 3x (diminishing) |
| **Test** | ₺250 | 4m | +12% | Evidence confidence | 2x |
| **Complete** | ₺400 | 5m | +15% | Accessory factor | 2x (diminishing) |
| **Light Service** | ₺500 | 6m | +10% | Function confidence | 1x (soft launch) |
| **Bundle** | Free | 2m | +20% | Ticket size & liquidity | 1x (post-alpha) |

### Preparation Design Constraints

- ✅ No magic quality creation → Max +8-15% value
- ✅ Diminishing returns prevent spam → 2-3 applications max
- ✅ Failure is possible → Test has 10% fail rate, teaches risk
- ✅ Cost is transparent → Before/after value shown, profit calc includes cost
- ✅ Optional, not required → Player can list without any prep

---

## 🎨 Visual Asset Organization

### Asset Keys

Each ProductFamily has an `assetKey` linking to visual assets. Example:

```json
{
  "id": "phone_smartphone",
  "assetKey": "phone_generic",
  "variants": ["flagship", "midrange", "budget"]
}
```

### Asset Resolution

For `phone_generic`, variant `flagship`:

1. **First try:** `images/products/phone/phone_flagship.png`
2. **Fallback:** `images/products/phone/phone_generic.png`
3. **Ultimate fallback:** `images/fallback/generic_product_placeholder.svg`

### Overlay System

Visual defects and states are indicated by SVG overlays:

- `battery_warning.svg` → Battery degraded
- `crack_overlay.svg` → Screen crack
- `water_damage.svg` → Water damage detected
- `counterfeit_indicator.svg` → Authenticity failed
- `rust_warning.svg` → Rust spots

**Overlays layer over product images; no pixel-perfect asset editing needed.**

---

## 🎭 UI Themes (Monetization)

### Standard (Free)
- Primary: `#2563eb` (Professional blue)
- Clean, neutral interface
- All core functionality

### Night Market (₺39.99 TRY)
- Primary: `#fbbf24` (Warm amber)
- Dark background, moody trading atmosphere
- Same functionality, different visual mood
- Includes: Dark portfolio background, themed portfolio cards, night market ambience

### Workshop (₺39.99 TRY)
- Primary: `#f97316` (Industrial orange)
- Rugged, hands-on feel
- Industrial textures, worker aesthetic
- Same functionality, craft-focused presentation

**Note:** Themes are **cosmetic only**. Condition metrics, evidence, profit calculations, and decision information remain identical across themes.

---

## 🏠 Home Styles (Post-Game)

When player reaches 100% home goal:

1. **Modern Minimalist** (Free default)
   - Clean, contemporary interior
   - Used in final sequence & portfolio view

2. **Cozy Traditional** (₺49.99 TRY via bundle)
   - Warm, lived-in home aesthetic
   - Family photos, personal touches

3. **Industrial Urban** (₺49.99 TRY via bundle)
   - Loft-style, art-forward space
   - Exposed brick, skylights, gallery walls

---

## 📝 Localization

All user-facing text lives in `src/localization/strings.json`:

```json
{
  "family.phone_smartphone.displayName": {
    "en": "Smartphones",
    "tr": "Akıllı Telefonlar"
  },
  "attribute.battery_health.label": {
    "en": "Battery Health",
    "tr": "Pil Sağlığı"
  }
}
```

**No hardcoded strings in code.** All UI pulls from this file.

---

## ✅ Content Acceptance Criteria

For a new ProductFamily to be added:

1. ✅ Data entry in `productFamilies.json` (variants, attributes, base value)
2. ✅ Attributes exist in `attributeDefinitions.json` (or use existing generic ones)
3. ✅ Evidence types in `evidenceDefinitions.json` (or reuse existing)
4. ✅ Defect pool in `defectDefinitions.json`
5. ✅ Asset entry in `assetManifest.json` (with at least placeholder)
6. ✅ Localization strings in `localization/strings.json`
7. ✅ No engine file changes required

**No code changes needed; only data + asset manifest updates.**

---

## 🚀 Adding Content Post-Launch

### New ProductFamily (Example: Luxury Watches → Mechanical Watches)

1. Add to `productFamilies.json` under existing category or new one
2. Define 2-3 variants with value factors
3. Reuse existing attributes or add new ones to `attributeDefinitions.json`
4. Link to defects in `defectDefinitions.json` (reuse existing like `scratched_case`)
5. Create/add visual assets and update `assetManifest.json`
6. Add localization strings
7. **Profit.** No code refactor needed.

### New Attribute Type (Example: "Rarity Grade")

1. Add definition to `attributeDefinitions.json` with type, options, value curve
2. Reference in relevant product families
3. Add to inspection actions if needed
4. Localize
5. Done. UI auto-renders it in comparisons.

### New Defect (Example: "Screen Protective Film Missing")

1. Add to `defectDefinitions.json` with severity, penalty, signal, reveal method
2. Link to relevant families' `defectPool`
3. Create overlay if visual (or reuse existing)
4. Localize
5. Risk signal added to market algorithm; defect can spawn

---

## 🔧 Fallback & Placeholder Strategy

### Missing Visual Assets

If `images/products/phone/phone_flagship.png` doesn't exist:

1. Try family default: `images/products/phone/phone_generic.png`
2. Try category fallback: `images/fallback/category_electronics.svg`
3. Ultimate fallback: `images/fallback/generic_product_placeholder.svg`

**Gameplay never stops for missing art.** Placeholder system ensures feature-complete flow.

### Missing Audio Assets

UI sounds optional. If missing:
- UI remains responsive (no audio, no stall)
- Gameplay unaffected
- Can be added post-launch

---

## 📊 Asset Manifest Format

```json
{
  "assetKey": "phone_generic",
  "familyId": "phone_smartphone",
  "type": "product_visual",
  "variants": ["flagship", "midrange", "budget"],
  "images": {
    "default": "path/to/default.png",
    "variant_flagship": "path/to/flagship.png",
    "thumbnail": "path/to/thumb.png"
  },
  "overlays": {
    "battery_warning": "path/to/overlay.svg",
    "crack_overlay": "path/to/crack.svg"
  },
  "status": "production_ready | placeholder_pending | in_progress"
}
```

**Status Values:**
- `production_ready` → Shipped, final quality
- `placeholder_pending` → Placeholder asset, real one pending
- `in_progress` → Being created
- `deferred` → Post-launch

---

## 🎯 Production Milestone Checklist

### Before Soft Launch

- [ ] 24 ProductFamilies fully defined in `productFamilies.json`
- [ ] All attributes, evidence, defects, prep actions config'd
- [ ] Core visual assets (2-3 per family minimum)
- [ ] All overlays for critical defects
- [ ] UI themes (Standard + 1 paid variant)
- [ ] Home styles (1-2 options)
- [ ] Complete localization (en + tr)
- [ ] Asset fallback system working
- [ ] No hardcoded product type logic in codebase

### Post-Soft-Launch (Content Roadmap)

- Phase 1: Add 6-8 new families (Q1 2027)
- Phase 2: Expand home styles, achievement cosmetics (Q2 2027)
- Phase 3: Regional market variants, seasonal content (Q3 2027+)

---

## 🔐 Design Freeze Compliance

**[LOCKED]** Per GDD v2.1:

- No new gameplay mechanics attached to specific product types
- No category-specific mini-games
- No hardcoded progression paths
- No purchasing power tied to product category
- System-first: all new content via config, not code

This asset system ensures compliance. **Content grows via data; architecture stays stable.**

---

## 📞 Questions?

Asset Bible is the source of truth for:
- What products are in the game
- How they're valued and prepared
- What evidence is needed
- What defects exist and cost
- How visuals map to gameplay

**If feature spec has "requires new asset system change," it contradicts this design. Escalate.**

---

**Document Ownership:** Studio Nostos | **Last Reviewed:** 04.09.2026 | **Next Review:** Post-Soft-Launch Data
