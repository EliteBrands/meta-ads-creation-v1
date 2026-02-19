# Meta Ads Creator v1

A zero-backend web app for generating vertical 9:16 Meta ad creatives from any landing page. Powered by Gemini AI.

## What it does

1. **Analyzes** your landing page — brand, product, audience, ad angles (9-section analysis)
2. **Extracts** the product image automatically
3. **Generates** vertical 9:16 ad images using Gemini (one per template)
4. **Downloads** ads individually or as a ZIP

## Quick Setup (5 minutes)

### 1. Enable GitHub Pages

1. Go to this repo on GitHub → **Settings** → **Pages**
2. Under **Source**, select: Branch `main`, folder `/ (root)`
3. Click **Save**
4. Your app is live at: `https://elitebrands.github.io/meta-ads-creation-v1/`

### 2. Embed in Notion

1. Open your Notion page
2. Type `/embed`
3. Paste your GitHub Pages URL
4. Resize the embed block to full page width

### 3. First Use

1. Open the embed in Notion
2. Get a free Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey)
3. Enter your key — it saves in your browser (per device)
4. You're ready to generate ads!

---

## Adding Ad Templates

Templates are reference images that tell Gemini the visual style/layout you want.

### Option A: Update the TEMPLATE_FILES constant

1. Add your images to the `templates/` folder (JPG, PNG, or WebP)
2. Open `index.html` and find the `TEMPLATE_FILES` array near the top of the `<script>` section:
   ```javascript
   const TEMPLATE_FILES = [
       // 'template-01.jpg',
       // 'template-02.jpg',
   ];
   ```
3. Uncomment and add your filenames
4. Commit and push — live in seconds

### Option B: Use a manifest file (easier to update without editing HTML)

1. Add images to `templates/`
2. Create `templates/manifest.json`:
   ```json
   ["template-01.jpg", "template-02.jpg", "template-03.jpg"]
   ```
3. Commit and push

---

## Customizing the Analysis Prompt

The brand analysis prompt is in `index.html` in the `buildAnalysisPrompt()` function. Edit it to match your preferred analysis framework.

## Customizing the Ad Generation Prompt

The ad image prompt is in `buildAdPrompt()` in `index.html`. Edit this to guide Gemini toward the exact style and format you want.

---

## Technical Notes

- **Zero backend** — everything runs in the browser
- **API key security** — your Gemini key stays in your browser's localStorage only
- **CORS proxy** — uses `allorigins.win` to fetch landing pages
- **Image model** — `gemini-3-pro-image-preview` (Nano Banana Pro)
- **Analysis model** — `gemini-2.0-flash`
- **ZIP download** — uses JSZip (CDN) for client-side ZIP creation

---

## File Structure

```
meta-ads-creation-v1/
├── index.html          # The entire app
├── templates/          # Your ad template reference images
│   └── manifest.json   # (optional) list of template filenames
└── README.md
```
