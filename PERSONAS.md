Here is the complete, production-ready **`USER_PERSONAS.md`** file. It defines the target users, their operating realities, core jobs-to-be-done, and specific testing and review criteria for the engineering and design validation phases.

***

# USER_PERSONAS.md
**Project:** RELIEF aid FOUNDATION (-RaF-)  
**Purpose:** UX Design Validation, Acceptance Testing, and Post-Build QA  
**Operating Context:** Base Camp, Rwamwanja Refugee Settlement & Global Humanitarian Donors  

---

## Persona Matrix Overview

| Persona | Archetype | Primary Device & Network | Core Touchpoint | Critical Success Metric |
| :--- | :--- | :--- | :--- | :--- |
| **1. The Institutional Due Diligence Officer** | Vetting & Compliance | Desktop / Office Fiber (Kampala / Geneva / London) | `/about/governance` & `/reports` | Access verified governance & download monthly PDF in $< 3$ clicks |
| **2. The Global Philanthropic Donor** | Direct Giving & Story Reader | Smartphone / High-Speed Wi-Fi (US / UK / Diaspora) | `/stories` & `/donate` | Read field dispatch & complete donation in $< 60$ seconds |
| **3. The Local Partner & Mobile Giver** | Settlement Community / Regional | Low-to-Mid Android / 3G Mobile Data (Kamwenge / Western UG) | Homepage & MTN/Airtel MoMo Checkout | Page load $< 2.5\text{s}$; seamless Mobile Money checkout |
| **4. The Refugee Leadership (Executive Director)** | Client & Community Ambassadorship | Android Phone / Settlement Connectivity | Entire Public Site via WhatsApp Sharing | Professional "credibility passport" to present to visiting delegations |
| **5. The Retainer Webmaster (Our Partnership)** | System Maintenance & Publishing | Laptop / Hotspot & Office Broadband | `/admin` / `/webmaster` Portal | Upload report, update live counters, and publish blog post in $< 10\text{ min}$ |

---

## 1. Persona 1: The Institutional Due Diligence Officer

```
Name: Elena Vance (38)
Role: Senior Grants & Localization Compliance Officer
Organization: International NGO Consortium / Bilateral Foundation
Location: Kampala / Nairobi / Geneva
Device: ThinkPad X1 Carbon / MacBook Pro (Desktop Chrome)
Network: High-speed corporate fiber
```

### Context & Mindset
Elena reviews 20–30 grant applications monthly under the Grand Bargain localization agenda. When R-a-F submits an expression of interest or partnership pitch, Elena is not looking for marketing buzzwords. Her single job is to answer: **"Is this entity legally compliant, operationally active, and low risk for our compliance audit?"**

### Core Jobs To Be Done (JTBD)
1. Verify the organization's authentic physical footprint in Rwamwanja Base Camp.
2. Review the leadership structure to confirm it is genuinely refugee-women-led.
3. Inspect and download the latest monthly activity reports to evaluate quantitative metric consistency.
4. Locate the Child Safeguarding (PSEA) policy and financial governance framework.

### Primary Frustrations / Red Flags
- Having to search through a generic social media page for basic organizational facts.
- Bureaucratic registration certificates slapped across the homepage hero like a flyer.
- Websites that haven't been updated in 6 months (signals a defunct project).
- Inability to find downloadable documentation.

### User Journey & Acceptance Testing Criteria
- [ ] **Discovery:** Enters site via direct link on a grant proposal.
- [ ] **Verification:** Finds the `/about/governance` page from the main navigation in $\le 2$ clicks.
- [ ] **Audit Trail:** Navigates to `/reports`, filters by "Monthly Activity", and downloads the latest PDF in under 15 seconds.
- [ ] **Compliance Sign-Off:** Reviews the minimalist footer to confirm non-profit registration metadata and operational coordination notes.

---

## 2. Persona 2: The Global Philanthropic Donor

```
Name: Marcus Sterling (44)
Role: Tech Executive & Independent Philanthropist
Location: London, UK / Washington DC, USA
Device: iPhone 15 Pro / Safari Mobile
Network: High-speed 5G / Home Wi-Fi
```

