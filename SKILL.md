---
name: ingest-narrative-spin-up-branded-microsite-cursor-optimized
description: Transforms a raw customer Salesforce narrative into a branded, Heroku-ready HTML/Tailwind microsite with deployment scaffolding. Optimized for Cursor. Use when the user asks to ingest a narrative markdown file, apply customer and Salesforce brand signals, generate a microsite, or prepare immediate Heroku deployment artifacts.
disable-model-invocation: true
---

# Ingest Narrative & Spin Up Branded Microsite (Cursor-Optimized)

## Description
Activates the specialized pipeline to transform a raw customer Salesforce narrative into a beautifully branded, Heroku-ready HTML/Tailwind microsite.

## Prerequisite Check
Before running, ensure the workspace contains:
1. A target narrative file (e.g., `input/customer-narrative.md`)
2. A configuration file (`input/config.json`) containing:
   - `customer_url`: "https://..."
   - `salesforce_brand_url`: "https://www.salesforce.com/company/brand/"

---

## Action Execution Steps

### Step 1: Scrape & Extract Design Tokens
1. Open the browser tool and navigate to `customer_url`. Extract:
   - Dominant brand colors (Primary, Secondary, Background).
   - Typography style (Sans-serif, Serif, Rounded, etc.).
   - UI Vibe (Enterprise, Modern SaaS, Tech-Forward).
2. Navigate to `salesforce_brand_url`. Extract standard Salesforce ecosystem guidelines (e.g., Salesforce Blue, Cloud asset styling).
3. Check `./branding/` directory for any override assets.

### Step 2: Architecture & Layout Mapping
Read the narrative `.md` file. Map the content structurally to:
- **Hero:** Narrative hook customized to the client.
- **Current State:** The Salesforce footprint metrics translated into Tailwind-based visual components (progress bars, metric cards, stat grids).
- **Future State / Story:** The core text flowing logically down the page.

### Step 3: Code Generation & Deployment Prep
1. Generate an `index.html` file using Tailwind CSS via CDN (or Vite setup if configured in config.json).
2. Generate an `app.js` or `style.css` if custom interactivity/styling is needed.
3. Automatically generate a Node.js `server.js` (Express) and a `Procfile` tailored for immediate Heroku deployment.

### Step 4: Verification
Confirm color contrast compliance (WCAG AA) and check that all structural sections from the `.md` narrative are fully accounted for in the generated HTML.
