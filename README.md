# Digital Marketing Quote Intake – README

This README documents the **Project Quote Intake** form used to scope digital‑marketing projects. It’s a **frontend‑only**, multi‑step wizard that stores data in the browser and lets you export JSON/CSV for manual processing.

---

## 1) Overview

**Purpose:** Capture all details needed to estimate and propose digital‑marketing services (SEO, PPC, Social, Content, Email/CRM, Web, Analytics, Branding, Video, Training) plus context (goals, audience, budget, timeline, compliance).

**Tech:**

- Single HTML file with TailwindCSS (CDN). No backend.
- Client‑side state only; optional `localStorage` draft save (key: `dm_intake_draft_v1`).
- Export as **JSON** or **CSV**, or **Print**.

**Navigation:** 7 steps with a progress bar; sections expand conditionally when a channel is selected.

---

## 2) How to Use

1. **Fill Step 1** (required: Contact name, email, company).
2. Use **Next/Back**; toggle channels to reveal their sub‑questions.
3. **Save draft** to the browser at any time; **Load** to restore later; **Clear** to reset.
4. On Step 7, **Preview** → **Copy JSON**, **Download JSON**, **Download CSV**, or **Print**.

> **Files upload note:** the *Uploads* field in Step 6 is local-only and not included in exports.

---

## 3) Field Reference (Inputs)

**Names** below match HTML `name` attributes and keys in exported JSON/CSV unless noted.

### Step 1 – Contact & Company

| Label                  | Name            | Type   | Required | Options/Format            | Notes                  |
| ---------------------- | --------------- | ------ | -------- | ------------------------- | ---------------------- |
| Contact name           | `contact_name`  | text   | Yes      | –                         | Primary contact person |
| Contact email          | `contact_email` | email  | Yes      | valid email               |                        |
| Phone / WhatsApp       | `contact_phone` | tel    | No       | international ok          |                        |
| Company / Organization | `company_name`  | text   | Yes      | –                         |                        |
| Website                | `website`       | url    | No       | https\://…                |                        |
| Industry               | `industry`      | text   | No       | –                         |                        |
| Country                | `country`       | text   | No       | –                         |                        |
| Preferred language     | `language`      | select | No       | English, French, Malagasy |                        |

### Step 2 – Current Status

| Label                       | Name               | Type     | Required | Options/Format                        | Notes |
| --------------------------- | ------------------ | -------- | -------- | ------------------------------------- | ----- |
| Website / Shop              | `assets_website`   | checkbox | No       | boolean                               |       |
| Brandbook / Logo            | `assets_brandbook` | checkbox | No       | boolean                               |       |
| GTM / Analytics             | `assets_gtm`       | checkbox | No       | boolean                               |       |
| Meta/TikTok/LinkedIn pixels | `assets_pixels`    | checkbox | No       | boolean                               |       |
| CRM / Email (Brevo, etc.)   | `assets_crm`       | checkbox | No       | boolean                               |       |
| Photo/Video library         | `assets_content`   | checkbox | No       | boolean                               |       |
| Current CMS / Stack         | `cms`              | select   | No       | WordPress, Shopify, Custom, Wix, None |       |
| Email list size (approx.)   | `list_size`        | number   | No       | ≥ 0                                   |       |
| Share asset folder          | `drive_link`       | url      | No       | https\://…                            |       |

### Step 3 – Goals & Audience

| Label                          | Name               | Type          | Required | Options/Format                                                                 | Notes                             |
| ------------------------------ | ------------------ | ------------- | -------- | ------------------------------------------------------------------------------ | --------------------------------- |
| Primary goal                   | `primary_goal`     | select        | Yes      | Lead generation, Online sales, Brand awareness, App installs, Community growth |                                   |
| Key KPIs                       | `kpis`             | text          | No       | e.g., CPL, ROAS, CTR                                                           |                                   |
| Audience type                  | `audience_type`    | select        | No       | B2C, B2B, Both                                                                 |                                   |
| Target locations               | `target_locations` | chips → array | No       | string array                                                                   | Add with Enter; exported as array |
| Describe ideal customer        | `personas`         | textarea      | No       | –                                                                              |                                   |
| Competitors                    | `competitors`      | chips → array | No       | string array                                                                   |                                   |
| Reference links / inspirations | `references`       | chips → array | No       | string array                                                                   | URLs or notes                     |

### Step 4 – Channels & Deliverables

Selecting a channel adds it to `channels` (array) **and reveals extra inputs.**

**Channel toggles**

