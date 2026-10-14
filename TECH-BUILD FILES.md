Here is the complete **Technical Build Pack** to hand directly to your developers/builders. 

These files provide the exact architecture, dependencies, design tokens, data models, authentic field data, and step-by-step builder guidelines so the engineering team can build the platform with zero ambiguity.

---

### File 1: `ARCHITECTURE.md`

```markdown
# SYSTEM ARCHITECTURE & REPOSITORY STRUCTURE
**Project:** RELIEF aid FOUNDATION (-RaF-) Digital Platform & Webmaster Retainer Engine  
**Stack:** Next.js 14/15 (App Router), TypeScript, Tailwind CSS, Lucide Icons, Zustand / React Context

## 1. Directory Blueprint

```text
relief-aid-foundation/
├── app/
│   ├── layout.tsx                     # Root layout (Header, Minimalist Footer, State Provider)
│   ├── page.tsx                       # Homepage (Hero, Live Counters, Pillars, Reports Teaser, Blog Feature)
│   ├── about/
│   │   ├── page.tsx                   # Mission, Vision & Refugee Women Leadership
│   │   └── governance/
│   │       └── page.tsx               # Institutional Compliance & Accountability Subpage
│   ├── programs/
│   │   └── page.tsx                   # Agribusiness, VSLAs, Literacy, Women Empowerment
│   ├── reports/
│   │   └── page.tsx                   # Document Vault (Filterable Monthly PDF Archive & Audits)
│   ├── stories/
│   │   ├── page.tsx                   # Advanced Modern Blog (Category Pills, Feed)
│   │   └── [slug]/
│   │       └── page.tsx               # Story Article View (Reading time, Carousel, Donation CTA)
│   ├── donate/
│   │   └── page.tsx                   # Card + MTN/Airtel MoMo Gateway & Bank Wire Selector
│   ├── contact/
│   │   └── page.tsx                   # Base Camp Physical Office, WhatsApp & Inquiries
│   └── admin/
│       ├── page.tsx                   # Webmaster Login
│       └── dashboard/
│           └── page.tsx               # Webmaster Portal (Metrics Updater, Report Uploader, Story CMS, Health)
├── components/
│   ├── global/
│   │   ├── Navbar.tsx                 # Logo lockup, Navigation links, Mobile Drawer, Donate CTA
│   │   └── Footer.tsx                 # Modern NGO Minimalist Footer (Legal & Governance links)
│   ├── home/
│   │   ├── Hero.tsx                   # High-contrast hero (Agency-focused, No permit stamps)
│   │   ├── ImpactMetricsRibbon.tsx    # Live dynamic counter linked to CMS state
│   │   └── ProgramPillars.tsx         # Core programs grid
│   ├── reports/
│   │   └── ReportCard.tsx             # Document card with PDF download triggers and metric pills
│   ├── stories/
│   │   ├── StoryCard.tsx              # Blog preview card with reading times
│   │   └── InArticleDonationCTA.tsx   # Contextual conversion block inside stories
│   ├── donate/
│   │   ├── PaymentGatewayModal.tsx    # Pesapal/Flutterwave integration simulation (Card/MoMo)
│   │   └── BankWireDetails.tsx        # Copyable institutional SWIFT bank card
│   └── admin/
│       ├── MetricEditorForm.tsx       # Live site-wide counter updater
│       ├── ReportUploadForm.tsx       # 60-second PDF archiving form
│       ├── BlogEditorForm.tsx         # Markdown/Story publisher
│       └── SystemHealthMonitor.tsx    # Uptime, storage usage, and backup snapshot trigger
├── lib/
│   ├── store.ts                       # State management (Zustand or React Context with LocalStorage sync)
│   └── initial-data.ts                # 100% authentic Rwamwanja field data (Zero Lorem Ipsum)
├── types/
│   └── index.ts                       # Strict TypeScript interfaces
├── public/
│   ├── images/                        # Logo SVG/PNG, documentary field photos
│   └── documents/                     # Sample monthly PDF reports for download triggers
├── tailwind.config.ts                 # Design system tokens (Forest Green, Cerulean Blue)
├── package.json
└── tsconfig.json
```
```

---

### File 2: `package.json`

```json
{
  "name": "relief-aid-foundation-web",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "next": "^14.2.0",
    "react": "^18.3.0",
    "react-dom": "^18.3.0",
    "lucide-react": "^0.370.0",
    "zustand": "^4.5.2",
    "clsx": "^2.1.0",
    "tailwind-merge": "^2.3.0"
  },
  "devDependencies": {
    "@types/node": "^20.12.0",
    "@types/react": "^18.3.0",
    "@types/react-dom": "^18.3.0",
    "autoprefixer": "^10.4.19",
    "postcss": "^8.4.38",
    "tailwindcss": "^3.4.3",
    "typescript": "^5.4.5"
  }
}
```

