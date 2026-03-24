# davidel.dev — Portofoliu Personal

Site personal construit cu **Astro**, optimizat pentru deployment pe **Cloudflare Pages**.

---

## 🗂 Structura proiectului

```
davidel-portfolio/
├── public/
│   ├── favicon.svg          # Favicon-ul site-ului
│   └── _redirects           # Config Cloudflare Pages
├── src/
│   ├── data/
│   │   └── projects.json    # ⭐ EDITEAZĂ AICI proiectele
│   ├── layouts/
│   │   └── Layout.astro     # Navbar + Footer + meta tags
│   ├── pages/
│   │   ├── index.astro      # Pagina Home
│   │   ├── about.astro      # Pagina About
│   │   ├── projects.astro   # Pagina Projects
│   │   ├── contact.astro    # Pagina Contact
│   │   └── 404.astro        # Pagina 404
│   └── styles/
│       └── global.css       # Design system global
├── astro.config.mjs
└── package.json
```

---

## ✏️ Ce și unde editezi

### 1. Informații personale — `src/layouts/Layout.astro`
- **Linia 6**: `description` implicită a site-ului
- **Footer**: editează linkurile GitHub, LinkedIn, Email (căutare `footer-links`)

### 2. Proiecte noi — `src/data/projects.json`
Adaugă un obiect nou în array:
```json
{
  "id": 4,
  "title": "Numele proiectului",
  "description": "Ce face proiectul în 1-2 propoziții.",
  "stack": ["React", "Node.js", "PostgreSQL"],
  "demo": "https://demo.example.com",
  "github": "https://github.com/davidel/proiect",
  "featured": false
}
```
- `demo` și `github` pot fi `""` dacă nu există
- `featured: true` adaugă badge-ul "Featured" pe card

### 3. Informații About — `src/pages/about.astro`
- **Linia 4-8**: obiectul `skills` — categorii și tehnologii
- **Linia 18-32**: array-ul `experience` — job-uri / proiecte majore
- **Secțiunea bio**: textul personal (caută `<h2>Salut, sunt`)
- **Linkurile bio**: GitHub, LinkedIn, Email (caută `bio-links`)

### 4. Contact & Social — `src/pages/contact.astro`
- **Linia 4-36**: array-ul `socials` — editează `href` și `value`
- **Formularul**: înlocuiește `YOUR_FORM_ID` cu ID-ul de la Formspree (formspree.io)

### 5. Hero Home — `src/pages/index.astro`
- Subtitlul (caută `hero-sub`)
- Skills strip (caută `Tech stack`)

---

## 📬 Formular de contact (Formspree)

1. Creează cont gratuit pe [formspree.io](https://formspree.io)
2. Creează un nou form — copiază Form ID (ex: `xabcdefg`)
3. În `contact.astro`, înlocuiește:
   ```
   https://formspree.io/f/YOUR_FORM_ID
   ```
   cu:
   ```
   https://formspree.io/f/xabcdefg
   ```
Alternativă: șterge `action` și `method` din form și gestionează cu un Cloudflare Worker sau Web3Forms.

---

## 💻 Rulare locală

```bash
# Instalează dependențele
npm install

# Pornește server dev (http://localhost:4321)
npm run dev

# Build pentru producție
npm run build

# Preview build local
npm run preview
```

---

## 🚀 Deploy pe Cloudflare Pages

### Prima dată (setup)
1. Push codul pe **GitHub** (sau GitLab)
2. Mergi pe [pages.cloudflare.com](https://pages.cloudflare.com)
3. Click **Create a project** → **Connect to Git**
4. Selectează repository-ul `davidel-portfolio`
5. Configurare build:
   - **Framework preset**: Astro
   - **Build command**: `npm run build`
   - **Build output directory**: `dist`
6. Click **Save and Deploy** ✅

### Adăugare domeniu custom
1. În Cloudflare Pages → proiectul tău → **Custom domains**
2. Click **Set up a custom domain**
3. Introdu `davidel.dev`
4. Urmează instrucțiunile pentru DNS (dacă domeniul e pe Cloudflare, e automat)

### Deploy-uri viitoare
Orice `git push` pe branch-ul principal → Cloudflare Pages redeploy-ează automat. Nu trebuie să faci nimic manual.

---

## ➕ Adăugare proiect nou (flux complet)

```bash
# 1. Editează fișierul JSON
nano src/data/projects.json

# 2. Commit și push
git add src/data/projects.json
git commit -m "add: proiect nou X"
git push

# 3. Cloudflare Pages se redeploy-ează automat în ~1 minut
```

---

## 🎨 Paletă de culori

| Variabilă | Valoare | Utilizare |
|---|---|---|
| `--bg-primary` | `#080810` | Background principal |
| `--accent` | `#8b5cf6` | Violet principal |
| `--accent-bright` | `#a78bfa` | Violet deschis |
| `--text-primary` | `#f0eeff` | Text principal |
| `--text-secondary` | `#a09bc0` | Text secundar |

Toate culorile sunt CSS variables în `src/styles/global.css`.

---

## 🔧 De ce Astro?

- **Static site generation** — perfect pentru Cloudflare Pages (fișiere HTML pure)
- **Zero JS by default** — site rapid, fără bundle inutil
- **Component-based** — ușor de extins cu noi pagini/componente
- **Markdown support** — poți scrie pagini în `.md` dacă vrei un blog
- **Oficial suportat** pe Cloudflare Pages
