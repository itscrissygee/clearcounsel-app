# ⚖ ClearCounsel

**AI compliance infrastructure for legal professionals.**

> *ClearCounsel isn’t an AI tool — it’s the compliance layer that makes AI use defensible.*

Live at **[clearcounsel.app](https://clearcounsel.app)**

-----

## What It Does

ClearCounsel is a two-tool compliance suite built for paralegals, attorneys, and legal ops professionals navigating AI use in legal practice.

### 🛡 Tool 1 — Redact Before You Paste

Detects and removes sensitive client information from any document before it enters an AI tool. Protects attorney-client privilege and satisfies **ABA Model Rule 1.6 (Confidentiality)**.

Detects:

- Social Security Numbers
- Email addresses
- Phone numbers
- Specific dates
- Street addresses
- Court case numbers
- Financial account data

### 📋 Tool 2 — Disclose After You File

Generates court-appropriate AI disclosure language for any filing in seconds. Select your court, jurisdiction, filing type, and AI tools used — and get disclosure language ready to paste directly into your brief or motion. Satisfies **ABA Model Rule 3.3 (Candor to Tribunal)**.

-----

## ABA Compliance Alignment

|Rule / Opinion     |Coverage                                             |
|-------------------|-----------------------------------------------------|
|Model Rule 1.1     |Technological competence — supervising AI output     |
|Model Rule 1.6     |Client confidentiality before AI input               |
|Model Rule 3.3     |Candor to tribunal — AI disclosure in filings        |
|Formal Opinion 477R|Cybersecurity & third-party vendor obligations       |
|2024 AI Guidance   |Attorney responsibility for AI-generated work product|

-----

## Tech Stack

|Layer                    |Technology                                       |
|-------------------------|-------------------------------------------------|
|Landing page             |Vanilla HTML/CSS/JS — zero dependencies          |
|Application              |React (JSX), Tailwind CSS                        |
|AI (Disclosure Generator)|Anthropic Claude API (`claude-sonnet-4-20250514`)|
|Hosting                  |GitHub Pages                                     |
|Waitlist                 |Formspree (free tier)                            |
|Domain                   |`clearcounsel.app`                               |

-----

## Repository Structure

```
clearcounsel-app/
├── index.html          # Landing page (GitHub Pages root)
├── ClearCounsel.jsx    # React application (tool UI)
└── README.md
```

-----

## Setup & Deployment

### 1. Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
1. Source: **Deploy from a branch**
1. Branch: `main` / root (`/`)
1. Save — your site will be live at `itscrissygee.github.io/clearcounsel-app`

### 2. Connect Your Custom Domain

1. In GitHub Pages settings, enter `clearcounsel.app` under **Custom Domain**
1. In your domain registrar (GoDaddy/Namecheap/Porkbun), add these DNS records:

```
Type    Host    Value
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
CNAME   www     itscrissygee.github.io
```

1. Wait 10–30 minutes for DNS propagation
1. Check **Enforce HTTPS** once the domain verifies (`.app` domains require it)

### 3. Configure the Waitlist Form

1. Create a free account at [formspree.io](https://formspree.io)
1. Create a new form — copy your endpoint ID
1. In `index.html`, find this line:

```html
action="https://formspree.io/f/YOUR_FORMSPREE_ID"
```

1. Replace `YOUR_FORMSPREE_ID` with your actual form ID

### 4. Configure the Anthropic API (for the disclosure generator)

The disclosure generator calls the Anthropic Claude API. To use it in production:

1. Get an API key at [console.anthropic.com](https://console.anthropic.com)
1. **Never expose your API key in client-side code for production** — set up a lightweight serverless function (Vercel, Netlify Functions, or Cloudflare Workers) to proxy the API call
1. For local development / portfolio demo purposes only, the React artifact handles this via Claude’s built-in API access

-----

## Local Development

The landing page (`index.html`) runs with zero build step — just open it in a browser or use Live Server in VS Code.

For the React tool (`ClearCounsel.jsx`), you’ll need a React environment:

```bash
npx create-react-app clearcounsel-tool
cd clearcounsel-tool
# Replace src/App.js content with ClearCounsel.jsx
npm start
```

-----

## Roadmap

- [x] PII detection & redaction (v1)
- [x] AI disclosure generator (v1)
- [x] Landing page with waitlist
- [ ] PDF export with firm header (paid feature)
- [ ] Disclosure history & audit log
- [ ] Team/firm seat licensing
- [ ] Jurisdiction-specific standing order database
- [ ] Bar association partnership integrations

-----

## Legal Disclaimer

ClearCounsel is a productivity and compliance aid. It does not constitute legal advice. The PII detection tool uses pattern-matching heuristics and may not detect every instance of sensitive information — always conduct a manual review before sharing documents with any third-party AI system. Generated disclosure language should be reviewed by the supervising attorney before inclusion in any court filing.

-----

## Contact

**Email:** hello@clearcounsel.app  
**Built by:** A paralegal, for the legal profession.  
**Portfolio:** [itscrissygee.github.io](https://itscrissygee.github.io)

-----

*© 2026 ClearCounsel · clearcounsel.app*