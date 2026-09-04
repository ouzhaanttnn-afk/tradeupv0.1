# TradeUp: Zero to Home

**A data-driven second-hand market trading simulation game**

---

## 📱 Game Overview

TradeUp is a short-session mobile game (2-20 minutes per play) where players:

1. **See** opportunities in a live second-hand marketplace
2. **Compare** similar products to spot value mismatches  
3. **Validate** claims and condition through strategic inspection
4. **Negotiate** with sellers (exactly two offers)
5. **Prepare** owned items to maximize resale value
6. **Exit** profitably and build a real trading career
7. **Reach** their home ownership goal through honest trading

**North Star:** Players build wealth through market intelligence, not luck or pay-to-win mechanics.

---

## 🎯 Core Design Principles

From [GDD v2.1](./ASSET_BIBLE.md):

| Principle | What It Means |
|-----------|---------------|
| **System-First** | All content lives in config/data; no hardcoded logic per product type |
| **Information Asymmetry** | Players use evidence, speed, and capital to outread the market |
| **Honest Economics** | Every transaction logged; wealth comes from real decisions, not RNG |
| **Short Sessions** | 2-4 min quick checks to 20+ min deep market dives; same economy |
| **Personal Journey** | Career timeline built from actual trades; no fixed story path |

---

## 📦 Project Structure

```
tradeupv0.1/
├── src/
│   ├── data/                      # Game configuration (JSON-based, no code changes needed)
│   │   ├── productFamilies.json   # 24 ProductFamily definitions (smartphones, watches, etc.)
│   │   ├── attributeDefinitions.json  # Generic attributes (battery, condition, etc.)
│   │   ├── evidenceDefinitions.json   # Inspection types & actions
│   │   ├── defectDefinitions.json    # Defect pool (28 types)
│   │   └── preparationActions.json   # Value-adding actions (Clean, Test, Complete)
│   │
│   └── assets/                    # Visual & audio assets
│       ├── assetManifest.json     # Asset registry & fallback mapping
│       ├── images/
│       │   ├── products/          # Product visuals by category
│       │   ├── overlays/          # Defect indicators (SVG)
│       │   ├── ui/                # Theme backgrounds, icons
│       │   ├── home/              # Home style previews
│       │   └── fallback/          # Placeholder assets
│       └── audio/
│           ├── ui/                # Navigation, feedback sounds
│           └── themes/            # Theme-specific audio
│
├── ASSET_BIBLE.md                # Complete asset system documentation
├── ASSET_GUIDELINES.md           # Visual design standards
├── README.md                      # This file
└── package.json
```

---

## 🚀 Getting Started (Development)

### Prerequisites

- Node.js ≥18
- Git
- (Optional) Asset creation tools (Figma, Adobe CC, Blender for 3D)

### Setup

```bash
git clone https://github.com/ouzhaanttnn-afk/tradeupv0.1.git
cd tradeupv0.1
npm install
# (More setup scripts will be added as project expands)
```

### Key Files for Understanding the Game

1. **[ASSET_BIBLE.md](./ASSET_BIBLE.md)** — Start here
   - 24 ProductFamily system
   - Attributes, evidence, defects
   - Preparation actions
   - Content acceptance criteria

2. **[ASSET_GUIDELINES.md](./ASSET_GUIDELINES.md)**
   - Visual design standards
   - Icon & overlay specifications
   - UI theme colors
   - Animation guidelines

3. **src/data/productFamilies.json**
   - Complete ProductFamily catalogue
   - Variant definitions
   - Base economics (value, demand, liquidity)

4. **src/data/attributeDefinitions.json**
   - Generic attributes (type, curve, reveal rule)
   - How evidence reveals partial information
   - Reusable across categories

5. **src/assets/assetManifest.json**
   - Visual asset registry
   - Fallback strategy
   - Theme definitions
   - Home style configurations

---

## 🎨 Asset System

### Zero Hardcoding Promise

**No code branches on product category names.** All content is:

✅ **Config-based** (JSON data)  
✅ **Attribute-driven** (generic attributes, no category-specific UI)  
✅ **Data-defined** (asset manifest, no hard-wired image paths)  
✅ **Localization-complete** (all strings in locale files)  

### 24 Vertical Slice Families