### Context & Mindset
Marcus contributes $500–$2,000 annually to grassroots community organizations. He is weary of traditional aid bureaucracies where 40% of money is lost to overhead. He wants direct, dignified, and emotionally resonant connection to grassroots transformation.

### Core Jobs To Be Done (JTBD)
1. Read a compelling field dispatch about a woman or young mother overcoming adversity in Rwamwanja.
2. Confirm that the organization does not practice exploitative "poverty porn."
3. Make an immediate, secure credit card donation (in USD or GBP).
4. Receive an instant confirmation and digital receipt for his contribution.

### Primary Frustrations / Red Flags
- Clunky donation forms that force account creation.
- Payment gateways that fail when using international credit cards on African URLs.
- Lack of clarity on where funds actually go.

### User Journey & Acceptance Testing Criteria
- [ ] **Engagement:** Lands on a story from a social media link (`/stories/bahati-agribusiness-harvest`).
- [ ] **Storytelling:** Reads a cleanly formatted article with photo carousel and reading time indicator.
- [ ] **Conversion Trigger:** Clicks the in-article CTA block: *"Empower more women like Bahati"* -> routed directly to `/donate` with the `$50` tier pre-selected.
- [ ] **Checkout:** Selects "Credit Card", completes payment via the Pesapal/Flutterwave secure modal without redirection errors.
- [ ] **Receipting:** Instantly views the on-screen confirmation and fund allocation chart (85% Direct Program / 15% Operations).

---

## 3. Persona 3: The Local Partner & Mobile Money Giver

```
Name: Grace Kyomugisha (31)
Role: Agricultural Extension Officer / Local Supporter
Location: Kamwenge Town / Fort Portal / Rwamwanja Host Community
Device: Tecno Spark 10 / Infinix Hot 30 (Android)
Network: 3G / Intermittent 4G (Airtel / MTN Uganda)
Screen: 720p resolution, used outdoors under bright sun
```

### Context & Mindset
Grace works with farmer groups across Kamwenge district and collaborates with R-a-F's agribusiness plot. She visits the website on her phone while in the field to check upcoming literacy dates or contribute UGX 50,000 via Mobile Money to support a local young mother cohort.

### Core Jobs To Be Done (JTBD)
1. Load the site fast without burning through her mobile data bundle.
2. Read text clearly on a budget screen in harsh sunlight.
3. Access program updates on Agribusiness and VSLAs.
4. Donate or contribute local funds via MTN MoMo or Airtel Money.

### Primary Frustrations / Red Flags
- Heavy, bloated websites that stall or crash budget mobile browsers.
- Low-contrast light grey text that is impossible to read outdoors.
- Payment portals that only accept international credit cards and reject Ugandan Mobile Money.

### User Journey & Acceptance Testing Criteria
- [ ] **Performance:** First Contentful Paint (FCP) $\le 2.0$ seconds on simulated 3G connection; page payload $\le 1.2$ MB total.
- [ ] **Contrast & Accessibility:** Text meets WCAG AA contrast against `#F8FAFC` background; buttons have a minimum touch target of $48 \times 48\text{ px}$.
- [ ] **Navigation:** Mobile hamburger menu opens fluidly with thumb reach.
- [ ] **MoMo Payment:** Selects `UGX`, picks `UGX 50,000`, enters phone number, and receives a prompt for the USSD push PIN cleanly.

---

## 4. Persona 4: The Executive Director (Client Leadership)

```
Name: Furaha (42)
Role: Founder & Executive Director, RELIEF aid FOUNDATION
Location: Base Camp, Rwamwanja Refugee Settlement
Device: Samsung Galaxy A-series (Android)
Network: Settlement mobile data / Base Camp office Wi-Fi
```

### Context & Mindset
Furaha is a respected refugee community leader. When meeting visiting officials from UNHCR, OPM, or INGO country directors at the Base Camp office, she pulls out her phone to show them R-a-F’s work. The website is her **institutional badge of authority and credibility**.

### Core Jobs To Be Done (JTBD)
1. Share direct links to official monthly reports via WhatsApp with visiting donors.
2. Show partners that R-a-F is a transparent, modern organization with an active digital record.
3. Ensure the community’s work is portrayed with dignity and pride.

