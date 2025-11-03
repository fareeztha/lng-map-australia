# 🗺️ Australia LNG Map — Leaflet + Google Sheets

A lightweight interactive map built with **Leaflet.js** and **MarkerCluster**, powered by **Google Sheets CSV** data. The map visualizes Australia’s LNG plants, upstream gas fields, and pipelines, categorized by their operational status.

---

## 🚀 Live Demo

Deployed on **Vercel** — simply open your deployment link (e.g. `https://australia-lng-map.vercel.app`).

---

## ⚙️ How It Works

1. **Google Sheets → Publish to Web → CSV**
   Each dataset (plants, fields, pipelines) must be *published to the web* and end with `&output=csv`.

2. **Paste CSV URLs into the top bar**, then click **Load / Refresh**.

3. The app will parse and render:

   * 🏭 **LNG Plants** with operator logos.
   * ⛽ **Gas Fields** colored by status (active, planned, inactive).
   * 🔗 **Pipelines** connecting plants and fields.

4. Use the **Filter buttons** to refine by:

   * Operator (auto-generated list from Sheets)
   * Project status (active, planned, inactive)

5. **Legend** at the bottom-left shows color codes for all layers.

---

## 🧩 Google Sheets Format

### 🏭 Plants Sheet

| Column              | Example           | Description         |
| ------------------- | ----------------- | ------------------- |
| plant_id            | GOR001            | Unique plant ID     |
| plant_name          | Gorgon LNG        | Plant name          |
| operator            | Chevron           | Operator name       |
| operator_logo_url   | https://...       | Logo URL (optional) |
| lat                 | -20.6             | Latitude            |
| lon                 | 115.6             | Longitude           |
| status              | Active            | Status text         |
| total_capacity_mtpa | 15.6              | LNG capacity        |
| train_count         | 3                 | Number of trains    |
| future_plan         | Expansion Train 4 | Optional notes      |

### ⛽ Fields Sheet

| Column       | Example   |
| ------------ | --------- |
| field_id     | GOR-F1    |
| field_name   | Jansz-Io  |
| operator     | Chevron   |
| basin        | Carnarvon |
| status       | Active    |
| lat          | -20.2     |
| lon          | 115.3     |
| planned_year | 2030      |
| end_year     | 2019      |

### 🔗 Pipelines Sheet

| Column        | Example                       |
| ------------- | ----------------------------- |
| pipeline_id   | PIPE-001                      |
| pipeline_name | Jansz Gas Export Pipeline     |
| status        | Active                        |
| from_type     | field                         |
| from_id       | GOR-F1                        |
| to_type       | plant                         |
| to_id         | GOR001                        |
| coords        | [[-20.2,115.3];[-20.6,115.6]] |

> **Tip:** If `coords` is empty, the app auto-connects based on `from_id` and `to_id`.

---

## 🧭 Deployment

### 1️⃣ Fork / Clone this repo

```bash
git clone https://github.com/<yourname>/australia-lng-map.git
```

### 2️⃣ Deploy to Vercel

1. Go to [vercel.com](https://vercel.com)
2. Import the repository
3. Deploy (no build step needed — it’s pure HTML+JS)

---

## 🔄 Updating Data

If you update the Google Sheet:

* Click **File → Publish to Web → Republish** if needed.
* Wait a few seconds, then click **Load / Refresh** on the site.

> Tip: A small delay (~1–3 min) is normal due to Google’s cache. You can add a cache-buster param manually:
> `https://docs.google.com/.../output=csv&_cb=12345`

---

## 🧠 Tech Stack

* [Leaflet.js](https://leafletjs.com/) — interactive map engine
* [PapaParse](https://www.papaparse.com/) — CSV parser
* [MarkerCluster](https://github.com/Leaflet/Leaflet.markercluster) — marker clustering
* [Vercel](https://vercel.com/) — static deployment

---

## 🧑‍💻 Author

Made by **[Your Name]**
For research, data visualization, and energy intelligence purposes.
Licensed under MIT.
