# TEVESO E-Shop — Free Setup Guide

## Files included
- `index.html` — the complete website
- `products.json` — your product catalog (edit this to add/remove products)
- `images/` — place product images here named by Part Number (e.g. `825016.jpg`)
- `README.md` — this guide

---

## STEP 1: Publish FREE on GitHub Pages

1. Go to https://github.com and create a free account (if you don't have one)
2. Click **New repository** → name it `teveso-shop` → set to **Public** → Create
3. Upload all files from this folder to the repository
4. Go to **Settings → Pages → Source → main branch / root** → Save
5. Your site will be live at: `https://YOUR-USERNAME.github.io/teveso-shop`

**Custom domain (optional):**  
Buy domain at Wedos.cz (~200 Kč/year), then in GitHub Pages settings add your custom domain (e.g. `shop.teveso.cz`).

---

## STEP 2: Set Up Stripe Payments (Free)

Stripe charges NO monthly fee — only ~1.4% + 25 Kč per transaction.

### Create Stripe account
1. Go to https://stripe.com → Create account
2. Complete business verification (TEVESO, s.r.o. details)

### Get your publishable key
1. In Stripe Dashboard → **Developers → API keys**
2. Copy your **Publishable key** (starts with `pk_live_...`)
3. Open `index.html`, find this line:
   ```
   const STRIPE_PUBLISHABLE_KEY = 'pk_test_REPLACE_WITH_YOUR_KEY';
   ```
   Replace with your actual key.

### Option A — Stripe Payment Links (EASIEST, no coding)
1. In Stripe Dashboard → **Payment Links → Create**
2. Add your products
3. Copy the link (e.g. `https://buy.stripe.com/xxxxx`)
4. In `index.html`, find the `checkout()` function and uncomment:
   ```js
   window.location.href = 'YOUR_STRIPE_PAYMENT_LINK';
   ```
5. Set `const STRIPE_CONFIGURED = true;`

### Option B — Full Stripe Checkout (better UX)
This requires a small backend function (free with Netlify or Vercel).
Contact AJ or a developer to set up.

---

## STEP 3: Add Products

Edit `products.json` to add, remove, or update products.

Each product entry:
```json
{
  "id": "825016",              ← Part number (must be unique)
  "name_cs": "Olejový filtr",  ← Czech name
  "name_en": "Oil Filter",     ← English name
  "desc_cs": "Popis...",       ← Czech description
  "desc_en": "Description...", ← English description
  "price": 371,                ← Price in CZK (without DPH or with — your choice)
  "currency": "CZK",
  "category": "accessories",
  "engine": ["912", "914"],    ← Which engines this fits
  "image": "images/825016.jpg",← Image path (or remove this line for placeholder)
  "stripe_price_id": "price_REPLACE_ME"  ← From Stripe dashboard
}
```

### Engine options
Use any combination of: `"912"`, `"914"`, `"915"`, `"916"`

### Categories
Use: `"accessories"`, `"cooling"`, `"oil"`, `"fuel"`, `"ignition"`, `"electrical"`

---

## STEP 4: Add Product Images

1. Take photos or use manufacturer images
2. Name each image file by Part Number: `825016.jpg`, `297656.png`, etc.
3. Place them in the `images/` folder
4. The website will auto-display them

Recommended size: **800×600 px**, JPEG or PNG, white/transparent background.

---

## Cost Summary

| Service | Cost |
|---|---|
| GitHub Pages hosting | FREE |
| Custom domain (optional) | ~200 Kč/year |
| Stripe account | FREE |
| Stripe per-transaction fee | ~1.4% + 25 Kč |
| **Monthly subscription (Shoptet)** | **ELIMINATED** |

---

## Need help?

Email: motory@teveso.cz  
Phone: +420 495 217 127