| Channel                 | Toggle Name    | Value in `channels` |
| ----------------------- | -------------- | ------------------- |
| SEO                     | `ch_seo`       | `"seo"`             |
| Paid Ads (PPC)          | `ch_ppc`       | `"ppc"`             |
| Social Media Management | `ch_social`    | `"social"`          |
| Content                 | `ch_content`   | `"content"`         |
| Email / CRM             | `ch_email`     | `"email"`           |
| Website / E‑commerce    | `ch_web`       | `"web"`             |
| Analytics & Tracking    | `ch_analytics` | `"analytics"`       |
| Branding & Design       | `ch_brand`     | `"brand"`           |
| Video / Reels           | `ch_video`     | `"video"`           |
| Team Training           | `ch_training`  | `"training"`        |

**SEO fields** (shown if `ch_seo` is checked)

| Label                  | Name               | Type     | Notes   |
| ---------------------- | ------------------ | -------- | ------- |
| # of pages to optimize | `seo_pages`        | number   | ≥ 0     |
| Blog posts / month     | `seo_blogs`        | number   | ≥ 0     |
| Need a full SEO audit  | `seo_audit`        | checkbox | boolean |
| Include link building  | `seo_linkbuilding` | checkbox | boolean |

**Paid Ads (PPC) fields** (shown if `ch_ppc` is checked)

| Label                      | Name            | Type                   | Notes                                  |
| -------------------------- | --------------- | ---------------------- | -------------------------------------- |
| Platforms                  | `ppc_platforms` | checkbox group → array | Values: Google, Meta, TikTok, LinkedIn |
| Monthly ad spend (est.)    | `ppc_spend`     | number                 | currency independent                   |
| Target geographies         | `ppc_geo`       | text                   | e.g., MG, FR                           |
| Conversion tracking set up | `ppc_tracking`  | checkbox               | boolean                                |

**Social Media Management fields** (shown if `ch_social` is checked)

| Label                     | Name           | Type                   | Notes                                                  |
| ------------------------- | -------------- | ---------------------- | ------------------------------------------------------ |
| Platforms                 | `sm_platforms` | checkbox group → array | Values: Facebook, Instagram, TikTok, LinkedIn, YouTube |
| Posts per week            | `sm_posts`     | number                 | ≥ 0                                                    |
| Community mgmt hours / wk | `sm_community` | number                 | ≥ 0                                                    |

**Content fields** (shown if `ch_content` is checked)

| Label                 | Name                | Type   | Notes            |
| --------------------- | ------------------- | ------ | ---------------- |
| Blog posts / month    | `content_blogs`     | number | ≥ 0              |
| Landing pages         | `content_landings`  | number | ≥ 0              |
| Copywriting languages | `content_languages` | text   | e.g., EN, FR, MG |

**Email / CRM fields** (shown if `ch_email` is checked)

| Label                   | Name                 | Type     | Notes       |
| ----------------------- | -------------------- | -------- | ----------- |
| Platform                | `email_platform`     | text     | e.g., Brevo |
| Newsletters / month     | `email_frequency`    | number   | ≥ 0         |
| Automations / workflows | `email_automation`   | checkbox | boolean     |
| Segmentation            | `email_segmentation` | checkbox | boolean     |

**Website / E‑commerce fields** (shown if `ch_web` is checked)

| Label                 | Name               | Type     | Notes                      |
| --------------------- | ------------------ | -------- | -------------------------- |
| Type                  | `web_type`         | select   | WordPress, Shopify, Custom |
| # of pages / products | `web_pages`        | number   | ≥ 0                        |
| Integrations needed   | `web_integrations` | text     | e.g., Payments, CRM, ERP   |
| Need hosting          | `web_hosting`      | checkbox | boolean                    |

**Analytics & Tracking fields** (shown if `ch_analytics` is checked)

| Label                | Name           | Type     | Notes                      |
| -------------------- | -------------- | -------- | -------------------------- |
| GA4                  | `an_ga4`       | checkbox | boolean                    |
| GTM                  | `an_gtm`       | checkbox | boolean                    |
| Meta / TikTok pixels | `an_pixels`    | checkbox | boolean                    |
| Consent management   | `an_consent`   | checkbox | boolean                    |
| Reporting frequency  | `an_reporting` | select   | Weekly, Bi‑weekly, Monthly |

**Branding & Design fields** (shown if `ch_brand` is checked)

| Label                 | Name               | Type     | Notes   |
| --------------------- | ------------------ | -------- | ------- |
| Logo / Identity       | `brand_logo`       | checkbox | boolean |
| Brand guidelines      | `brand_guidelines` | checkbox | boolean |
| Ad / Social templates | `brand_mockups`    | checkbox | boolean |

**Video / Reels fields** (shown if `ch_video` is checked)

| Label                    | Name              | Type     | Notes   |
| ------------------------ | ----------------- | -------- | ------- |
| # of videos / month      | `video_count`     | number   | ≥ 0     |
| Typical length (sec)     | `video_length`    | number   | ≥ 0     |
| On‑site filming required | `video_filming`   | checkbox | boolean |
| Subtitles                | `video_subtitles` | checkbox | boolean |

