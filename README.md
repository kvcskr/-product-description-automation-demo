# Product Description Automation — n8n + GPT-4o Vision

An n8n workflow that automatically generates ready-to-publish product descriptions from photos stored in Google Drive. Results are saved to Google Sheets, which feeds directly into a live website.

---

## The problem it solves

Previously, every product description had to be written manually — someone would review the photos, write the text, format the features and benefits, then copy everything into a spreadsheet. With dozens or hundreds of products, this took hours every week.

This workflow does it automatically. Just upload product photos to the right folder on Google Drive and run the workflow.

---

## How it works

```
Google Drive (folders with product photos)
        ↓
Loop through each product folder
        ↓
Download all photos of the product (multiple angles)
        ↓
GPT-4o Vision — analyze photos and generate description
        ↓
Parse response (name, company, description, features, EAN)
        ↓
Google Sheets — ready row with full product description
        ↓
Website (connected directly to the spreadsheet)
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

## What GPT-4o generates

For each product:

- **Product name** with weight/size
- **Brand** (manufacturer)
- **Short description** — 3 sentences in a professional gastronomy tone
- **Features & benefits** — 2–4 lines in `feature – benefit` format
- **EAN barcode** — if visible in the photos

---

## Stack

| Tool | Role |
|---|---|
| n8n | Workflow orchestration |
| Google Drive | Source of product photos |
| GPT-4o Vision (OpenAI) | Photo analysis and description generation |
| Google Sheets | Output database, connected to website |

---

## How to import

1. Download `workflow_automatyzacja_opisow.json`
2. In n8n: **Import** → upload the file
3. Replace placeholders in the workflow:
   - Your Google Drive folder ID
   - Your Google Sheets spreadsheet ID
   - Add your own credentials for Google Drive, Google Sheets, and OpenAI
4. Run

---

## Result

Every run adds new rows to the spreadsheet with complete, ready-to-publish product descriptions — no manual writing, no copying, no formatting.
