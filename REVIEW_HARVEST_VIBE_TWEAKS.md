# REVIEW HARVEST — VIBE CODER TWEAK BRIEF

Paste this alongside the exported page code into GoHighLevel's Vibe Coder. It tells the AI builder exactly how to re-skin the existing "Review Harvest" review-reputation landing page (hero → footer, same sections/copy structure) into the **Wave Pay & Strategies "deep ocean at night"** look defined in `STYLE_BLUEPRINT.md`. Keep the current section order and form logic — only restyle colors, type, motion, and card treatment as below.

---

## 1. Global palette swap

The page currently runs a light, generic-SaaS palette (white/#fafafa panels, near-black text, purple/blue accents). Replace every instance with the dark aquatic-luxury palette:

| Current (light theme) | Role | New (Wave Pay dark theme) |
|---|---|---|
| `#ffffff` (white section/card backgrounds) | page/card surface | `#030810` (page bg) / `rgba(8,18,32,0.65)` (glass cards) |
| `#fafafa` (alternating section bg) | secondary section bg | `#060c18` |
| `#F0F0F0` (card/nav borders) | hairline borders | `rgba(42,184,212,0.14)` — brighter `rgba(42,184,212,0.35)` on hover |
| `#242424` (headings) | heading text | `rgba(255,255,255,0.86)` |
| `#64646E` (body copy) | body/dim text | `rgba(255,255,255,0.62)` |
| undefined primary (`--color-m6qoe61i`, used on all CTA buttons, links, icons) | primary accent | `#2ab8d4` (teal), glow variant `#4dd9ef` for hover/shadow |
| `#604BEA` (purple, feature icon accents) | secondary accent | `#c9a96e` (muted gold) — use sparingly, e.g. one icon or divider per section |
| `#0038FF` (pricing bullet links) | accent | `#2ab8d4` |
| `#565A7C` / `#8893A8` (secondary/testimonial text) | dim text | `rgba(255,255,255,0.62)` / `rgba(255,255,255,0.5)` |
| `#000321` (dark testimonial quote text) | — | keep as a background variant if a near-black card is needed (`#0c1828` preferred) |

Body background should be the deep navy-black gradient feel: base `#030810`, alternating sections `#060c18` / `#0c1828` — never pure white or light gray again.

## 2. Typography

- Add Google Fonts: **Cormorant Garamond** (weights 300, 300 italic) and **Montserrat** (400–700).
- Set the headline font to Cormorant Garamond at weight 300 (light), not the current bold 700. Every `<h1>`/`<h2>` in this export is currently forced to 700 weight — override to 300, and italicize the emotional/benefit word in each headline (e.g. "Get More Reviews, Rank Higher, *Grow Faster*").
- Set the body/content font to Montserrat.
- All the small pill/eyebrow buttons above each section heading ("Welcome to", "About Us", "Testimonials", "Three Steps", "Pricing", "Statistics", "FAQ") should stop being filled button-pills and become tiny uppercase labels: Montserrat, 11–12px, letter-spacing 0.24–0.32em, color `rgba(255,255,255,0.62)`, transparent background, no border.
- Increase the size contrast: keep hero H1 large and delicate serif; keep uppercase labels genuinely small (don't let the builder auto-scale them up).

## 3. Buttons / CTAs

Every button in the export ("Start Free", "Get Started Now", "Choose Starter/Growth/Pro", "Send Preview", etc.) should become:
- Solid turquoise fill `#2ab8d4`, dark navy text `#030810` (not white).
- 10px radius (keep existing `radius10`).
- On hover: lift 2–3px + teal glow shadow `0 8px 24px rgba(42,184,212,0.35)` — the export already has `buttonElevate`/`hvr-grow` hover classes wired up, just repoint the glow color, keep it gentle (no bounce/wobble).
- Secondary/outline buttons (footer nav links, e.g. "Home", "About Us") stay text-only, dim white, brightening to teal on hover.

## 4. Cards (features, testimonials, pricing, stats)

Every white card box in the export (about-section 3-up cards, feature blocks, testimonial cards, pricing columns, "92% / 72% / 54% / 84%" stat tiles) becomes a **floating glassmorphic card**:
- `background: rgba(8,18,32,0.65)`
- `border: 1px solid rgba(42,184,212,0.14)` → `rgba(42,184,212,0.4)` on hover
- `border-radius: 14px`
- `backdrop-filter: blur(12px)`
- subtle lift + teal glow shadow on hover, matching the button treatment
- Pricing "Growth" (middle/featured) plan keeps a slightly brighter border/glow so it still reads as the recommended tier, but no longer a solid brand-color block — use a soft teal-tinted glass instead of the current flat fill.

## 5. Motion

- The export already has `data-animation-class` / entrance-animation hooks on every section and `hvr-*` hover classes on buttons — don't remove them, just slow them down. In the Vibe Coder's animation settings, set section entrance to **Fade Up, 0.9s, ease** (current default is snappier) so it matches the blueprint's "slow, deliberate" motion language.
- Skip aggressive hover styles like `buttonBounce`/`buttonRocking`/`buttonWobble` if the builder offers them — stick to a gentle lift + glow only.
- Ambient effects (rising bubbles, wave canvas, caustic shimmer) are a stretch goal — GHL's no-code builder can't do this natively, so only add it if the Vibe Coder supports a custom HTML/JS embed block in the hero section; otherwise skip and rely on the glow/glass treatment to carry the "underwater" feeling.

## 6. Form (popup lead-capture form + any embedded intake form)

Per the blueprint's Form/Intake Sheet Treatment:
- Form card: `rgba(8,18,32,0.65)` surface, 1px teal border `rgba(42,184,212,0.14)`, 14px radius (the export's popup already sits in its own bordered container — just restyle it).
- Inputs (name/phone/text fields): near-transparent dark fill, `rgba(255,255,255,0.05)` background, 1px `rgba(42,184,212,0.14)` border, teal focus ring + soft glow on focus.
- Labels: tiny uppercase, wide letter-spacing, dim white — matching section eyebrow labels above.
- Submit button: solid turquoise, dark text, lift + glow on hover (same as CTA spec).
- Success/thank-you state ("A Preview Is Heading Your Way!"): teal-tinted confirmation panel, not the current default green/white system message.
- **Mobile:** the export's phone dropdown (country-code picker) and any select/multiselect must stay a solid, opaque dark panel — `#0c1828` or similar, not translucent — so text stays legible over the dark page background. This is an explicit blueprint rule; don't let the glass/blur treatment bleed into mobile dropdown menus.

## 7. Copy tone (aquatic language pass)

Keep every heading's meaning but lean into the blueprint's vocabulary ("flow," "currents," "seamless," "deep," "tide") where it doesn't feel forced. A few direct swaps:

- Hero H1 "Get More Reviews, Rank Higher, Grow Faster" → keep, but consider "Let Your Reviews *Flow*" as an alt for the small eyebrow label above it.
- "We make building your business's online reputation easier than ever." → "We make your online reputation flow effortlessly."
- "Get Started in Three Steps" → "Three Steps to a Stronger Current" (optional — only if it doesn't read as gimmicky next to functional copy like "Sign Up and Customize").
- Keep all functional/precise copy (pricing, feature descriptions, FAQ answers) as-is — the aquatic metaphor belongs in headlines and section eyebrows, not feature bullet lists or legal/FAQ text.

## 8. Brand-name check (confirm before rebuild)

`STYLE_BLUEPRINT.md`'s brand rules ("Always 'Wave Pay & Strategies' — never a dash separator," "Founder: Noah Nodal · 'Smart Solutions. Stronger Businesses.'") apply to the parent company. This export is branded as its own product, **"Review Harvest"** (page title, footer copyright link to reviewharvest.com). This brief assumes you're keeping "Review Harvest" as the product name and applying Wave Pay's *visual design system* to it (same way a company skins a sub-product), not renaming the product itself or replacing the footer/copyright/founder line. If the product should actually be re-branded as a Wave Pay & Strategies property (name, footer, links all swapped), say so and I'll extend this brief with the exact copy changes.

---

### One-paragraph version to paste straight into the Vibe Coder chat

> Restyle this page into a "deep ocean at night" luxury look: dark navy-black background (#030810 base, #060c18/#0c1828 for alternating sections), bright turquoise accent (#2ab8d4, glow #4dd9ef) on all buttons/links/icons, muted gold (#c9a96e) used sparingly for one accent per section, soft white body text (rgba(255,255,255,0.86) headings, 0.62 body). Headings in Cormorant Garamond, weight 300, with the key phrase italicized; body and small uppercase eyebrow labels (0.24–0.32em letter-spacing) in Montserrat. Turn every card (feature blocks, testimonials, pricing columns, stat tiles) into a glassmorphic panel: rgba(8,18,32,0.65) background, 1px teal border rgba(42,184,212,0.14), 14px radius, subtle blur, with a gentle lift + teal glow on hover — same lift+glow treatment on all buttons (turquoise fill, dark navy text). Slow all entrance/scroll animations to a 0.9s fade-up. Restyle the lead-capture form to match: transparent dark inputs with teal focus glow, tiny uppercase dim labels, teal submit button, teal-tinted success message — but keep the mobile phone/country-code dropdown solid and opaque (not translucent) so it stays readable. Keep all copy, layout, and section order as-is except: lightly weave in aquatic language ("flow," "seamless," "deep," "tide") in headlines and section eyebrows only, not in feature/FAQ body copy.
