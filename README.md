# MARD

**Predictive Modeling of Antibody Thermostability: Evaluation and Ranking of Machine Learning Models for Prediction Performance Based on Amino Acid Sequences**

This repository hosts figures from the MARD project for public access. Every figure is available via a direct URL **and** via a scannable QR code, making it easy to reference figures from printed materials, posters, or presentations without typing long URLs.

---

## 📊 Figure Gallery

Browse the full figure gallery — with inline previews and QR codes — at the GitHub Pages site:

**🔗 https://technareri.github.io/MARD/**

---

## 📱 Accessing Figures via QR Code

Each figure has a QR code on the gallery page that encodes the figure's raw GitHub URL:

```
https://raw.githubusercontent.com/technareri/MARD/main/figures/<filename>
```

Scan any QR code with a smartphone camera to open the full-resolution figure directly.

---

## 🗂 Repository Structure

```
MARD/
├── figures/          # Project figures (PNG / JPG / SVG / PDF)
│   └── README.md     # Figure directory documentation
├── docs/
│   └── index.html    # GitHub Pages gallery with QR codes
└── README.md
```

---

## ➕ Adding New Figures

1. Place the figure file in the `figures/` directory.
2. Open `docs/index.html` and add a new entry to the `FIGURES` array near the bottom of the `<script>` block:

```js
{
  file:    "figureN_short_name.png",
  label:   "Category",
  title:   "Figure N – Descriptive Title",
  caption: "One-sentence description of the figure."
}
```

3. Commit and push — the gallery updates automatically.