**Team Training fields** (shown if `ch_training` is checked)

| Label      | Name           | Type   | Notes                     |
| ---------- | -------------- | ------ | ------------------------- |
| Topics     | `train_topics` | text   | e.g., Ads, SEO, Analytics |
| # of seats | `train_seats`  | number | ≥ 0                       |

### Step 5 – Timeline & Budget

| Label                       | Name             | Type     | Required | Notes                            |
| --------------------------- | ---------------- | -------- | -------- | -------------------------------- |
| Desired start               | `start_date`     | date     | No       |                                  |
| Deadline / launch           | `deadline`       | date     | No       |                                  |
| Urgency                     | `urgency`        | select   | No       | Values: Flexible, Normal, Urgent |
| Currency                    | `currency`       | select   | No       | Values: MGA, EUR, USD            |
| Monthly budget (est.)       | `budget_monthly` | number   | No       | ≥ 0                              |
| One‑time budget (setup/dev) | `budget_onetime` | number   | No       | ≥ 0                              |
| Constraints / approvals     | `constraints`    | textarea | No       |                                  |
| Notes                       | `notes`          | textarea | No       |                                  |

### Step 6 – Compliance & Access

| Label                      | Name        | Type            | Notes                        |
| -------------------------- | ----------- | --------------- | ---------------------------- |
| GDPR                       | `gdpr`      | checkbox        | boolean                      |
| Health/medical sensitive   | `hipaa`     | checkbox        | boolean                      |
| Finance/regulated          | `finance`   | checkbox        | boolean                      |
| GA4 access                 | `acc_ga4`   | checkbox        | boolean                      |
| GTM access                 | `acc_gtm`   | checkbox        | boolean                      |
| Meta Business access       | `acc_meta`  | checkbox        | boolean                      |
| Google Ads access          | `acc_ads`   | checkbox        | boolean                      |
| Brevo access               | `acc_brevo` | checkbox        | boolean                      |
| WordPress / Shopify access | `acc_wp`    | checkbox        | boolean                      |
| Upload briefs / RFP        | `uploads`   | file (multiple) | **Local only; not exported** |

### Step 7 – Review & Export

Action buttons only (no new fields). Preview table reflects current state.

---

## 4) Outputs (JSON, CSV)

### JSON Structure

- Generated from all fields except files.
- Arrays for: `channels`, `ppc_platforms`, `sm_platforms`, `target_locations`, `competitors`, `references`.
- Adds computed metrics: `complexity_score` (number as string) and `complexity_level` (Low/Medium/High).

**Example JSON**

```json
{
  "contact_name": "Jane Doe",
  "contact_email": "jane@acme.com",
  "contact_phone": "+261 34 12 345 67",
  "company_name": "Acme Ltd",
  "website": "https://acme.example",
  "industry": "Retail",
  "country": "Madagascar",
  "language": "French",
  "assets_website": "on",
  "assets_brandbook": "on",
  "cms": "WordPress",
  "list_size": "2500",
  "drive_link": "https://drive.google.com/folder/...",
  "primary_goal": "Lead generation",
  "kpis": "CPL < $5, CTR > 2%",
  "audience_type": "B2C",
  "target_locations": ["Antananarivo", "Paris"],
  "personas": "Young professionals...",
  "competitors": ["BrandX", "BrandY"],
  "references": ["https://inspo1.com", "https://inspo2.com"],
  "channels": ["ppc", "social", "analytics"],
  "ppc_platforms": ["Google", "Meta"],
  "ppc_spend": "10000000",
  "ppc_geo": "MG, FR",
  "ppc_tracking": "on",
  "sm_platforms": ["Facebook", "Instagram"],
  "sm_posts": "5",
  "sm_community": "3",
  "an_ga4": "on",
  "an_gtm": "on",
  "an_reporting": "Monthly",
  "start_date": "2025-09-01",
  "deadline": "2025-11-15",
  "urgency": "Normal",
  "currency": "MGA",
  "budget_monthly": "2000000",
  "budget_onetime": "5000000",
  "constraints": "Procurement approval required",
  "notes": "Bundle with training if possible",
  "complexity_score": "37",
  "complexity_level": "Medium"
}
```

> **Booleans:** HTML checkboxes export as presence of the key with value `"on"` if checked (or absent if unchecked). Normalize to true/false in your processing if preferred.

### CSV Structure

- **Header row** lists all keys present at export time.
- **Arrays** (e.g., `ppc_platforms`) are joined by semicolon and space: `"Google; Meta"`.
- **Booleans** appear as `on` for checked, empty otherwise.

---

## 5) Conditional Logic

