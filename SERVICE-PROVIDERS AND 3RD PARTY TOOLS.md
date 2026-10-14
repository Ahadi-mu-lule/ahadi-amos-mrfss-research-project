Here is the complete **`SERVICE_PROVIDERS_AND_THIRD_PARTY_TOOLS.md`** file. 

It is tailored specifically to Uganda’s regulatory and infrastructure landscape (Bank of Uganda payment licensing, East African CDN edge routing, and global non-profit subsidy programs like TechSoup) to ensure maximum reliability at minimal operating cost.

***

# SERVICE_PROVIDERS_AND_THIRD_PARTY_TOOLS.md
**Project:** RELIEF aid FOUNDATION (-RaF-)  
**Operational Base:** Rwamwanja Refugee Settlement, Kamwenge District, Uganda  
**Core Strategy:** Maximize free non-profit subsidies (TechSoup/Google), ensure full Bank of Uganda payment compliance, and minimize monthly infrastructure overhead so our Scenario A Webmaster Retainer remains highly profitable and sustainable.

---

## 1. Stack & Provider Overview Matrix

| Category | Primary Recommended Provider | Backup / Alternative | Cost Structure | Key Advantage for R-a-F |
| :--- | :--- | :--- | :--- | :--- |
| **Domain Registration** | **Cloudflare Registrar** or **Namecheap** | Porkbun | ~$10 – $14 / year (`.org`) | Wholesale pricing, free WHOIS privacy, rock-solid security. |
| **DNS, CDN & Security** | **Cloudflare (Free Tier)** | AWS CloudFront | **$0 / month** | Edge caching in Nairobi/Mombasa; fast loading on Uganda 3G networks. |
| **Web Hosting & CI/CD** | **Vercel (Hobby/Pro)** | **Cloudflare Pages** / Netlify | **$0 / month** (Hobby) | Instant global edge deployment, native Next.js support, automated SSL. |
| **Institutional Email & Cloud**| **Google Workspace for Nonprofits** | Microsoft 365 for Nonprofits | **$0 / month** (via TechSoup Uganda) | Free `@reliefaidfoundation.org` emails, 30 GB Drive per user, high donor trust. |
| **Uganda & Global Payments** | **Pesapal Uganda** | **Flutterwave** | 2.5% – 3.5% per transaction | Bank of Uganda licensed; handles MTN MoMo, Airtel Money, Visa & Mastercard. |
| **Reports & Media Storage** | **Cloudflare R2** | **Supabase Storage** | **$0 / month** (First 10 GB free) | **Zero egress bandwidth fees** when donors download large PDF reports. |
| **Uptime & Site Monitoring** | **Better Stack** or **UptimeRobot** | Cronitor | **$0 / month** (Free tier) | 24/7 ping monitoring; alerts webmaster instantly via email/SMS if site drops. |
| **Newsletter & Donor Comms** | **Brevo (formerly Sendinblue)** | Mailchimp | **$0 / month** (Up to 300 emails/day) | Automated email delivery of monthly PDF reports to subscribed donors. |

---

## 2. Detailed Tool Specifications & Setup Protocols

### 2.1 Domain & DNS Management
An international `.org` domain is non-negotiable for institutional credibility with UNHCR and international foundations (avoid `.com` or generic extensions for an NGO).

- **Recommended Domain:** `reliefaidfoundation.org` (Fallback: `reliefaid-uganda.org` or `rafuganda.org`).
- **Registrar:** **Cloudflare Registrar** or **Namecheap**.
- **DNS Configuration:**
  - Route all DNS records through **Cloudflare**.
  - Enable **Cloudflare Universal SSL** (Full/Strict mode) for automatic HTTPS encryption.
  - Enable **Brotli Compression** and **Early Hints** to speed up delivery over mobile data in Western Uganda.

---

### 2.2 Web Hosting & Deployment (Frontend & CMS)
- **Primary Platform:** **Vercel**
  - Connects directly to the GitHub repository (`main` branch).
  - Every time the Webmaster pushes an update, Vercel automatically builds and deploys to the global edge network in under 90 seconds.
  - Includes automated DDoS protection and dynamic image optimization.
- **Alternative:** **Cloudflare Pages** (unlimited free bandwidth and direct integration with Cloudflare R2 storage).

---

### 2.3 Institutional Email & Collaboration (The TechSoup Advantage)
Never allow the Executive Director or staff to communicate with international donors using personal `@gmail.com` or `@yahoo.com` addresses. This is one of the top reasons grant applications fail preliminary vetting.

- **Provider:** **Google Workspace for Nonprofits**
- **How to Get It for Free ($0/month instead of $6/user/month):**
  1. Register RELIEF aid FOUNDATION on **TechSoup Global (TechSoup Uganda)**.
  2. Upload R-a-F’s CBO registration certificate and OPM settlement clearance letter.
  3. Receive a TechSoup Validation Token (takes 3–5 business days).
  4. Submit the token to **Google for Nonprofits** to unlock free business Gmail accounts (`ed@reliefaidfoundation.org`, `info@reliefaidfoundation.org`, `finance@reliefaidfoundation.org`).

---

### 2.4 Payment Gateways (Uganda & Global Multi-Currency)

Collecting donations in Uganda requires a hybrid engine that handles local mobile money and international cards without triggering bank fraud blocks.

#### Primary Gateway: **Pesapal Uganda**
- **Regulatory Standing:** Formally licensed and regulated as a National Payment System Operator by the **Bank of Uganda (BoU)** [1, 2].
- **Payment Methods Supported:**
  - **Local:** MTN Mobile Money, Airtel Money (via direct USSD push).
  - **International:** Visa, Mastercard, and American Express.
