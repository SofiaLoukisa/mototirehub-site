# MotoTyre Service – Website

Production-ready website για βουλκανιζατέρ μηχανών.  
**Stack:** React 18 + Vite + Tailwind CSS + React Router + EmailJS

---

## Γρήγορη Εκκίνηση

```bash
# 1. Εγκατάσταση dependencies
npm install

# 2. Αντέγραψε το .env.example σε .env και συμπλήρωσε τα EmailJS keys
cp .env.example .env

# 3. Development server
npm run dev

# 4. Production build
npm run build

# 5. Preview του build
npm run preview
```

---

## Δομή Project

```
MotoTireHub/
├── public/
│   ├── images/
│   │   ├── hero-bg.jpg          ← PLACEHOLDER: βάλε την hero εικόνα
│   │   ├── og-default.jpg       ← PLACEHOLDER: Open Graph εικόνα (1200x630px)
│   │   ├── gallery/             ← PLACEHOLDER: φωτογραφίες gallery
│   │   └── brands/              ← PLACEHOLDER: logos brands (προαιρετικά)
│   ├── robots.txt
│   ├── CNAME                    ← Για GitHub Pages deploy
│   └── favicon.svg
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── Navbar.jsx
│   │   ├── Footer.jsx
│   │   ├── Hero.jsx
│   │   ├── CTAButton.jsx
│   │   ├── ServiceCard.jsx
│   │   ├── GalleryGrid.jsx
│   │   ├── BlogCard.jsx
│   │   ├── FAQAccordion.jsx
│   │   ├── ContactForm.jsx
│   │   ├── ReviewsSection.jsx
│   │   ├── BrandsSection.jsx
│   │   ├── MapSection.jsx
│   │   ├── OpeningHours.jsx
│   │   ├── SEO.jsx
│   │   └── FloatingContactButtons.jsx
│   ├── pages/
│   │   ├── Home.jsx
│   │   ├── Services.jsx
│   │   ├── Gallery.jsx
│   │   ├── Blog.jsx
│   │   ├── BlogPost.jsx
│   │   ├── FAQ.jsx
│   │   ├── Contact.jsx
│   │   └── PrivacyPolicy.jsx
│   ├── data/
│   │   ├── services.json        ← Επεξεργάσιμο: υπηρεσίες
│   │   ├── gallery.json         ← Επεξεργάσιμο: gallery
│   │   ├── blog.json            ← Επεξεργάσιμο: άρθρα blog
│   │   ├── faq.json             ← Επεξεργάσιμο: FAQ
│   │   ├── reviews.json         ← Επεξεργάσιμο: κριτικές
│   │   └── brands.json          ← Επεξεργάσιμο: brands
│   ├── layouts/
│   │   └── MainLayout.jsx
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── .env.example
├── netlify.toml
├── tailwind.config.js
├── vite.config.js
└── package.json
```

---

## Placeholders που ΠΡΕΠΕΙ να αλλάξεις πριν το deploy

### 📞 Στοιχεία Επιχείρησης
Αναζήτησε `PLACEHOLDER` σε όλα τα αρχεία. Τα βασικά σημεία:

| Αρχείο | Τι να αλλάξεις |
|--------|----------------|
| `src/components/Navbar.jsx` | `PHONE`, `PHONE_DISPLAY` |
| `src/components/Footer.jsx` | `PHONE`, `EMAIL`, `WHATSAPP_NUM`, social URLs |
| `src/components/FloatingContactButtons.jsx` | `PHONE`, `WHATSAPP_NUM`, `VIBER_NUM` |
| `src/components/Hero.jsx` | `PHONE`, `WHATSAPP_NUM` |
| `src/components/MapSection.jsx` | `MAPS_EMBED_SRC`, `MAPS_LINK` |
| `src/components/SEO.jsx` | `SITE_URL`, coordinates |
| `src/pages/Home.jsx` | social URLs |
| `src/pages/Contact.jsx` | `PHONE`, `EMAIL`, `WHATSAPP_NUM`, `VIBER_NUM`, social URLs |
| `src/pages/PrivacyPolicy.jsx` | `EMAIL`, `DOMAIN` |
| `public/CNAME` | το domain σου |
| `public/robots.txt` | το domain σου |

