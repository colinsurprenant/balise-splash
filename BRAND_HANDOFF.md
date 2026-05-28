# Balise — Brand Handoff for Claude Code

> This document describes the visual identity refresh of Balise (May 2026), to be propagated across the product. The splash page (`balise-splash`) has been updated as the reference implementation — match its language when working on the app.

---

## 1 · The Mark

The Balise logo is a **stacked trail blaze** — two rectangles, red on top, navy below. It's a literal reference to the French wayfinding symbol (the painted rectangle on a tree marking a hiking or ski trail). The stacked variant means "continue on the trail" — which is the brand promise.

The mark lives in `assets/balise-mark.svg`. Always use SVG. Never recolor the blocks, never offset the top block (which would change its trail meaning to "turn"), never frame it inside a circle or ring.

**Construction** (on a 200u canvas):
- Top block: x=64, y=30, w=72, h=50, rx=3, fill=red
- Bottom block: x=64, y=92, w=72, h=78, rx=3, fill=navy
- Gap: 12u
- Clear space: 12u on all sides

**Minimum sizes**: 16px for the mark, 88px for any horizontal lockup. Below those, use only the mark.

**Lockup** (mark + wordmark, side-by-side):
- Mark on the left
- Wordmark to the right: "Balise" in Manrope 700, immediately followed by "AI" (or "IA" in French) in Manrope 500 at 60% of the size, 55% opacity, raised baseline
- Vertical alignment: baselines aligned on the "B" descender

---

## 2 · Design Tokens

```css
:root {
  /* Brand colors */
  --balise-navy:       #0F2742;   /* structure: type, plates, dividers */
  --balise-navy-2:     #1d3a5c;   /* body text on light */
  --balise-navy-mute:  #6a7a8a;   /* secondary text, labels */
  --balise-red:        #C8362F;   /* action only: CTAs, links, signal */
  --balise-red-hover:  #A12921;
  --balise-red-soft:   rgba(200, 54, 47, 0.08);  /* icon backgrounds, tints */
  --balise-paper:      #ffffff;   /* primary surface */
  --balise-paper-2:    #f6f4ee;   /* secondary surface, status grid */
  --balise-ink:        #0A1A2E;   /* deep dark, true-black surfaces */
  --balise-line:       rgba(15, 39, 66, 0.10);
  --balise-line-soft:  rgba(15, 39, 66, 0.06);

  /* Type */
  --font-sans: 'Manrope', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-mono: 'DM Mono', ui-monospace, 'SF Mono', Menlo, monospace;
}
```

### Color roles (CRITICAL — don't break the contract)

- **Navy** = structure. Type, headings, plates, dividers, icons.
- **Red** = action / signal. CTAs, links, audience-stat callouts, the blaze tab on cards. Used sparingly so it retains its meaning. Never use red for body text or as a passive accent.
- **Paper white** = primary surface.
- **Paper-2 (warm)** = secondary surface, used only in grouped containers (status grid).

When in doubt, **navy first, red rarely**.

---

## 3 · Typography

```html
<link rel="stylesheet"
      href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700&family=DM+Mono:wght@400;500&display=swap">
```

**Manrope** — UI body, headlines, the wordmark.
- H1: weight 700, letter-spacing -0.028em, line-height 1.18, clamp(1.4rem, 5.2vw, 2.4rem)
- H2 / eyebrows: weight 500, uppercase, letter-spacing 0.16em — but use DM Mono for these
- Body: weight 400/500, line-height 1.55
- Strong: weight 700

**DM Mono** — labels, eyebrows, tags, metadata, file paths, citation references, status sub-labels.
- Use for anything machine/data-flavored
- Use for ALL-CAPS micro-labels (font-size 0.6875rem, letter-spacing 0.08-0.16em)
- NEVER use for body copy

Pattern recognition: if it's content the user reads, Manrope. If it's a label / tag / metadata, DM Mono.

---

## 4 · Component patterns (from the splash, port to the app)

### Header / Brand
```
<logo svg 52px>  Balise<span class="ai">IA</span>           [EN ↗]
```
- Logo: 52px square SVG
- Wordmark: 2rem (32px), Manrope 700, navy
- "AI" / "IA" suffix: 60% of size, weight 500, 55% opacity, raised baseline