- **Settlement:** Directly auto-settles into R-a-F’s official Ugandan commercial bank account (e.g., Centenary Bank, Stanbic, or Equity Bank) in UGX or USD.
- **Integration Mode:** Pesapal Standard Redirect / Seamless iFrame embedded directly into `/donate`.

#### Backup Gateway: **Flutterwave for Business (Uganda)**
- Serves as the redundancy layer if Pesapal undergoes maintenance.
- Strong coverage for cross-border African diaspora remittances (Kenya M-Pesa, Rwanda Mobile Money, UK/Europe debit cards).

#### Major Philanthropic Gifts & Bilateral Grants: **Direct Bank Wire (SWIFT)**
- For donations exceeding $1,000, card processing fees (2.9–3.5%) become unnecessarily expensive.
- The site provides a clean, copyable modal with:
  - Account Name: `RELIEF AID FOUNDATION`
  - Bank Name & Branch Code
  - SWIFT / BIC Code
  - Currency Accounts: Designated UGX & USD accounts.

---

### 2.5 Document & Media Storage (Reports & Blog Assets)

The Reports Vault needs to host multi-megabyte PDF files that will be downloaded by dozens of grant evaluators simultaneously. Standard web servers charge hefty egress fees for document bandwidth.

- **Primary Provider:** **Cloudflare R2**
  - **S3-Compatible Object Storage:** Works with standard AWS SDK libraries.
  - **The Game-Changer:** **$0 egress bandwidth fees.** Donors can download thousands of monthly PDF reports without incurring hosting bills.
  - **Free Tier:** 10 GB storage free every month (more than enough for 5+ years of monthly reports).
- **Alternative:** **Supabase Storage** (includes a built-in PostgreSQL database if dynamic querying is preferred).

---

### 2.6 Webmaster Monitoring & Retainer Infrastructure (Scenario A)

To fulfill our ongoing monthly retainer agreement without manual babysitting, we use automated monitoring tools:

- **Uptime Monitoring:** **Better Stack (formerly Better Uptime)**
  - Pings the website every 3 minutes from global nodes.
  - Sends immediate WhatsApp / SMS / Email alerts to our technical lead if the site goes down.
  - Generates a public or private status report showing 99.9% uptime (excellent proof of performance for our monthly client reporting).
- **Automated Backups:**
  - Codebase & static assets: Hosted on a private **GitHub** repository with automated version history.
  - Uploaded Reports & Database state: Weekly automated snapshots archived to Cloudflare R2.
- **Error Tracking:** **Sentry (Free Developer Tier)**
  - Captures broken links, broken donation modal submits, or failed API calls in real-time before donors complain.

---

### 2.7 Donor Communication & Report Distribution
- **Provider:** **Brevo (formerly Sendinblue)**
  - **Free Tier:** 300 emails/day forever.
  - **Use Case:**
    1. Automated transactional email sending an official branded PDF receipt whenever someone donates.
    2. Monthly Newsletter Dispatch: When the Webmaster publishes a new monthly report, a 1-click broadcast sends the summary and PDF link to all registered partner contacts.

---

## 3. Projected Operating Budget (Infrastructure Costs)

By taking advantage of non-profit tiers and modern edge architecture, we keep fixed platform costs virtually at zero. This ensures high client retention and healthy profit margins for our advisory and webmaster retainer.

| Service / Tool | Regular Commercial Price | R-a-F Non-Profit / Optimized Price | Annual Cost (USD) | Annual Cost (UGX Approx) |
| :--- | :--- | :--- | :--- | :--- |
| **Domain Name (`.org`)** | $14 / year | $12 / year | $12 | ~UGX 45,000 |
| **Cloudflare DNS & CDN** | $20 / month | **FREE** | $0 | UGX 0 |
| **Vercel Edge Hosting** | $20 / month | **FREE (Hobby Tier)** | $0 | UGX 0 |
| **Google Workspace (3 Users)**| $216 / year | **FREE (via TechSoup)** | $0 | UGX 0 |
| **Cloudflare R2 PDF Storage** | $15 / month | **FREE (Under 10 GB)** | $0 | UGX 0 |
| **Pesapal Payment Gateway** | Transaction Fee only | **2.5% - 3.5% per donation** | $0 upfront | Pay-as-you-raise |
| **Better Stack Uptime Monitor**| $25 / month | **FREE (Starter Tier)** | $0 | UGX 0 |
| **Brevo Donor Email Engine** | $25 / month | **FREE (300 emails/day)** | $0 | UGX 0 |
| **TOTAL FIXED INFRASTRUCTURE**| ~$600 / year | **MINIMAL HARD COST** | **~$12 / year** | **~UGX 45,000 / year** |

---

## 4. Setup Sequence for the Builder & Webmaster

```text
[PHASE 1: REGISTRATION & IDENTIFICATION]
1. Purchase .org domain via Cloudflare Registrar or Namecheap.
2. Register organization on TechSoup Uganda using CBO certificate.
3. Apply for Google Workspace for Nonprofits.

[PHASE 2: CODEBASE & DEPLOYMENT]
4. Initialize Next.js project on GitHub.
5. Link GitHub repo to Vercel and assign custom domain.
6. Configure Cloudflare DNS records (A, CNAME, MX records for Google Workspace).

[PHASE 3: STORAGE & GATEWAY INTEGRATION]
7. Set up Cloudflare R2 bucket for PDF report hosting.
8. Register merchant account on Pesapal Uganda using R-a-F commercial bank credentials.
9. Embed Pesapal API keys into Vercel environment variables.

[PHASE 4: WEBMASTER RETAINER HANDOVER]
10. Connect Better Stack uptime ping to monitor live URL.
11. Test donation gateway with a live UGX 2,000 Mobile Money test.
12. Hand over operational tracking to the Scenario A monthly retainer workflow.
```
