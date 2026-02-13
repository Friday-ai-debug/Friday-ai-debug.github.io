# Design System: AI Email Agent Website

## 1. Visual Theme & Atmosphere

Clean, trustworthy, and human-focused. The design balances professional credibility with approachability. It feels like talking to a capable assistant, not a faceless corporation.

**Atmosphere:** Warm but functional, like a well-designed productivity tool you'd actually use
**Vibe:** "I've got this handled" - competent without being sterile
**Density:** Airy and spacious - generous whitespace prevents overwhelm
**Philosophy:** Function over flash. Every element has a clear purpose.

## 2. Color Palette & Roles

- **Deep Charcoal (#1a1a1a)** - Primary headings and important text. Trustworthy, authoritative without being harsh
- **Soft Gray (#666666)** - Body text and secondary content. Easy on eyes, maintains readability
- **Warm White (#faf9f7)** - Background. Paper-like, feels natural not digital
- **Clean White (#ffffff)** - Content cards and sections. Creates separation without harsh lines
- **Deep Ocean Blue (#2563eb)** - Primary actions and links. Trustworthy, professional, prompts action
- **Success Green (#22c55e)** - Guarantees and positive messages. Reassuring without being aggressive
- **Warning Yellow (#fcd34d)** - Highlights and callouts. Draws attention without being alarming

## 3. Typography Rules

- **Font family:** Georgia for headings (serif, human feel), Inter or system-ui for body (clean, readable)
- **Font weights:** Bold (600-700) for headlines only. Regular (400) for body text - creates clear hierarchy
- **Letter spacing:** 0.01em for headings (slightly open, feels friendly). Normal tracking for body text
- **Line height:** 1.7 for body text (generous spacing, easy reading). 1.3 for headings
- **Size scale:** 2.2em for h1 (title), 1.5em for h2 (section headers), 1.05em for body

## 4. Component Stylings

**Buttons:**
- Shape: Subtly rounded corners (6px radius). Friendly but not playful
- Color: Deep Ocean Blue (#2563eb) for primary actions. Text is Clean White (#ffffff)
- Size: Generous padding (15px 25px vertically, 25px horizontally). Easy to tap/click
- Behavior: Hover deepens to #1a1a1a with 0.2s transition. Provides feedback

**Cards/Containers:**
- Corner roundness: Gently rounded (12px). Soft, approachable
- Background: Clean White (#ffffff) on Warm White (#faf9f7). Creates subtle depth
- Shadow: Whisper-soft diffused shadows (0 2px 8px rgba(0,0,0,0.06)). Elevation without heaviness
- Padding: 25px all sides. Content breathes

**Inputs/Forms:**
- Stroke style: 1px solid #e5e5e5. Visible but not harsh
- Background: Clean White (#ffffff). Blends with content
- Focus state: Subtle glow ring (0 0 0 3px rgba(37,99,235,0.3)). Confirms where you're typing
- Padding: 12px 16px. Generous touch targets

**Links:**
- Color: Deep Ocean Blue (#2563eb). Matches primary actions
- Behavior: Underline by default, none on hover. Familiar interaction pattern
- Weight: 600 for navigation links. Slightly heavier than body text

**Highlights/Callouts:**
- Background: Warning Yellow (#fcd34d). Draws attention naturally
- Shape: Very subtly rounded (4px). Integrates with text
- Padding: 2px 6px. Emphasizes without overwhelming

## 5. Layout Principles

**Whitespace strategy:** Generous margins (40px between sections). Content feels approachable, not cramped
**Container width:** 700px maximum on desktop. Optimal reading line length (60-75 characters)
**Vertical rhythm:** 30px minimum between stacked elements. Clear visual hierarchy
**Mobile adaptation:** Stack vertically on screens < 600px. Full-width containers on mobile
**Grid alignment:** Single column center-focused. Focused reading path, no distraction

## 6. Interaction & Motion

**Transitions:** 0.2s ease-out. Natural, responsive feel without being sluggish
**Hover states:** All interactive elements respond to hover. Confirms interactability
**Focus states:** Visible indicators for all inputs/links. Accessibility and clarity
**Load states:** Clean skeleton loading. No jarring content shifts
