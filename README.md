# Related Products Slider – Shopify (Collection-Based)

A **clean, lightweight Related Products slider** for Shopify product pages that intelligently shows products from the **same collection**, prioritizing **in-stock items first** and displaying only a **limited number of sold-out products**.

Designed for **better UX, faster load, and higher cross-sell conversions**.

---

## ✨ Features

* ✅ Works on **product pages**
* ✅ Automatically picks the **product’s first collection**
* ✅ Shows **in-stock products first**
* ✅ Optionally shows a few **sold-out products**
* ✅ Excludes the current product
* ✅ Horizontal scroll (mobile-friendly)
* ✅ Clean card design
* ✅ No JavaScript required
* ✅ Lightweight & fast
* ✅ Shopify OS 2.0 compatible

---

## 📂 Files Included

This version is **plug-and-play** and can be pasted directly.

```
Custom Liquid / Section / Snippet
```

(Inline CSS included for instant usage.)

---

## 🚀 Usage Options

You can use this **in two ways**:

1. **Paste directly into a Custom Liquid block**
2. **Create a reusable snippet** and render it on product pages

---

## 🚀 Option 1: Paste Directly (Custom Liquid Block)

### Steps

1. Go to **Shopify Admin → Online Store → Themes**
2. Click **Customize**
3. Open a **Product page**
4. Click **Add block**
5. Select **Custom Liquid**
6. Paste the code below
7. Click **Save**

---

### ✅ Code (Copy–Paste Ready)

```liquid
{% if product.collections.size > 0 %}
  {% assign related_collection = product.collections.first %}
{% endif %}

{% if related_collection != blank %}
<div class="rp-wrapper">
  <h2 class="rp-title">Related Products</h2>

  <div class="rp-scroll">

    {% assign shown_products = 0 %}
    {% assign max_products = 8 %}
    {% assign max_soldout = 2 %}

    {% comment %} In-stock products first {% endcomment %}
    {% for rp in related_collection.products %}
      {% if rp.id != product.id and rp.available and shown_products < max_products %}
        {% assign shown_products = shown_products | plus: 1 %}
        <a href="{{ rp.url }}" class="rp-card">
          <div class="rp-img-box">
            <img src="{{ rp.featured_image | image_url: width: 400 }}" alt="{{ rp.title }}" loading="lazy">
          </div>
          <div class="rp-info">
            <p class="rp-name">{{ rp.title }}</p>
            <p class="rp-price">{{ rp.price | money }}</p>
          </div>
        </a>
      {% endif %}
    {% endfor %}

    {% comment %} Few sold-out products {% endcomment %}
    {% assign soldout_count = 0 %}
    {% for rp in related_collection.products %}
      {% if rp.id != product.id and rp.available == false and soldout_count < max_soldout and shown_products < max_products %}
        {% assign soldout_count = soldout_count | plus: 1 %}
        {% assign shown_products = shown_products | plus: 1 %}
        <a href="{{ rp.url }}" class="rp-card rp-sold">
          <div class="rp-img-box">
            <span class="rp-badge">Sold Out</span>
            <img src="{{ rp.featured_image | image_url: width: 400 }}" alt="{{ rp.title }}" loading="lazy">
          </div>
          <div class="rp-info">
            <p class="rp-name">{{ rp.title }}</p>
            <p class="rp-price">{{ rp.price | money }}</p>
          </div>
        </a>
      {% endif %}
    {% endfor %}

  </div>
</div>
{% endif %}

<style>
.rp-wrapper { margin-top: 36px; }
.rp-title { color:#fff;font-size:18px;font-weight:700;margin-bottom:14px;text-transform:uppercase }
.rp-scroll { display:flex;gap:12px;overflow-x:auto;scroll-snap-type:x mandatory;padding-bottom:8px }
.rp-card { min-width:140px;background:#111;border:1px solid #222;border-radius:8px;text-decoration:none;color:#fff;scroll-snap-align:start }
.rp-img-box { width:100%;height:130px;background:#000;display:flex;align-items:center;justify-content:center;position:relative }
.rp-img-box img { max-width:100%;max-height:100%;object-fit:contain }
.rp-badge { position:absolute;top:8px;left:8px;background:#c0392b;color:#fff;font-size:11px;font-weight:700;padding:4px 8px;border-radius:4px;text-transform:uppercase }
.rp-sold img { opacity:0.5 }
.rp-info { padding:8px;text-align:center }
.rp-name { font-size:13px;font-weight:600;line-height:1.25;margin-bottom:4px }
.rp-price { font-size:13px;font-weight:700;color:#f5c542 }
@media(min-width:768px){ .rp-card{min-width:170px} .rp-img-box{height:150px} }
</style>
```

---

## 🚀 Option 2: Create a Reusable Snippet (Recommended)

### Step 1: Create Snippet

1. Go to **Online Store → Themes → Edit code**
2. Open **Snippets**
3. Click **Add a new snippet**
4. Name it:

```
related-products-slider.liquid
```

5. Paste the same code above
6. Click **Save**

---

### Step 2: Render Snippet

Add this line where you want it to appear:

```liquid
{% render 'related-products-slider' %}
```

Best placements:

* Below product description
* Above product recommendations
* Near reviews section

---

## 🧩 How It Works

* Automatically selects the product’s **first collection**
* Skips the current product
* Displays:

  * In-stock items first
  * Only a limited number of sold-out items
* Uses horizontal scrolling for mobile UX

---

## 🎨 Customization

You can easily adjust:

* Max products shown
* Number of sold-out products
* Card size
* Colors & typography
* Badge text

All values are easy to edit in Liquid & CSS.

---

## 🛒 Best Use Cases

* Cross-selling on product pages
* Mobile-first stores
* Faster alternative to Shopify’s default recommendations
* Stores without heavy JS sliders
* CRO-focused layouts

---

## ⭐ Support

If this snippet helped you, consider **starring ⭐ the repository**.
Feel free to fork, reuse, and customize it for your Shopify projects.

---