### 🔑 EmailJS Setup
1. Δημιούργησε λογαριασμό στο [emailjs.com](https://www.emailjs.com/)
2. Δημιούργησε Email Service και Email Template
3. Στο template χρησιμοποίησε τις μεταβλητές: `{{from_name}}`, `{{phone}}`, `{{reply_to}}`, `{{service_type}}`, `{{message}}`
4. Αντέγραψε τα keys στο `.env`:
```env
VITE_EMAILJS_SERVICE_ID=service_xxxxxxx
VITE_EMAILJS_TEMPLATE_ID=template_xxxxxxx
VITE_EMAILJS_PUBLIC_KEY=xxxxxxxxxxxxxxx
```

### 🗺️ Google Maps Embed
1. Πήγαινε στο [maps.google.com](https://maps.google.com)
2. Αναζήτησε: `Εθνάρχου Μακαρίου 66, Δάφνη Αττικής`
3. Κλικ **Share → Embed a map → Copy HTML**
4. Αντέγραψε το `src="..."` του iframe στο `MAPS_EMBED_SRC` στο `src/components/MapSection.jsx`

### 🖼️ Εικόνες
Πρόσθεσε εικόνες στους εξής φακέλους:
- `public/images/hero-bg.jpg` – Hero background (1920x1080px συνιστάται)
- `public/images/og-default.jpg` – Open Graph (1200x630px)
- `public/images/gallery/` – Gallery (workshop-1.jpg, customer-1.jpg κ.ά. – δες `src/data/gallery.json` για τα ονόματα)

---

## Deploy σε Netlify

### Αυτόματο Deploy (συνιστάται)
1. Ανέβασε τον κώδικα στο GitHub
2. Πήγαινε στο [app.netlify.com](https://app.netlify.com) → **Add new site → Import from Git**
3. Επέλεξε το repository
4. Build settings: `Build command: npm run build`, `Publish directory: dist`
5. Πρόσθεσε ENV variables (EmailJS keys) στο **Site settings → Environment variables**
6. Κάνε **Deploy**

### Χειροκίνητο Deploy
```bash
npm run build
# Ανέβασε τον φάκελο dist/ στο Netlify drag-and-drop
```

---

## Deploy σε GitHub Pages

1. Άλλαξε στο `vite.config.js`:
```js
base: '/your-repo-name/',  // ← το όνομα του GitHub repository
```

2. Εγκατάστησε gh-pages:
```bash
npm install --save-dev gh-pages
```

3. Πρόσθεσε στο `package.json`:
```json
"scripts": {
  "deploy": "npm run build && gh-pages -d dist"
}
```

4. Κάνε deploy:
```bash
npm run deploy
```

5. Στο GitHub repo → **Settings → Pages → Source: gh-pages branch**

---

## Σύνδεση Domain από Papaki

### Για Netlify
1. Στο Netlify → **Domain settings → Add custom domain**
2. Επίλεξε **Netlify DNS** (συνιστάται) ή **External DNS**:

**Με External DNS (Papaki):**
- Πρόσθεσε `A record` → `@` → `75.2.60.5`
- Πρόσθεσε `CNAME record` → `www` → `your-site.netlify.app`

**Με Netlify DNS:**
- Στο Papaki αλλαξε Nameservers σε:
  - `dns1.p05.nsone.net`
  - `dns2.p05.nsone.net`
  - `dns3.p05.nsone.net`
  - `dns4.p05.nsone.net`

### Για GitHub Pages
Στο Papaki DNS Manager:
```
A record:   @     → 185.199.108.153
A record:   @     → 185.199.109.153
A record:   @     → 185.199.110.153
A record:   @     → 185.199.111.153
CNAME:      www   → your-username.github.io
```

Στο GitHub repo → **Settings → Pages → Custom domain** → βάλε το domain σου.

**Σημείωση:** Το αρχείο `public/CNAME` περιέχει ήδη `THEMOTOTIREHUB.GR` – αλλαξε το αν αλλάξεις domain.

---

## Επεξεργασία Περιεχομένου

Όλα τα δεδομένα βρίσκονται στον φάκελο `src/data/`:

- **`services.json`** – Τίτλος, περιγραφή, εικονίδιο για κάθε υπηρεσία
- **`blog.json`** – Άρθρα blog με title, slug, content, FAQ
- **`faq.json`** – Ερωτήσεις/απαντήσεις FAQ
- **`reviews.json`** – Κριτικές πελατών
- **`gallery.json`** – Πληροφορίες gallery (paths, captions, κατηγορίες)
- **`brands.json`** – Brands ελαστικών

---

## Τεχνολογίες

| Τεχνολογία | Έκδοση | Χρήση |
|-----------|--------|-------|
| React | 18 | UI framework |
| Vite | 5 | Build tool |
| Tailwind CSS | 3 | Styling |
| React Router | 6 | Routing |
| React Helmet Async | 2 | SEO meta tags |
| EmailJS | 4 | Φόρμα επικοινωνίας |

---

## Άδεια

© 2025 MotoTyre Service – Όλα τα δικαιώματα διατηρούνται.