### Primary Frustrations / Red Flags
- Broken links or outdated information when showing the site to partners.
- Having her organization dismissed as an "unregistered informal group."
- Complex interfaces she cannot easily navigate on her phone.

### User Journey & Acceptance Testing Criteria
- [ ] **Mobile Sharing:** Can copy a clean URL from the `/reports` page into WhatsApp with an automated OpenGraph preview showing the official logo and title.
- [ ] **Showcase:** Displays the Homepage Live Impact Counter (`100+ Beneficiaries`, `4 Programs`) during physical field meetings.
- [ ] **Dignity Review:** Verifies that community photography honors beneficiaries rather than depicting helplessness.

---

## 5. Persona 5: The Retainer Webmaster (Our Partnership - Scenario A)

```
Name: The Partnership Technical Lead (Us)
Role: Systems Webmaster & Ongoing Retainer Lead
Location: Uganda (Kampala / Field Operations)
Device: Laptop (Mac / Windows / Chrome DevTools)
Network: Broadband / Hotspot
```

### Context & Mindset
Operating under the Scenario A Retainer agreement, our partnership is responsible for the site’s health, monthly report releases, and live metric updates. We need an administrative backend (`/admin`) that allows us to execute monthly tasks in minutes without opening a code editor.

### Core Jobs To Be Done (JTBD)
1. Log into the secure dashboard at `/admin` on the 1st of every month.
2. Upload the newly formatted Monthly Activity PDF and set its metadata (period, metrics, summary).
3. Increment the live site-wide impact counters (e.g., updating beneficiaries from 104 to 128).
4. Publish a 600-word field dispatch to the Advanced Blog.
5. Review the automated system health and backup status.

### Primary Frustrations / Red Flags
- Hardcoded counters that require code commits and redeployments for simple number changes.
- Slow or buggy file uploaders for PDF documents.
- Complicated CMS platforms with unnecessary corporate bloat.

### User Journey & Acceptance Testing Criteria
- [ ] **Authentication:** Accesses `/admin` via secure password/token session.
- [ ] **One-Click Metric Update:** Adjusts `Monthly Beneficiaries` input field $\rightarrow$ clicks `Save` $\rightarrow$ verifies instant update on the live homepage without code deployment.
- [ ] **PDF Vault Upload:** Uploads a 2 MB PDF report with metadata in $\le 60$ seconds; verifies it displays immediately at `/reports`.
- [ ] **Blog Publishing:** Pastes Markdown field dispatch, uploads 1 cover image, tags `Agribusiness`, hits `Publish` $\rightarrow$ article appears at `/stories/[slug]` with an active donation CTA.
- [ ] **Maintenance Audit:** Checks the health panel: verifies SSL active, gateway connection live, and triggers a database backup snapshot.

---

## 6. QA & Testing Checklist (Cross-Persona Validation)

Use this checklist before presenting the completed platform to the Executive Director:

```text
[ ] PERSONA 1 (DONOR AUDIT):
    - Can Elena find the PSEA and financial policies in under 30 seconds?
    - Are the PDF reports authentic, clear, and download-ready?
    - Is the footer legally complete with registration and settlement coordination metadata?

[ ] PERSONA 2 (INTERNATIONAL GIVER):
    - Does the blog story render cleanly with high editorial legibility?
    - Does the in-article donation button correctly carry over the selected donation amount?
    - Does the card checkout process function without country-blocking errors?

[ ] PERSONA 3 (LOCAL MOBILE USER):
    - Does the site achieve a Lighthouse Mobile Performance score of ≥ 85?
    - Does the MTN/Airtel Mobile Money option display correctly under the UGX toggle?
    - Are all touch targets at least 48px high on mobile?

[ ] PERSONA 4 (EXECUTIVE DIRECTOR):
    - Does the website present an inspiring, dignity-first image of refugee women leaders?
    - Do social share links render with proper logo previews on WhatsApp and LinkedIn?

[ ] PERSONA 5 (WEBMASTER RETAINER):
    - Can all homepage counters be updated dynamically from the /admin portal?
    - Does uploading a new monthly report take under 2 minutes end-to-end?
    - Does the system backup trigger successfully?
```
