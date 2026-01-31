# Shopify Pricelist Update

Founder-owned project by **Muhammad Faizaan** 🚀  
A modern, error-proof integration to sync product variant prices from **Google Sheets → Shopify** using SKU matching and percentage margin calculations.

---

## ✨ Features
- 📖 Read pricing data from Google Sheets (SKU, Price, Margin %)
- ➕ Calculate new prices with margin markup
- 🔄 Update Shopify product variants by SKU
- ⏭️ Skip variants that are already at the correct price
- 🛡️ Rate limiting and error handling for safe sync

---

## ⚙️ Installation
1. **Clone the repository**
   ```bash
   git clone https://github.com/Muhammad-Faizaan/shopify-smart-sync-sheets.git
   ```
2. **Install dependencies**
   ```bash
   npm install @shopify/shopify-api googleapis dotenv
   ```
3. **Create a `.env` file** with your configuration.

---

## 🔑 Environment Variables
Create a `.env` file in your project root:

```env
# Shopify Configuration
SHOP_DOMAIN=your-shop.myshopify.com
SHOPIFY_ACCESS_TOKEN=your_access_token

# Google Sheets Configuration
GOOGLE_SHEETS_ID=your_sheet_id
GOOGLE_SERVICE_ACCOUNT_EMAIL=your-service-account@project.iam.gserviceaccount.com
GOOGLE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\nYOUR_PRIVATE_KEY\n-----END PRIVATE KEY-----\n"

# Optional
GOOGLE_SHEETS_RANGE=Sheet1!A:C
```

---

## 🛠️ Getting Required Values

### Shopify Access Token (Private App Recommended)
1. Go to your Shopify admin → **Apps → App and sales channel settings**  
2. Click **Develop apps → Create an app**  
3. Configure Admin API scopes: `read_products` and `write_products`  
4. Install the app and copy the Admin API access token  

⚠️ Your app must have both `read_products` and `write_products` scopes enabled.

---

### Google Sheets Setup
1. **Get Sheet ID**  
   Copy from your Google Sheets URL:  
   ```
   https://docs.google.com/spreadsheets/d/[SHEET_ID]/edit
   ```
2. **Create Service Account**  
   - Go to Google Cloud Console  
   - Create or select a project  
   - Navigate to **APIs & Services → Credentials**  
   - Click **Create Service Account**  
   - Download the JSON key file  
   - Extract `client_email` and `private_key` values  
3. **Share Your Sheet**  
   Share your Google Sheet with the service account email (Viewer access).

---

## 📑 Sheet Format
Your Google Sheet should have these columns:

| Column | Type  | Description                  |
|--------|-------|------------------------------|
| A      | SKU   | Product variant SKU (text)   |
| B      | Price | Base price (number)          |
| C      | Margin| Margin percentage (number)   |

**Example:**
```
SKU123    10.00    25
SKU456    15.50    30
SKU789    8.99     40
```

---

## ▶️ Usage
Run the sync script:
```bash
node sync-prices.js
```

**Sample Output:**
```
Syncing prices for: your-shop.myshopify.com

Reading from sheet: 1pvDaq0-bSXsAM...
Processing 15 items

SKU123: $10.00 + 25%
Updated: $10.00 → $12.50

==================================================
Updated: 8/15 variants
==================================================
```

---

## ⚙️ How It Works
1. **Read** → Connects to Google Sheet and reads pricing data  
2. **Calculate** → Applies margin percentages to base prices  
3. **Match** → Finds Shopify variants by SKU using GraphQL  
4. **Update** → Updates variant prices via Shopify Admin API  
5. **Report** → Console logs sync results  

---

## 🛡️ Error-Proof Features
- Rate limiting (500ms delay between API calls)  
- Price validation (only updates when needed)  
- Error handling and logging  
- Read-only Google Sheets access  

---

## 🧩 Troubleshooting

### Authentication Errors
- Verify your Shopify access token has correct scopes  
- Check that your Google service account has sheet access  

### SKU Not Found
- Ensure SKUs in your sheet match exactly  
- Verify variants exist in your Shopify store  

---

## ⚠️ Warning
Always test with a **small batch first** to ensure everything works correctly.


---

✅ This README is now **complete, professional, and founder-branded** for your repo.  

Would you like me to also **add badges** (like build status, license, npm version) at the top so your README looks even more premium and GitHub-ready?
