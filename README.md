# Vihara — Town Guide for Shravanabelagola

A fully static website that showcases everything in the town of **Shravanabelagola** —
temples, street food, markets, shops, transport, stays, healthcare and local services.
Visitors can browse by category and **Call, WhatsApp, or navigate** to any business directly.

No backend, no build step — just HTML, CSS and vanilla JavaScript. It can be hosted for
free on GitHub Pages (or any static host).

## 🚀 Host it on GitHub Pages

1. Create a new repository on GitHub (e.g. `town-gallery`) and upload **all** the files in
   this folder (keep the folder structure exactly as-is, with `index.html` at the top).
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** = *Deploy from a branch*, **Branch** = `main`,
   **Folder** = `/ (root)`, then **Save**.
4. Wait a minute — your site goes live at
   `https://<your-username>.github.io/<repo-name>/`.

> The included `.nojekyll` file tells GitHub Pages to serve the files as-is (no Jekyll
> processing), and `404.html` is used automatically as the custom "page not found" screen.

## 📁 Folder structure

```
.
├── index.html            # Homepage
├── more_categories.html  # All categories grid
├── gallery.html          # Town photo gallery (filter + lightbox)
├── add_button.html       # "Add your place" — WhatsApp submission form
├── aboutus.html          # About the project
├── map.html              # Town map + landmarks
├── 404.html              # Custom not-found page (GitHub Pages)
├── categories/           # One folder per category
│   └── <name>/
│       ├── <name>.html          # Listing page (reads the JSON below)
│       ├── <name>_details.html  # Single-place detail page
│       └── <name>_data.json     # The place data for that category
└── images/               # Photos, logos, icons
```

Categories: temples, street_food, food, bakeries, markets, retail_shops, transport,
stays, healthcare, services, education, fitness, travels, nature, bars.

## ✏️ Adding or editing a place

Open the category's `_data.json` file (e.g. `categories/food/food_data.json`) and add an
object. Common fields:

```json
{
  "id": "food9",
  "name": "New Restaurant",
  "image": "../../images/food/new_restaurant.jpg",
  "location": "Main Road, Shravanabelagola",
  "phone": "+919999999999",
  "mapLink": "https://www.google.com/maps/search/?api=1&query=New+Restaurant+Shravanabelagola",
  "status": "Open Now",
  "statusColor": "#27ae60",
  "timings": "9:00 AM - 9:00 PM",
  "description": "Short description shown on the details page."
}
```

- **`phone`** powers both the **Call** and **WhatsApp** buttons (WhatsApp opens a chat with
  that number). Use the full international format: `+91` + number.
- **`image`** — drop the photo into the matching `images/<category>/` folder and point to it.
  If the image is missing, the card falls back to a placeholder automatically.

## 📥 How "Add your place" works

`add_button.html` has a form. When a business owner fills it in and taps **Send**, WhatsApp
opens with all the details pre-formatted, sent to the site owner's number. The owner attaches
photos in the chat, then adds the listing to the right `_data.json`.

👉 **Set your own WhatsApp number:** open `add_button.html` and change the `ADMIN_WHATSAPP`
value near the bottom of the file (format: country code + number, e.g. `919876543210`).

## 🖥️ Run it locally

Because the pages load data with `fetch()`, opening the HTML directly (`file://`) won't load
the JSON. Serve it over HTTP instead:

```bash
# from this folder
python -m http.server 8000
# then open http://localhost:8000
```

## 🔧 Things to personalise

- Replace `ADMIN_WHATSAPP` in `add_button.html` with your real number.
- Update the footer contact (email / phone) in `index.html`.
- Add real photos and entries for Street Food, Markets and Transport (they ship with sample data).
- Large images in `images/logo/` and `images/story/` are several MB each — compressing them
  will make the site load faster.
