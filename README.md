# SNOVIS Website (snovis.ai)

Static landing page + legal pages for **SNOVIS e.K.** — KI-Telefonassistent für deutsche Betriebe.

## What's in this bundle

| File | Purpose |
|---|---|
| `index.html` | Main landing page (hero, use cases, features, DSGVO, pricing, pilot, FAQ, footer) |
| `impressum.html` | Impressum nach § 5 TMG + § 18 MStV |
| `datenschutz.html` | Datenschutzerklärung nach Art. 13/14 DSGVO |
| `agb.html` | Allgemeine Geschäftsbedingungen (B2B SaaS, KI-spezifisch) |
| `og-card.png` | Open Graph share image (1200×630) — referenced by `og:image` and `twitter:image` meta tags |
| `robots.txt` | Allow-all crawlers + sitemap reference |
| `sitemap.xml` | Sitemap for Google / Bing |

**No build step. No framework. No node_modules.** Just static files. Drop into Vercel and go.

---

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
5. Output Directory: *(leave empty — defaults to repo root)*
6. Click **Deploy**

You should now have a temporary URL like `snovis-website-xxx.vercel.app`. Test it.

### 3. Add the snovis.ai custom domain

1. In your Vercel project → **Settings** → **Domains**
2. Add `snovis.ai` and `www.snovis.ai`
3. Vercel shows the DNS records you need. At your registrar:
   - **A record** for `snovis.ai` → `76.76.21.21`
   - **CNAME record** for `www.snovis.ai` → `cname.vercel-dns.com`
4. Wait for DNS propagation (usually 5 min – 1 hour)
5. Vercel automatically issues a free SSL certificate via Let's Encrypt

### 4. Verify after deployment

Open `https://snovis.ai/` and check:

- [ ] Main page renders with logo, hero, all sections, footer
- [ ] `/impressum.html` opens
- [ ] `/datenschutz.html` opens
- [ ] `/agb.html` opens
- [ ] All footer links work
- [ ] Demo CTAs open mailto with prefilled subject + body
- [ ] Phone CTAs open dialer
- [ ] **OG share image** — test at <https://www.opengraph.xyz/?url=https://snovis.ai>
- [ ] **schema.org** — test at <https://search.google.com/test/rich-results>
- [ ] **Lighthouse perf** — Chrome DevTools → Lighthouse → Mobile, expect 90+ across the board

---

## ⚠️ Before signing your first paying customer

The legal documents (Impressum, Datenschutzerklärung, AGB) are **professional first drafts** based on best-practice German B2B SaaS templates and current case law (Mai 2026), but they are **not a substitute for legal counsel**.

**Strongly recommended:** have a German IT-/Datenschutz-Anwalt review them. Especially if your first customers are **Arztpraxen** (health data = Art. 9 DSGVO special category, much higher stakes).

Specific clauses to flag for the lawyer:

- **AGB § 11 Abs. 5** — KI-Output-Haftungsausschluss. Novel territory; verify wording survives § 307 BGB scrutiny.
- **AGB § 4 Abs. 3** — Notfall-Risikoverteilung pushed to customer. Robust for B2B?
- **AGB § 14** — AGB-Änderungsklausel mit fingierter Zustimmung. BGH XI ZR 26/20 (2021) tightened these — verify still enforceable.
- **AGB § 6** — Kündigung "ohne Frist" beidseitig. Confirm reciprocity.
- **AGB § 5 Abs. 7** — Sperrungsrecht bei Zahlungsverzug.
- **Datenschutz § 5** — Vercel (USA) hosting + DPF + SCC. Schrems-III risk?
- **Datenschutz § 10.3 / 10.4** — WhatsApp Business + Google Meet disclosures (especially for Arztpraxen).

A 2–4 hour review at a German IT-Anwalt typically runs **€600 – €1,500**. Cheap insurance against an Abmahnung or lost lawsuit.

### After first medical-practice customer

You will likely trigger **DPO obligation** under Art. 37(1)(c) DSGVO once you process Gesundheitsdaten "in großem Umfang" (= more than a few small Praxen). Externe Datenschutzbeauftragte cost ~€150–400/month for KMU. Plan for this.

---

## Tech notes

- **Self-hosted fonts** (DM Sans, Inter, JetBrains Mono) embedded as base64 data URIs — zero third-party requests, makes the privacy claim "Schriftarten lokal eingebunden" actually true.
- **No cookies, no analytics, no tracking** — DSGVO-clean by default. No banner needed.
- **Logo + favicon** embedded as data URIs — zero external requests for branding.
- **schema.org JSON-LD** in `<head>` — Organization + Service + WebSite + FAQPage. Should produce rich Google results.
- **Open Graph + Twitter Card** meta tags wired up. Shared link previews work everywhere.
- **All CTAs** are `mailto:` (with prefilled subject + body) or `tel:` — no form-handling backend needed.

### Future swap-outs

When you build/connect a real demo-booking system (Cal.com, Google Calendar embed, custom):
- Replace the 5 `mailto:juan@snovis.com?subject=SNOVIS%20Demo-Termin&body=...` links in `index.html` with the booking URL.
- Update Datenschutz § 10.5 (and remove the existing 10.3 WhatsApp / 10.4 Google Meet sections if you stop using those channels).

When you have real customer logos / testimonials:
- Update the pilot section in `index.html` (currently says "10 Pilotplätze · noch verfügbar").
- Replace with a real counter or remove once full.

### File checksums (for sanity)

Each HTML file is roughly 480–500 KB on disk because of embedded fonts (~360 KB shared) and embedded images (logo + favicon). On the wire after gzip, that's ~150 KB per page. Acceptable.

---

**Stand:** Mai 2026
**Built for:** SNOVIS e.K., Köln
**Domain:** snovis.ai
