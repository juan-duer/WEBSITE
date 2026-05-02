# SNOVIS Website (snovis.ai)

Static landing page + legal pages for **SNOVIS e.K.**, KI-Telefonassistent für deutsche Betriebe.

## What's in this bundle

| File | Purpose |
|---|---|
| `index.html` | Main landing page (hero, use cases, features, DSGVO, pricing, pilot, FAQ, footer) |
| `impressum.html` | Impressum nach § 5 TMG + § 18 MStV |
| `datenschutz.html` | Datenschutzerklärung nach Art. 13/14 DSGVO |
| `agb.html` | Allgemeine Geschäftsbedingungen (B2B SaaS, KI-spezifisch) |
| `og-card.png` | Open Graph share image (1200x630), referenced by `og:image` and `twitter:image` meta tags |
| `robots.txt` | Allow-all crawlers + sitemap reference |
| `sitemap.xml` | Sitemap for Google / Bing |
| `DESIGN.md` | Design tokens + brand rationale in [DESIGN.md format](https://github.com/google-labs-code/design.md). Read by Claude Code / other AI agents to produce on-brand UI changes. |

**No build step. No framework. No node_modules.** Just static files. Drop into Vercel and go.

## Deploy to Vercel

### 1. Push to GitHub

```bash
cd /path/to/this/folder
git init
git add .
git commit -m "Initial: SNOVIS website"
git branch -M main
git remote add origin git@github.com:YOUR_USERNAME/snovis-website.git
git push -u origin main
```

### 2. Import to Vercel

1. Go to <https://vercel.com/new>
2. Click **Import** next to your GitHub repo
3. Framework Preset: **Other**
4. Build Command: *(leave empty)*
5. Output Directory: *(leave empty, defaults to repo root)*
6. Click **Deploy**

You should now have a temporary URL like `snovis-website-xxx.vercel.app`. Test it.

### 3. Add the snovis.ai custom domain

1. In your Vercel project, **Settings** > **Domains**
2. Add `snovis.ai` and `www.snovis.ai`
3. Update DNS at your registrar (Vercel shows the exact records)
4. Wait for DNS propagation (5 min to 1 hour)
5. Vercel issues a free SSL certificate automatically

### 4. Verify after deployment

Open `https://snovis.ai/` and check:

- [ ] Main page renders with logo, hero, all sections, footer
- [ ] `/impressum.html` opens
- [ ] `/datenschutz.html` opens
- [ ] `/agb.html` opens
- [ ] All footer links work
- [ ] Demo CTAs open mailto with prefilled subject + body
- [ ] Phone CTAs open dialer
- [ ] OG share image, test at <https://www.opengraph.xyz/?url=https://snovis.ai>
- [ ] schema.org, test at <https://search.google.com/test/rich-results>
- [ ] Lighthouse perf, Chrome DevTools > Lighthouse > Mobile, expect 90+ across the board

## Important: Legal Review Required

The legal documents (Impressum, Datenschutzerklärung, AGB) are professional first drafts based on best-practice German B2B SaaS templates. **Before signing your first paying customer (especially a Praxis), have a German IT-Anwalt review them.**

Specific clauses to flag for the lawyer:

- **AGB § 11 Abs. 5**, KI-Output-Haftungsausschluss (novel territory; § 307 BGB scrutiny)
- **AGB § 4 Abs. 3**, Notfall-Risikoverteilung pushed to customer
- **AGB § 14**, AGB-Änderungsklausel mit fingierter Zustimmung (BGH XI ZR 26/20)
- **AGB § 6**, Kündigung "ohne Frist" beidseitig
- **AGB § 5 Abs. 7**, Sperrungsrecht bei Zahlungsverzug
- **Datenschutz § 5**, Vercel (USA) hosting + DPF + SCC
- **Datenschutz § 10.3 / 10.4**, WhatsApp Business + Google Meet disclosures

A 2 to 4 hour review at a German IT-Anwalt typically runs **€600 to €1,500**. Cheap insurance against an Abmahnung or lost lawsuit.

### After first medical-practice customer

You will likely trigger **DPO obligation** under Art. 37(1)(c) DSGVO once you process Gesundheitsdaten "in großem Umfang". Externe Datenschutzbeauftragte cost ~€150 to €400/month for KMU. Plan for this.

## Tech notes

- **Self-hosted fonts** (DM Sans, Inter, JetBrains Mono) embedded as base64 data URIs. Zero third-party requests, makes the privacy claim "Schriftarten lokal eingebunden" actually true.
- **No cookies, no analytics, no tracking**. DSGVO-clean by default. No banner needed.
- **Logo + favicon** embedded as data URIs. Zero external requests for branding.
- **schema.org JSON-LD** in `<head>`. Organization + Service + WebSite + FAQPage. Should produce rich Google results.
- **Open Graph + Twitter Card** meta tags wired up. Shared link previews work everywhere.
- **All CTAs** are `mailto:` (with prefilled subject + body) or `tel:`. No form-handling backend needed.

### Future swap-outs

When you build/connect a real demo-booking system (Cal.com, Google Calendar embed, custom):
- Replace the 5 `mailto:juan@snovis.com?subject=SNOVIS%20Demo-Termin&body=...` links in `index.html` with the booking URL.
- Update Datenschutz § 10 sections accordingly.

When you have real customer logos / testimonials:
- Update the pilot section in `index.html` (currently says "10 Pilotplätze noch verfügbar").
- Replace with a real counter or remove once full.

### File checksums (for sanity)

Each HTML file is roughly 480-500 KB on disk because of embedded fonts (~360 KB shared) and embedded images (logo + favicon). On the wire after gzip, that's ~150 KB per page. Acceptable.

**Stand:** Mai 2026
**Built for:** SNOVIS e.K., Köln
**Domain:** snovis.ai