### Jurisdiction band (when product needs to advertise the 3-level coverage)
A navy plate with a red blaze marker, eyebrow label, and three pillars:
```
▌ COUVERTURE COMPLÈTE — du palier local au provincial

Municipal    │ MRC                    │ Provincial
Règlements    │ Schéma                 │ Lois et règlements
de votre ville│ d'aménagement         │ du Québec
```
Use this exact pattern whenever the product needs to communicate jurisdiction scope.

### Cards (audience, feature, etc.)
- White background, 1px navy-10% border, 6px radius
- Small red blaze tab on top (`::before` pseudo, 28px wide × 3px tall, navy-corner)
- Padding 22px
- Icon in a 36px square box with `--balise-red-soft` background (8% red tint), navy icon inside
- On hover: border darkens to navy, translateY(-2px)
- Bottom-pinned stat in DM Mono, red, uppercase, 0.625rem

### Icons
- Solid filled shapes only — speaks the same language as the blaze
- Navy fill (`--balise-navy`)
- 20–24px display size
- Sit inside a 36px square with red-soft background

### Status / metric grid
- Bordered container, light gray (`--balise-paper-2`) background
- 3 cells separated by 1px navy-10% dividers
- Each cell: icon (22px, red filled), title (Manrope 600, 0.9375rem), sub-label (DM Mono, uppercase, 0.6875rem)

### Section dividers
Between major sections, render the mark itself as a tiny vertical centered divider:
```html
<div class="blaze-divider">
  <svg viewBox="0 0 100 130" width="14" height="18">
    <rect x="14" y="0"  width="72" height="50" rx="4" fill="#C8362F"/>
    <rect x="14" y="62" width="72" height="68" rx="4" fill="#0F2742"/>
  </svg>
</div>
```
Use sparingly — once or twice per page, never as a frame element.

### CTA button
- Background: `--balise-red`
- Hover: `--balise-red-hover`
- Color: white/paper
- Padding: 16px 28px 16px 24px
- Border-radius: 4px
- Font: Manrope 700, 1.0625rem
- Include an arrow `→` that animates 3px right on hover

---

## 5 · Bilingual rules

- **Mark never changes** between languages.
- Wordmark switches: "Balise AI" (en) ↔ "Balise IA" (fr).
- Use `<span class="ai">AI</span>` / `<span class="ai">IA</span>` for the suffix so styling is consistent.
- "Naviguez la réglementation municipale." / "Navigate municipal regulations." — that's the brand headline pattern: action verb that activates the navigation metaphor + the regulatory domain. Use parallel phrasing wherever an H1 is needed in the app.

---

## 6 · The kit

The full visual identity kit lives separately and contains:
- SVG masters (mark, mono variants, EN + FR lockups)
- PNG exports (16 → 1024px)
- Favicons (16, 32, 48, 192, apple-touch-icon)
- Social avatars (paper/navy/red colorways) + 1200×630 OG images (EN + FR)
- README with usage rules

Pull from the kit; don't redraw the mark.

---

## 7 · Migration checklist for the app

- [ ] Replace existing logo files with `balise-mark.svg` and the relevant lockup SVGs
- [ ] Add the four CSS custom properties for navy/red/paper/ink at the root
- [ ] Replace any existing red value (`#9C1B20`, `#A40000`, etc.) with `#C8362F`
- [ ] Load Manrope + DM Mono from Google Fonts; replace system font stacks
- [ ] Audit icons: replace stroked/outlined icons with solid filled equivalents in navy
- [ ] Replace any beige/cream background with `#ffffff` (`--balise-paper`)
- [ ] Apply the card pattern (border + red blaze tab + 36px icon-on-red-tint) to existing feature/audience/info cards
- [ ] Update CTA buttons to the new red + arrow pattern
- [ ] If the app surfaces jurisdictions, port the jurisdiction-band pattern
- [ ] Verify both FR and EN lockups render correctly in their respective locales

---

## 8 · References

- Splash reference implementation: `splash/index.html` (FR) and `splash/index_en.html` (EN)
- Visual kit: `kit/` (provided separately)
- Logo brand sheet: `Balise Logo Final.html` (3-page PDF available)

When implementing a new screen in the app, **open the splash first** and match its language — its margins, its rhythm of label → content → divider, its restraint with red, its solid-fill icon style. If a pattern isn't covered here, infer it from the splash before inventing something new.