| Category | Families | Focus |
|----------|----------|-------|
| **Electronics** | Phone, Tablet, Laptop, Camera, Audio, Watch, Console | Demand, battery, condition |
| **Fashion** | Luxury Watch, Handbag, Sneakers, Sunglasses | Authenticity, rarity |
| **Home** | Sofa, Desk, Bed, Shelf | Condition, transport |
| **Entertainment** | Vinyl, Games, Instruments | Rarity, collection value |
| **Vehicles** | Bike, E-Scooter | Mechanical condition |
| **Sports** | Camping, Fitness | Material quality |

Each family has **3-4 variants** representing different tiers/styles within the category.

---

## 🔍 Evidence & Inspection

Players validate listings through **8 evidence types**, each with cost/time/confidence trade-off:

| Type | Cost | Confidence | Use Case |
|------|------|------------|----------|
| Photo Analysis | Free | +15% | Spot visual red flags |
| Warranty Check | ₺200 | +30% | Confirm coverage (electronics) |
| Quick Test | ₺250 | +35% | Fast functional check |
| Service History | ₺300 | +40% | Maintenance records |
| Detailed Inspection | ₺750 | +55% | Professional assessment |
| Authenticity Check | ₺1,500 | +80% | Verify authenticity (deal-breaker) |
| Expert Appraisal | ₺2,500 | +90% | Full valuation |

**Design:** More inspection = higher confidence = narrower value band = better buy/sell decisions.

---

## 🛠️ Preparation System

After purchasing, players add value through **5 optional actions**:

| Action | Cost | Time | Max Benefit | Purpose |
|--------|------|------|-------------|---------|
| **Clean** | ₺150 | 3m | +8% | Improve cosmetic appeal |
| **Test** | ₺250 | 4m | +12% | Document working state |
| **Complete** | ₺400 | 5m | +15% | Add missing accessories |
| **Light Service** | ₺500 | 6m | +10% | Minor maintenance (soft launch) |
| **Bundle** | Free | 2m | +20% | Combine for lot sale (post-alpha) |

**Design:** Preparation rewards knowledge (knowing which action helps) + investment, but doesn't bypass core economics.

---

## ⚠️ Defect System

**28 defined defects** with clear severity tiers and fairness guarantees:

| Severity | Example | Penalty | Design Rule |
|----------|---------|---------|------------|
| **Low** | Dead pixel | -5-12% | Cosmetic, always visible |
| **Medium** | Battery degraded | -15-22% | Detectible via inspection |
| **High** | Screen crack | -30-40% | Visible in photos + risk signal |
| **Critical** | Water damage, counterfeit | -50-100% | Requires paid inspection; has risk signal OR is deal-breaker |

**Fairness Guardrails:**
- ✅ No defect surprises without prior risk signal
- ✅ No wipe-outs in first 60 minutes
- ✅ Recovery paths exist for learning moments
- ✅ Result screen explains what player missed

---

## 💰 Economy & Monetization

### v1.0 (Locked)

**Free-to-Play:**
- Full access to core loop (market, negotiate, prepare, exit)
- Home ownership reachable without spending
- Rewarded video for convenience (4 placements, 8 daily cap)

**Premium ($4.99 USD equivalent):**
- Skip rewarded ads
- Exclusive Obsidian Ledger UI theme
- Founder badge

**Cosmetic Themes ($1.99 each):**
- Night Market (dark, moody)
- Workshop (industrial aesthetic)

**Home Styles ($2.99 bundle):**
- Cozy Traditional
- Industrial Urban

**Economic Invariants:**
- Zero pay-to-win mechanics
- No cash packs, energy, or power purchases
- No "guaranteed fırsat" or "ek pazarlık hakkı" for money
- Monetization is UI/cosmetics only

---

## 📊 Data-Driven Content

### Adding New Content Post-Launch

**New ProductFamily? Only touch data:**

1. Add to `productFamilies.json`
2. Reference existing/new attributes in `attributeDefinitions.json`
3. Link defects in `defectDefinitions.json`
4. Create/add visuals in `assetManifest.json`
5. Add localization strings
6. **No code changes.**

**New Defect? Only data:**

1. Add to `defectDefinitions.json`
2. Reference in family `defectPool`
3. Create overlay (SVG) if visual
4. Localize
5. Done.

**New Attribute? Only data:**

1. Add definition to `attributeDefinitions.json`
2. Link in families that use it
3. Localize
4. UI auto-renders in comparisons

---

## 🎭 UI Themes

### Standard (Free)
Clean, professional market interface. Blue primary, neutral secondary.