- Checking a channel (`ch_*`) reveals its fields and adds the channel id to `channels` (e.g., `"ppc"`).
- Hidden sections do **not** prevent export; if left empty their keys are absent or empty.

---

## 6) Complexity Score (Heuristic)

Displayed in Step 5; also exported as `complexity_score` and `complexity_level`.

**Computation:**

- +10 points per selected channel.
- For each numeric workload field, add `min(value, 50) / 5` (caps contribution at +10 per field). Fields considered: `seo_pages`, `seo_blogs`, `sm_posts`, `sm_community`, `content_blogs`, `content_landings`, `video_count`, `video_length`, `web_pages`.
- Urgency: `Urgent` +10, `Normal` +5, `Flexible` +0.

**Bands:** `< 20 = Low`, `20–44 = Medium`, `≥ 45 = High`.

> This is a lightweight indicator to help right‑size proposals; adjust to match your pricing model.

---

## 7) Data Handling & Privacy

- **Storage:** nothing leaves the browser; drafts saved to `localStorage` (`dm_intake_draft_v1`).
- **Uploads:** shown for convenience but *not* transmitted or included in exports.
- **Exports:** JSON and CSV are generated client‑side and downloaded to the user.

---

## 8) Validation & UX

- Required: `contact_name`, `contact_email`, `company_name` (Step 1).
- Basic HTML5 types (email, url, number, date) and browser validation.
- Chips inputs store arrays as JSON strings internally; the exporter converts them to real arrays in JSON.

---

## 9) Customization Guide

**Branding:**

- Update Tailwind palette in the inline `tailwind.config` (color `brand.*`).
- Modify classes on buttons/cards for different aesthetics.

**Labels/Locales:**

- Replace visible text in HTML to French/Malagasy or make bilingual.
- For options (e.g., languages, CMS types), edit corresponding `<select>` or checkbox labels.

**Fields:**

- Add more channels by duplicating a fieldset and adding a new `.channel` checkbox. Ensure its `name` starts with `ch_` so it appears in `channels`.
- Include additional numeric fields in the complexity calculation by adding their `id` into `updateComplexity()`.

**Integration (optional):**

- To submit to a backend, replace the export buttons with a call like:

```js
fetch('/api/intake', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(collectData())
});
```

---

## 10) Deployment

- Serve the single HTML file on any static host (e.g., GitHub Pages, Netlify, Vercel, or as a WordPress page template).
- Ensure internet access for Tailwind CDN and Google Fonts, or self‑host them for offline environments.

---

## 11) Field Key Map (Quick Reference)

**Core:** `contact_name`, `contact_email`, `contact_phone`, `company_name`, `website`, `industry`, `country`, `language`\
**Status:** `assets_website`, `assets_brandbook`, `assets_gtm`, `assets_pixels`, `assets_crm`, `assets_content`, `cms`, `list_size`, `drive_link`\
**Goals:** `primary_goal`, `kpis`, `audience_type`, `target_locations[]`, `personas`, `competitors[]`, `references[]`\
**Channels (toggle → adds to **``**):** `ch_seo`, `ch_ppc`, `ch_social`, `ch_content`, `ch_email`, `ch_web`, `ch_analytics`, `ch_brand`, `ch_video`, `ch_training`\
**SEO:** `seo_pages`, `seo_blogs`, `seo_audit`, `seo_linkbuilding`\
**PPC:** `ppc_platforms[]`, `ppc_spend`, `ppc_geo`, `ppc_tracking`\
**Social:** `sm_platforms[]`, `sm_posts`, `sm_community`\
**Content:** `content_blogs`, `content_landings`, `content_languages`\
**Email/CRM:** `email_platform`, `email_frequency`, `email_automation`, `email_segmentation`\
**Web:** `web_type`, `web_pages`, `web_integrations`, `web_hosting`\
**Analytics:** `an_ga4`, `an_gtm`, `an_pixels`, `an_consent`, `an_reporting`\
**Brand:** `brand_logo`, `brand_guidelines`, `brand_mockups`\
**Video:** `video_count`, `video_length`, `video_filming`, `video_subtitles`\
**Training:** `train_topics`, `train_seats`\
**Budget/Timeline:** `start_date`, `deadline`, `urgency`, `currency`, `budget_monthly`, `budget_onetime`, `constraints`, `notes`\
**Computed:** `channels[]`, `complexity_score`, `complexity_level`

---

## 12) FAQs

**Q: Where do files go?**\
A: Nowhere—uploads are local only and not exported.

**Q: Why do some booleans show as **``**?**\
A: That’s the standard HTML checkbox value. Convert to true/false during processing if needed.

**Q: Can I add my own price calculator?**\
A: Yes—extend `updateComplexity()` or create a separate `estimate()` using the collected fields.

---

*End of README.*