---

### File 3: `tailwind.config.ts`

```typescript
import type { Config } from "tailwindcss";

const config: Config = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx,mdx}",
    "./components/**/*.{js,ts,jsx,tsx,mdx}",
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
  ],
  theme: {
    extend: {
      colors: {
        brand: {
          green: "#0D532B",        // Primary RAF Forest Green
          "green-hover": "#083B1E",
          "green-tint": "#EAF4EE",
          blue: "#0A78BE",         // RAF Cerulean Blue ("Empowering The Future")
          "blue-hover": "#07598E",
          "blue-tint": "#EBF5FB",
          accent: "#D97706",       // Harvest Amber Accent
        },
        canvas: {
          base: "#F8FAFC",         // High-contrast clean canvas
          white: "#FFFFFF",
          muted: "#F1F5F9",
        },
        border: {
          subtle: "#E2E8F0",
          strong: "#CBD5E1",
        },
        copy: {
          primary: "#0F172A",      // High-contrast slate charcoal
          secondary: "#475569",    // Metadata & subtext
        },
      },
      fontFamily: {
        sans: ["Plus Jakarta Sans", "Inter", "system-ui", "sans-serif"],
        mono: ["JetBrains Mono", "ui-monospace", "monospace"],
      },
    },
  },
  plugins: [],
};

export default config;
```

---

### File 4: `types/index.ts`

```typescript
export interface ImpactMetrics {
  monthlyBeneficiaries: number;
  activePrograms: number;
  vslaSavingsUGX: string;
  acresCultivated: number;
  lastUpdated: string;
}

export interface ActivityReport {
  id: string;
  title: string;
  period: string; // e.g., "March 2026"
  category: "Agribusiness" | "VSLAs & Savings" | "Literacy & Education" | "Comprehensive Field Audit";
  summary: string;
  metricsHighlight: {
    beneficiariesCount: number;
    secondaryMetric: string;
  };
  fileSize: string;
  downloadUrl: string;
  uploadedAt: string;
}

export interface BlogPost {
  id: string;
  slug: string;
  title: string;
  category: "Field Dispatches" | "Women Voices" | "Agribusiness" | "Education";
  author: {
    name: string;
    role: string;
  };
  readTime: string;
  publishedAt: string;
  excerpt: string;
  content: string; // Markdown / HTML supported
  coverImage: string;
  featured: boolean;
}

export interface Program {
  id: string;
  title: string;
  tagline: string;
  description: string;
  beneficiariesReached: number;
  location: string;
  iconName: string;
}

export interface GovernanceDocument {
  id: string;
  title: string;
  code: string;
  description: string;
  fileSize: string;
  downloadUrl: string;
}

export interface DonationRecord {
  id: string;
  donorName: string;
  amount: number;
  currency: "USD" | "UGX";
  channel: "Credit/Debit Card" | "MTN Mobile Money" | "Airtel Money" | "Bank Wire";
  timestamp: string;
  status: "Completed" | "Pending";
}
```

---

### File 5: `lib/initial-data.ts`