### Night Market (₺39.99)
Dark, moody trading space. Warm amber primary, deep gray background.

### Workshop (₺39.99)
Industrial, hands-on aesthetic. Orange primary, stone brown background.

**Rule:** All themes have identical functionality. Cosmetic only. Condition metrics, evidence, profit math unchanged.

---

## 🏠 Home Progression

Player's goal: Accumulate enough wealth (config: ₺3.5M default) to buy a home.

Milestones:
- 25%: "Journey started"
- 50%: Home siluette visible
- 75%: Top 3 trades shown
- 90%: Liquidity plan + remaining amount
- 100%: Choose home style → personal finale

**Design:** Home is aspiration, not paywall. Reachable entirely through gameplay.

---

## 🌍 Localization

**Supported:** English (en), Turkish (tr)

All user-facing text lives in `src/localization/strings.json`. No hardcoded strings in code.

---

## 🧪 Testing & QA

### Before Soft Launch

- [ ] 24 ProductFamilies load correctly
- [ ] All attributes, evidence, defects config'd
- [ ] Asset fallback system works (missing images → placeholder)
- [ ] Localization complete (en + tr)
- [ ] Economic invariants hold (no double-charging, no asset loss)
- [ ] No hardcoded product type logic
- [ ] UI renders at 320-430 px widths
- [ ] Animations smooth, sounds play correctly

### Telemetry

Critical metrics to track:
- D1, D7, D30 retention
- Time to first profitable sale
- Compare usage rate (should be high)
- Preparation action adoption
- Category distribution (avoid single-category trap)

---

## 🚀 Roadmap

### v1.0 (Soft Launch)
- ✅ 24 ProductFamilies
- ✅ Core economy + trading loop
- ✅ Evidence & preparation system
- ✅ One paid theme + cosmetics
- ✅ Home progression
- Measurement + data collection

### v1.1 (Post-Data)
- 6-8 new families based on player signals
- Seller memory system (if retention strong)
- Market events (trend, seasonality)
- Achievement cosmetics

### v1.2+
- Regional market variants
- Advanced portfolio management
- Social features (if single-player retention stable)

---

## 📞 Documentation

| Document | Purpose |
|----------|---------|
| [ASSET_BIBLE.md](./ASSET_BIBLE.md) | Complete asset system & content guide |
| [ASSET_GUIDELINES.md](./ASSET_GUIDELINES.md) | Visual design standards |
| [GDD v2.1](./gdd/GDD_v2.1.md) | Game design document (locked) |

---

## 🔐 Design Freeze (v2.1)

Per GDD v2.1, the following are **frozen** until post-soft-launch data review:

- 🔒 Exact 24 ProductFamily list
- 🔒 Two-offer negotiation limit (not bypassed by ads/IAP)
- 🔒 Home goal amount (₺3.5M TRY default)
- 🔒 Rewarded ad placements & caps
- 🔒 Core economic formulas
- 🔒 No new gameplay mechanics

What **can** change during implementation:
- ✅ Bug fixes
- ✅ UI clarity & UX tweaks
- ✅ Asset quality improvements
- ✅ Performance optimization
- ✅ Config calibration (within published ranges)

---

## 🤝 Contributing

### Asset Submission

1. Create asset per [ASSET_GUIDELINES.md](./ASSET_GUIDELINES.md)
2. Test at game size (256×256 minimum)
3. Update `assetManifest.json` with path
4. Add localization if new family
5. Create PR → code + asset review → merge

### Data Changes

1. Edit `.json` in `src/data/`
2. Validate against schema (if validator added)
3. Test in game (ensure asset references exist)
4. PR → review → merge

### Localization Additions

1. Edit `src/localization/strings.json`
2. Add both `en` and `tr` keys
3. PR → review → merge

---

## 📄 License

*License information to be added*

---

## 👥 Team

**Studio Nostos**

- **Design:** Alper (GDD lead)
- **Development:** (Incoming)
- **Art & Assets:** (Incoming)

---

## 🙋 Questions?

- Asset system: See [ASSET_BIBLE.md](./ASSET_BIBLE.md)
- Visual standards: See [ASSET_GUIDELINES.md](./ASSET_GUIDELINES.md)
- Game design: See GDD v2.1 (locked)
- Feature requests: Escalate; design is frozen until post-soft-launch

---

**Last Updated:** 04.09.2026 | **Maintained by:** Studio Nostos | **Current Branch:** `claude/asset-hazirlama-gc8whk`
