# Shopify Smart Sync via Google Sheets

Founder-owned project by Muhammad Faizaan 🚀  
A modern, error-proof integration between Shopify and Google Sheets.

## ✨ Features
- 🔄 Price Sync: Update Shopify variant prices directly from Google Sheets.
- 📦 Inventory Sync: Keep stock levels aligned automatically.
- 📝 Product Details: Update titles, descriptions, and tags.
- ✅ Error-Proofing: Validation checks for SKU mismatches, missing data, and API limits.
- 📊 Analytics Export: Push Shopify sales data back into Google Sheets.

## 🚀 Setup
1. Clone the repo:
   ```bash
   git clone https://github.com/Muhammad-Faizaan/shopify-smart-sync-sheets.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Configure your credentials in `config/settings.yaml`.
4. Run the sync:
   ```bash
   python src/main.py
   ```

## 🛡️ Error-Proof Design
- Validation Layer ensures only correct SKUs and data are synced.
- Rate Limiting prevents Shopify API overload.
- Logging provides detailed reports of updates, skips, and errors.
