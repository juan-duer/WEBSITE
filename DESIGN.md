---
version: alpha
name: SNOVIS
description: >
  Dark editorial design system for SNOVIS, a DSGVO-konformer KI-Telefonassistent
  for German B2B businesses. The aesthetic balances Berlin precision with
  journalistic gravitas, dark-mode native, brand accent currently royal blue
  (subject to change without altering the rest of the system).

colors:
  # Surfaces (dark by design)
  bg: "#030303"
  window-top: "#0d0d10"
  window-bottom: "#080809"
  pinstripe: "#FFFFFF03"

  # Foreground text
  text: "#FFFFFF"
  text-200: "#e5e7eb"
  text-300: "#d1d5db"
  text-400: "#9ca3af"
  text-500: "#6b7280"
  text-600: "#4b5563"

  # Borders (always white-on-dark at low opacity)
  border-subtle: "#FFFFFF0F"
  border-soft: "#FFFFFF14"
  border-medium: "#FFFFFF1F"
  border-strong: "#FFFFFF2E"

  # Brand accent (royal blue today, swappable in future)
  accent: "#2563eb"
  accent-dim: "#1d4ed8"
  accent-bright: "#3b82f6"
  accent-glow: "#2563EB80"

  # Trust accent (green, for verified / DSGVO / EU info)
  trust: "#6ee7b7"
  trust-bright: "#7DD3A0"
  trust-bg: "#7DD3A014"
  trust-border: "#7DD3A02E"

  # Ambient accent (slate, for neutral / infrastructure / global signals)
  ambient: "#94a3b8"
  ambient-bg-top: "#1e293b"
  ambient-bg-bottom: "#0f172a"

typography:
  # Headlines, hero copy, section titles
  display:
    fontFamily: DM Sans
    fontSize: 4.25rem
    fontWeight: 300
    lineHeight: 1.02
    letterSpacing: "-0.05em"
  h1:
    fontFamily: DM Sans
    fontSize: 3rem
    fontWeight: 300
    lineHeight: 1.05
    letterSpacing: "-0.045em"
  h2:
    fontFamily: DM Sans
    fontSize: 2.25rem
    fontWeight: 400
    lineHeight: 1.1
    letterSpacing: "-0.03em"
  h3:
    fontFamily: DM Sans
    fontSize: 1.5rem
    fontWeight: 500
    lineHeight: 1.2
    letterSpacing: "-0.02em"
  h4:
    fontFamily: DM Sans
    fontSize: 1.0625rem
    fontWeight: 500
    lineHeight: 1.3
    letterSpacing: "-0.01em"

  # Body / supporting prose (Inter)
  body-lg:
    fontFamily: Inter
    fontSize: 1.0625rem
    fontWeight: 300
    lineHeight: 1.65
  body-md:
    fontFamily: Inter
    fontSize: 0.9375rem
    fontWeight: 300
    lineHeight: 1.65
  body-sm:
    fontFamily: Inter
    fontSize: 0.8125rem
    fontWeight: 400
    lineHeight: 1.55

  # Eyebrows, pill labels, category markers (always uppercase mono)
  eyebrow:
    fontFamily: JetBrains Mono
    fontSize: 0.72rem
    fontWeight: 500
    letterSpacing: "0.18em"
    fontFeature: '"ss01" off'
  pill:
    fontFamily: JetBrains Mono
    fontSize: 0.625rem
    fontWeight: 500
    letterSpacing: "0.14em"

rounded:
  none: 0
  sm: 4px
  md: 8px
  lg: 12px
  xl: 24px
  window: 32px
  pill: 9999px

spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
  xl: 32px
  "2xl": 48px
  "3xl": 80px

components:
  # The flagship "window" section frame, every page section uses this
  window:
    backgroundColor: "{colors.window-top}"
    rounded: "{rounded.window}"
    padding: "{spacing.xl}"
  window-border:
    backgroundColor: "{colors.border-medium}"

  # Buttons follow X.com auth-flow spec, 300px x 40px
  button-primary:
    backgroundColor: "{colors.text}"
    textColor: "{colors.bg}"
    rounded: "{rounded.pill}"
    padding: "10px 20px"
    height: 40px
  button-primary-hover:
    backgroundColor: "{colors.text-200}"
  button-secondary:
    backgroundColor: "transparent"
    textColor: "{colors.text-200}"
    rounded: "{rounded.pill}"
    padding: "10px 20px"
    height: 40px
  button-secondary-hover:
    backgroundColor: "{colors.border-subtle}"

  # The signature green trust pill, used for DSGVO / EU / verified signals
  trust-pill:
    backgroundColor: "{colors.trust-bg}"
    textColor: "{colors.trust}"
    rounded: "{rounded.pill}"
    padding: "7px 16px"
    typography: "{typography.pill}"

  # Eyebrow labels above section headlines
  eyebrow-label:
    textColor: "{colors.text-400}"
    typography: "{typography.eyebrow}"

  # Stack-cards used in DSGVO infrastructure section
  stack-card:
    backgroundColor: "#FFFFFF09"
    rounded: "{rounded.lg}"
    padding: "18px 20px"
  stack-card-border:
    backgroundColor: "{colors.border-subtle}"

  # Pricing-card with diagonal gradient border (royal blue to white)
  pricing-card:
    backgroundColor: "#09090BD9"
    rounded: "{rounded.xl}"
    padding: "32px"
