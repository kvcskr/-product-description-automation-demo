# n8n — Automated Product Description Generator

An n8n workflow that generates ready-to-publish product descriptions from product photos using GPT-4o Vision. Results are saved directly to Google Sheets, which can feed a live website or product catalog.

---

## The Problem It Solves

Writing product descriptions manually is time-consuming — someone reviews photos, writes the copy, formats features and benefits, then enters everything into a spreadsheet. With dozens or hundreds of products, this takes hours every week.

This workflow automates the entire process. Upload product photos to a Google Drive folder and run the workflow — structured descriptions appear in the spreadsheet within seconds.

---

## How It Works

```
Google Drive (folders with product photos)
        ↓
Loop through each product folder
        ↓
Download all photos of the product (multiple angles)
        ↓
GPT-4o Vision — analyze photos and generate description
        ↓
Parse AI response (name, brand, description, features, EAN)
        ↓
Google Sheets — ready row with full product description
        ↓
Website or catalog (reads directly from the spreadsheet)
```

**Google Drive folder structure:**
```
Product Photos/
  Product A/
    photo1.jpg
    photo2.jpg
  Product B/
    photo1.jpg
```

Each folder = one product. The workflow processes them one by one.

---

## What GPT-4o Generates

| Field | Description |
|-------|-------------|
| Product name | With weight or size if visible in photo |
| Brand | Manufacturer name |
| Short description | 3 sentences in a professional tone |
| Features & benefits | 2–4 lines in `feature – benefit` format |
| EAN barcode | If visible in the photo |

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Automation | n8n |
| AI Vision | GPT-4o (OpenAI) |
| Photo storage | Google Drive |
| Output | Google Sheets |

---

## Setup

1. Download `workflow_automatyzacja_opisow.json`
2. In n8n: **Import from file** → upload the JSON
3. Add your credentials: OpenAI API, Google Drive OAuth, Google Sheets OAuth
4. Replace the following placeholders in the workflow:

| Placeholder | Where to find it |
|-------------|-----------------|
| Google Drive Folder ID | Drive URL: `/folders/YOUR_ID` |
| Google Sheets Spreadsheet ID | Sheets URL: `/d/YOUR_ID/` |

5. Run the workflow manually — results appear in your spreadsheet row by row

---

## Notes

- Each product folder can contain multiple photos (different angles) — GPT-4o analyzes all of them together before generating the description
- The workflow loops through folders automatically — no manual triggering per product
- Google Sheets output can be connected directly to a website (via Sheets API, CMS, or tools like Softr / Glide)
- No credentials or sensitive data are included in the workflow JSON