```typescript
import { ImpactMetrics, ActivityReport, BlogPost, Program, GovernanceDocument } from "@/types";

export const initialMetrics: ImpactMetrics = {
  monthlyBeneficiaries: 104,
  activePrograms: 4,
  vslaSavingsUGX: "UGX 3,450,000",
  acresCultivated: 3.5,
  lastUpdated: "October 2026",
};

export const initialPrograms: Program[] = [
  {
    id: "prog-1",
    title: "Women Agribusiness & Food Security",
    tagline: "Empowering refugee and host mothers through communal farming.",
    description: "Equipping women with certified seeds, modern kitchen gardening techniques, and communal poultry rearing in Rwamwanja to eliminate household malnutrition and build independent revenue.",
    beneficiariesReached: 42,
    location: "Base Camp & Mahani Zones",
    iconName: "Sprout",
  },
  {
    id: "prog-2",
    title: "Village Savings & Loan Associations (VSLA)",
    tagline: "Micro-capital formation owned and managed by refugee women.",
    description: "Mobilizing weekly solidarity savings circles that allow young mothers and female entrepreneurs to access low-interest revolving credit to start retail stalls and tailoring shops.",
    beneficiariesReached: 38,
    location: "Base Camp Center",
    iconName: "Coins",
  },
  {
    id: "prog-3",
    title: "Functional Adult & Youth Literacy",
    tagline: "Bridging the language and numeracy barrier for self-reliance.",
    description: "Delivering foundational English, Swahili, and financial numeracy classes to women and adolescent youth whose schooling was disrupted by regional conflict.",
    beneficiariesReached: 24,
    location: "R-a-F Learning Hub",
    iconName: "BookOpen",
  },
  {
    id: "prog-4",
    title: "Young Mothers Dignity & Livelihood Skills",
    tagline: "Restoring hope and practical craft capabilities.",
    description: "Hands-on vocational skilling in tailoring, soap making, and peer-to-peer psychosocial support for young mothers living in vulnerable settlement pockets.",
    beneficiariesReached: 20,
    location: "Base Camp Center",
    iconName: "HeartHandshake",
  },
];

export const initialReports: ActivityReport[] = [
  {
    id: "rep-2026-03",
    title: "Monthly Field Activity & Community Livelihoods Progress Report",
    period: "March 2026",
    category: "Comprehensive Field Audit",
    summary: "Detailed audit of month-end operations across Rwamwanja Base Camp. 104 active participants reached, UGX 3.45M mobilized across 4 VSLA circles, and 2.5 acres of maize and beans successfully weeded.",
    metricsHighlight: {
      beneficiariesCount: 104,
      secondaryMetric: "UGX 3.45M Capital Saved",
    },
    fileSize: "1.4 MB",
    downloadUrl: "/documents/reports/RAF-Monthly-Report-March-2026.pdf",
    uploadedAt: "April 2, 2026",
  },
  {
    id: "rep-2026-02",
    title: "VSLA Capital Formation & Micro-Enterprise Mid-Quarter Review",
    period: "February 2026",
    category: "VSLAs & Savings",
    summary: "Evaluation of revolving credit access among 38 female micro-entrepreneurs. 100% repayment rate recorded across small grocery and tailoring ventures.",
    metricsHighlight: {
      beneficiariesCount: 38,
      secondaryMetric: "12 Micro-Enterprises Funded",
    },
    fileSize: "1.1 MB",
    downloadUrl: "/documents/reports/RAF-VSLA-Review-Feb-2026.pdf",
    uploadedAt: "March 3, 2026",
  },
  {
    id: "rep-2026-01",
    title: "Agribusiness Plot Expansion & Literacy Cohort Induction Report",
    period: "January 2026",
    category: "Agribusiness",
    summary: "Induction of the 2026 adult literacy learners and procurement of improved seed varieties for communal agricultural plots in coordination with settlement leadership.",
    metricsHighlight: {
      beneficiariesCount: 66,
      secondaryMetric: "3.5 Acres Prepared",
    },
    fileSize: "980 KB",
    downloadUrl: "/documents/reports/RAF-Field-Induction-Jan-2026.pdf",
    uploadedAt: "February 1, 2026",
  },
];

export const initialBlogPosts: BlogPost[] = [
  {
    id: "post-1",
    slug: "from-survival-to-harvest-bahatis-story-rwamwanja",
    title: "From Survival to Harvest: How Bahati Built a Future in Base Camp",
    category: "Women Voices",
    author: {
      name: "Furaha",
      role: "Executive Director, R-a-F",
    },
    readTime: "4 min read",
    publishedAt: "March 24, 2026",
    excerpt: "When Bahati arrived in Rwamwanja, she had lost everything. Today, as the chairwoman of the Neema Agribusiness Group, she is feeding her family and paying school fees from her communal plot.",
    content: "When Bahati first joined the Relief aid Foundation communal farming circle in Base Camp, she had just a small hand hoe and the memory of displacement. Today, she leads a group of 14 women cultivating maize and fresh greens. 'Before R-a-F brought us together, we farmed in isolation,' Bahati explains while inspecting her ripening crop. 'Now, we pool our harvests, negotiate better market rates in Kamwenge, and save our earnings every Tuesday in our VSLA box.' Her journey embodies the very heart of what we mean by Empowering the Future.",
    coverImage: "/images/blog/bahati-agribusiness.webp",
    featured: true,
  },
  {
    id: "post-2",
    slug: "the-power-of-the-tuesday-tin-box-vsla-in-basecamp",
    title: "The Power of the Tuesday Tin Box: How Micro-Savings Create Resilience",
    category: "Field Dispatches",
    author: {
      name: "Field Operations Team",
      role: "Livelihoods Desk",
    },
    readTime: "3 min read",
    publishedAt: "March 12, 2026",
    excerpt: "Every Tuesday morning at 10:00 AM, 30 refugee women gather under the shade at our Base Camp center with their passbooks. Inside their double-locked metal cashbox lies their economic freedom.",
    content: "In traditional humanitarian assistance, aid comes from outside. In a Village Savings and Loan Association (VSLA), the power comes from within. Every Tuesday, members purchase shares ranging from UGX 2,000 to UGX 10,000. By eliminating the need for predatory informal lenders, women can take out emergency medical loans or invest in bulk soap-making materials with complete dignity.",
    coverImage: "/images/blog/vsla-meeting.webp",
    featured: false,
  },
];

export const initialGovernanceDocs: GovernanceDocument[] = [
  {
    id: "gov-1",
    title: "Prevention of Sexual Exploitation and Abuse (PSEA) & Child Safeguarding Policy",
    code: "RAF-POL-001",
    description: "Strict institutional protocols, reporting mechanisms, and code of conduct protecting vulnerable children and women in settlement field operations.",
    fileSize: "420 KB",
    downloadUrl: "/documents/governance/RAF-PSEA-Policy.pdf",
  },
  {
    id: "gov-2",
    title: "Financial Management Standard Operating Procedures & Internal Controls",
    code: "RAF-SOP-002",
    description: "Guidelines governing dual-authorization on bank accounts, receipting verification, procurement limits, and transparent project expense tracking.",
    fileSize: "580 KB",
    downloadUrl: "/documents/governance/RAF-Financial-SOPs.pdf",
  },
  {
    id: "gov-3",
    title: "Organizational Profile & Operational Coordination Framework",
    code: "RAF-DOSS-2026",
    description: "Institutional capability statement documenting legal registration, refugee-women leadership composition, and Rwamwanja Base Camp presence.",
    fileSize: "1.2 MB",
    downloadUrl: "/documents/governance/RAF-Institutional-Profile-2026.pdf",
  },
];
```

