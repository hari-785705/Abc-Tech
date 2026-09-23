# ABC Tech — Company Website

A simple 2-page static site: a home page and a login page, linked to each other.

## Folder structure

```
site/
├── index.html          ← Home page (was "SOFTWARE COMPANY.html")
├── about.html           ← About Us page
├── services.html        ← Services page
├── contact.html         ← Contact Us page (with a front-end contact form)
├── login.html           ← Login page (was "login  page 1.html")
├── register.html        ← Registration page
├── assets/
│   └── img/
│       ├── home-bg.jpg   ← page background, used on every page (was "Soft 1.jpg")
│       └── login-bg.jpg  ← login page background (was 123.jpg)
└── README.md
```

## Branding

The logo is a pure-CSS tech mark: a pulsing gradient hexagon badge
("AT", for ABC Tech) in a cyan → blue → violet gradient, paired with an
animated shimmering **ABC Tech.** wordmark and the tagline "Powering
Ideas Into Code". It's shown consistently on every page, with a matching
version on the login/register card. No image file is needed for the
logo, so it stays crisp at any size and loads instantly.

## How the pages link together

Every page shares the same header and nav bar, so you can jump between any
of them from anywhere on the site:

- **HOME** → `index.html`
- **ABOUT** → `about.html`
- **SERVICES** → `services.html`
- **CONTACT US** → `contact.html`
- **LOGIN** → `login.html`
- `register.html` now redirects straight into `login.html#register` (kept
  only so old links keep working)

All pages reference images with **relative paths** (`assets/img/...`)
instead of the original absolute `C:\Users\COPA\Desktop\...` paths, so the
site works from any folder or web server, including GitHub Pages.
Icons/fonts (Font Awesome, Ionicons, Google Fonts) load from public CDNs,
so an internet connection is needed when viewing the pages.

## Responsive design

Every page now has a proper viewport meta tag and fluid, mobile-friendly
CSS:

- The header (logo + search + nav) is a wrapping flexbox — it stacks and
  centers itself on narrow screens instead of overlapping
- The background photo now uses `background-size: cover` so it fills the
  screen correctly at any width, on any device
- A `max-width: 640px` breakpoint shrinks the logo, tagline, and nav text,
  and gives page content more breathing room on phones
- The login/register card already used `max-width: 90vw` with fluid units;
  it now also has a small `max-width: 420px` breakpoint that trims its
  padding and background blobs so nothing feels cramped on small phones
- The Services cards and Contact form were already flex/percentage based,
  so they reflow into a single column automatically on narrow screens

## Login page — dynamic & interactive

`login.html` is now a single animated auth card with a sliding
**Login / Register** tab switcher — no page reload when you flip between
them. It also includes:

- A dark, glassmorphism card over an animated tech background: a moving
  grid, three drifting gradient blobs, and rising particles
- Show/hide (eye icon) toggles on every password field
- A live password-strength meter and a real-time "passwords match" hint
  as you type on the Register tab
- Submitting Register validates the form, then dynamically flips to the
  Login tab and shows a green "Account created" banner — all without
  leaving the page

The contact form on `contact.html` and both auth forms are front-end
only (no backend yet) — nothing is actually stored until they're wired
up to a real backend or auth service (e.g. Firebase Auth, Supabase, or a
custom API).

## Run locally

No build step needed — just open `index.html` in a browser, or serve the
folder so relative paths behave consistently:

```bash
cd site
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Put it on GitHub

```bash
cd site
git init
git add .
git commit -m "Initial commit: ABC Tech site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

## Host it free with GitHub Pages

1. On GitHub, open your repo → **Settings → Pages**.
2. Under **Build and deployment**, set **Source** to `Deploy from a branch`.
3. Choose branch `main`, folder `/ (root)`, then **Save**.
4. After a minute, your site is live at:
   `https://<your-username>.github.io/<repo-name>/`
   - Home: `.../index.html` (also the default page)
   - Login: `.../login.html`

## Notes / unused files

The nav bar only lists the five pages that actually exist — HOME, ABOUT,
SERVICES, CONTACT US, LOGIN. The earlier placeholder items (SOLUTIONS,
INDUSTRIES, TECHNOLOGIES, PORTFOLIO, COSTS) that went nowhere have been
removed. Two large stock photos from the original zip
(`group-people-working-team.jpg` and the "programming background" photo)
weren't referenced by either page, so they were left out to keep the repo
small; add them back into `assets/img/` and reference them if you want to
use them on a page.