---

## Overview

SNOVIS is a DSGVO-konformer KI-Telefonassistent for German B2B businesses, hauptsächlich Praxen, Friseure, Kanzleien, Werkstätten. The visual system reflects this audience: serious, German, technically credible, no marketing fluff. Three principles drive every decision:

1. **Editorial gravitas, not SaaS-marketing.** Light-weight DM Sans headlines, generous whitespace, restrained motion. Reads like Wired or The Atlantic, not Mailchimp.
2. **Dark-mode native.** Pure black canvas (#030303) with subtle vertical gradients on window surfaces. Avoid pure-white backgrounds outright. Light text on dark surfaces is the default state, not an inverted theme.
3. **Trust through specificity.** Stack-flags name actual providers (Hetzner Frankfurt, Vertex AI Frankfurt, Telnyx, Deepgram EU). Eyebrow labels in JetBrains Mono uppercase signal "this is documented, this is real." Generic stock imagery is forbidden.

The brand accent is currently royal blue (`{colors.accent}`). It will likely evolve. The rest of the system, neutral palette, typography, spacing, component shapes, must continue to work when the accent changes. Treat the accent as a single replaceable token, never hardcode the hex.

## Colors

Dark-mode design with high-contrast neutrals and three semantic accents.

### Surfaces

The page sits on `bg` (#030303), an almost-black with a faint 45-degree pinstripe overlay (`pinstripe` at ~3 alpha). Sections live inside `window` containers with a vertical gradient from `window-top` (#0d0d10) to `window-bottom` (#080809). The 1-pixel difference between `bg` and `window-top` creates a subtle "lifted" feel that you read more than see.

### Foreground

Five tints of white-on-dark, descending from full white (#FFFFFF) to slate-grey (#4b5563). Use `text` only for the most important on-screen text (hero headline, primary buttons). Body copy lives at `text-300`. Captions and metadata at `text-400` or below.

### Borders

Borders are never solid colors, always white at low opacity (`border-subtle` to `border-strong`). This keeps them feeling like they emerged from the surface rather than being painted on. On gradient-bordered components (pricing-card), the border itself becomes a gradient from accent to white at very low alpha.

### Accent (currently royal blue)

`accent` (#2563eb) is the brand voice color. It carries primary CTAs, focus rings, mesh-blob atmospheres in the hero, and the gradient on the pricing-card border. **It is the single token that may change to reposition the brand.** When it does, do not introduce variant blues. Replace one color, propagate.

### Trust (green)

`trust` (#6ee7b7) and `trust-bright` (#7DD3A0) signal verified, compliant, EU-hosted, GDPR-clean. Uses: Frankfurt-Hosting stack-flags, the "10 Pilotplätze, noch verfügbar" pill, glowing dots in the hero trust-row, the OG-card pill ("100% DSGVO, EU-GEHOSTET"). **Reserve green strictly for this semantic.** It is never decorative.

### Ambient (slate)

`ambient` (#94a3b8) reads as neutral / supportive / infrastructure. Uses: the back-most globe icon in the hero trust-pill stack (the icon that recedes behind the front-most shield). Slate is what the eye should pass over, not stop on.

## Typography

Three families, each with one job:

- **DM Sans** is the brand voice. Headlines, page titles, brand wordmark. **Always weight 300 for hero / display, 400-500 for sub-headlines, 700 only for the wordmark logo**. The light weight is what gives the site its editorial feel, do not bold up.
- **Inter** is for prose. Body text, descriptions, FAQ answers, legal copy. Weight 300 for the dim-on-dark default, 400 for emphasis.
- **JetBrains Mono** is for eyebrows, pill labels, category markers, the snovis.ai URL stamp. **Always uppercase, always wide-tracked (`letterSpacing` 0.14-0.18em).** Never use it for prose.

Hero headlines target `clamp(2.5rem, 9vw, 4.25rem)` with `letter-spacing: -0.05em` and `line-height: 1.02`. The tight tracking + tight leading is what produces the "newspaper masthead" feel; do not loosen.

All three fonts are self-hosted (Latin + Latin-Ext only) and embedded as base64 data URIs in production. No request ever leaves the page for typography. This is a DSGVO claim; honor it.

## Layout

The page lives inside `surface`, an outer container with the 45-degree pinstripe and `padding: 12px` (mobile) → `24px` (tablet) → `32px` (desktop). Inside `surface`, every section is a `window`, a rounded rect with a 1px gradient border (white 24% at top → 3% at bottom) and the `window-top → window-bottom` vertical gradient inside. Sections never run edge-to-edge; they always sit inside the surface's padding.

### Spacing scale

Spacing tokens are tight on mobile and breathe on desktop. The site uses:

- `spacing.xs / sm` for inline gaps inside pills, between icon and text.
- `spacing.md / lg` for separation between an eyebrow and the headline below it, between paragraph blocks.
- `spacing.xl / 2xl` for the gap between sections (the `padding` on the `window` itself, plus the gap between adjacent windows).
- `spacing.3xl` for the hero's vertical breathing room above and below.

Rule of thumb: **the more important an element, the more space it gets above and below.** Hero headlines have the most negative space. Captions have almost none.

### Mobile

Single column, full-width windows. The desktop "side rails" (the dotted vertical edge-frame lines) get hidden or pulled to the screen edge. Hero atmosphere blobs are pinned to GPU layers (`transform: translate3d(0,0,0)`) to keep their blur from escaping the rounded clip on iOS Safari.

## Elevation & Depth

Three depth signals, in order of subtlety:

1. **The pinstripe overlay** on `surface` adds visual depth without color. Its 3% alpha is intentional, do not strengthen.
2. **The vertical gradient inside `window`** (`window-top → window-bottom`) creates a "lit from above" sensation. The 1px gradient border around it picks up the same direction.
3. **The drop shadow** on `window` (`0 28px 92px rgba(0,0,0,0.46)`) is the only true shadow in the system. Component-level cards do not get their own shadow; they sit flat inside their parent window.

Mesh-blob atmosphere (the blue radial gradients in the hero) is decorative depth, not informational. It can be removed entirely without breaking the page.

## Shapes

Three radii do almost everything:

- `{rounded.window}` (32px) for the section windows.
- `{rounded.xl}` (24px) for major cards (pricing-card, pilot-card).
- `{rounded.pill}` (9999px) for buttons, badges, trust-pills, all rounded-tag elements.

`{rounded.lg}` (12px) is reserved for stack-cards (the smaller infrastructure cards in the DSGVO section). `{rounded.sm}` (4px) is for inline tags, code chips, small-detail elements only. **There is no in-between**, do not introduce 16px or 20px radii.

Corners are always uniform (no asymmetric rounding). When a child element sits on the boundary of a parent (e.g., a pill straddling a card edge), the child uses `{rounded.pill}` and the parent uses its own radius; the visual relationship comes from contrast in shape, not from matching curves.

## Components

### button-primary

White-on-dark pill button at 300x40px. Used for the most important action on a screen ("Demo-Termin buchen", "Pilotplatz anfragen"). On hover, lighten the background slightly toward `text-200`. **Only one button-primary per visible viewport.**

### button-secondary

Transparent fill, soft white border, white-on-dark text. Same dimensions as button-primary. Used as the alternative to a primary action ("Live mit der KI sprechen", "Anrufen").

### trust-pill (the green DSGVO pill)

The signature trust marker. Green-tinted background, green border, green-glow dot, JetBrains Mono uppercase text in light green. Variants:
- "10 PILOTPLÄTZE, NOCH VERFÜGBAR" on the pilot section.
- "100% DSGVO, EU-GEHOSTET" on the OG share card.
- "FRANKFURT, DE" inside infrastructure stack-cards.

Always center-aligned within its container. Always with a single dot to the left. Never colored differently from `{colors.trust}`.

### eyebrow-label

A short uppercase mono label that appears above a section headline. Examples: "DAS PROBLEM", "FUNKTIONEN IM ÜBERBLICK", "DSGVO & EU-HOSTING". Always in `text-400` (mid-grey), never in the brand accent. Communicates "you are entering a new section" without competing with the headline.

### stack-card

Smaller cards used inside the DSGVO/EU-hosting section to enumerate sub-providers. Subtle white-on-dark background, soft border, `{rounded.lg}` corners, 18-20px padding. Each carries a green trust-pill at the top, then an h4 + body-sm description.

### pricing-card

The most ornamented card in the system. Diagonal gradient border (accent to white at low alpha), 32px padding, dark fill. Inside, a centered blue badge ("Pilot-Tarif, 10 Plätze"), pricing tier name in DM Sans 500, big amount, then a checked feature list. **One pricing card per page maximum.**

## Do's and Don'ts

### Do

- Use the trust accent (green) only for DSGVO / verified / EU / available signals. Treat it like a semantic, not a decoration.
- Keep DM Sans headlines at weight 300 unless they are the brand wordmark. The light weight is the brand voice.
- Compose with the existing tokens. If a value isn't on the spacing scale, it doesn't belong in this design.
- Self-host fonts and never link to fonts.googleapis.com. The DSGVO claim depends on this.

### Don't

- Don't introduce blue variants. There is one accent. If you need a different blue, request a token change, do not freelance.
- Don't use solid `border` colors. Borders are always white-on-dark at controlled opacity.
- Don't put pure white (#FFFFFF) backgrounds anywhere on the marketing site. The system is dark-mode native.
- Don't use Inter for headlines or DM Sans for body copy. Each family has one job.
- Don't add drop shadows to non-window elements. The system has exactly one shadow style and it lives on `window`.
- Don't bold-weight the hero headline. The light weight is intentional.

---

**Spec version:** alpha
**Built for:** SNOVIS e.K., Köln
**Domain:** snovis.ai
**Last reviewed:** Mai 2026