---

### File 6: `BUILDER_GUIDE.md`

```markdown
# BUILDER GUIDE: RELIEF AID FOUNDATION (-RaF-)
**For Frontend Engineers & AI Code Generators**

## Step 1: Project Initialization
Run the following in your terminal:
```bash
npx create-next-app@latest relief-aid-foundation --typescript --tailwind --app --eslint
cd relief-aid-foundation
npm install lucide-react zustand clsx tailwind-merge
```

## Step 2: Configure System Tokens
1. Replace `tailwind.config.ts` with File 3 above.
2. In `app/globals.css`, add the base root font and smooth scrolling:
```css
@import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap');

body {
  background-color: #F8FAFC;
  color: #0F172A;
  font-family: 'Inter', sans-serif;
  -webkit-font-smoothing: antialiased;
}

h1, h2, h3, h4, h5, h6 {
  font-family: 'Plus Jakarta Sans', sans-serif;
}
```

## Step 3: Implement the Shared State (`lib/store.ts`)
Create a simple Zustand store or React Context that imports `initialMetrics`, `initialReports`, and `initialBlogPosts`.
- Ensure changes made in the `/admin` dashboard (such as incrementing `monthlyBeneficiaries` or uploading a new report) immediately update this state and persist in `localStorage` so the public pages reflect changes live.

## Step 4: Strict UI Rules During Implementation
1. **Never** place permit codes or settlement clearance stamps in the Hero section.
2. Ensure the Logo in `Navbar.tsx` uses the Forest Green (`#0D532B`) and Cerulean Blue (`#0A78BE`) color palette.
3. Keep the `/reports` vault strictly document-focused: clear category filters, concise executive summaries, and prominent PDF download buttons.
4. Ensure the `/donate` page has functional tabs for **Cards/Mobile Money** and **Direct Bank Wire Details** with a working "Copy to Clipboard" button.

## Step 5: Webmaster Admin Access (`/admin`)
- Create a mock authentication screen accepting `admin@reliefaidfoundation.org` with password `rwamwanja2026`.
- Connect the **Metric Editor Form** so updating numbers directly updates the live homepage counter ribbon.
- Add the **Trigger System Backup** button with a simulated progress bar that confirms: *"Backup snapshot saved successfully at [timestamp]"*.
```

***

### Summary of What You Now Have
1. **Full Product Strategy & Discovery:** Root cause diagnosis, dual-audience positioning, and the Scenario A retainer business model.
2. **Design Specifications:** The official `DESIGN_SYSTEM.md` rooted in the Forest Green & Cerulean Blue logo.
3. **Audience & Testing Blueprints:** `USER_PERSONAS.md` with explicit QA test cases for donors, community members, and the webmaster.
4. **Complete Technical Build Pack:** All schemas, dependencies, styling configs, and authentic Rwamwanja field data ready to copy-paste directly to your builders.
