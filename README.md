# The Table — Modern Restaurant Website Template

A production-ready, full-stack restaurant website demo template built with **React**, **TypeScript**, **Vite**, **Tailwind CSS**, and **Lucide React**, backed by API endpoints compatible with both **Vercel Serverless Functions** (`/api/*`) and local **Express** development (`server.ts`).

All restaurant branding, menus, photography, opening hours, reviews, location details, and reservation rules are centralized in a single configuration file (`src/data/restaurant.ts`) so the template can be customized for any restaurant client in minutes.

---

## Project Structure

```text
├── api/
│   ├── reservations.ts         # POST /api/reservations endpoint (Vercel & Express compatible)
│   └── contact.ts              # POST /api/contact endpoint (Vercel & Express compatible)
├── src/
│   ├── assets/images/          # High-resolution culinary & interior photography assets
│   ├── components/
│   │   ├── DishModal.tsx       # Interactive dish detail & pairing modal
│   │   ├── Footer.tsx          # Site footer with hours, navigation, and contact info
│   │   ├── ImageWithFallback.tsx # Resilient image component with graceful SVG fallback
│   │   └── Navbar.tsx          # 3-zone top navigation bar & mobile drawer
│   ├── data/
│   │   └── restaurant.ts       # Central client configuration & menu dataset
│   ├── sections/
│   │   ├── Hero.tsx            # Hero banner with CTAs & quick info bar
│   │   ├── FeaturedMenu.tsx    # 6 featured signature dishes
│   │   ├── About.tsx           # Restaurant story, chef quote & key statistics
│   │   ├── FullMenu.tsx        # Categorized menu (Starters, Main Course, Burgers, Desserts, Drinks)
│   │   ├── Gallery.tsx         # Filterable photo gallery with lightbox modal
│   │   ├── Reviews.tsx         # Attributable sample guest reviews
│   │   ├── LocationHours.tsx   # Address, service hours & interactive map area
│   │   ├── ReservationSection.tsx # Validated table reservation form -> POST /api/reservations
│   │   ├── ContactSection.tsx  # Validated contact form -> POST /api/contact
│   │   └── FinalCTA.tsx        # Bottom reservation call-to-action
│   ├── types/
│   │   └── restaurant.ts       # TypeScript interfaces for config, forms & API responses
│   ├── App.tsx                 # Main application layout
│   ├── main.tsx                # React DOM entry point
│   └── index.css               # Tailwind CSS v4 & typography setup
├── .env.example                # Environment variable placeholders for client integrations
├── index.html                  # HTML entry point & SEO metadata
├── package.json                # Dependencies & scripts
├── server.ts                   # Full-stack Express + Vite server (Port 3000)
├── tsconfig.json               # TypeScript configuration
├── vercel.json                 # Vercel routing & build configuration
└── vite.config.ts              # Vite bundler configuration
```

---

## 1. Install Dependencies

```bash
npm install
```

---

## 2. Run Locally

Start the full-stack development server (Frontend + `/api/reservations` + `/api/contact` on `http://localhost:3000`):

```bash
npm run dev
```

---

## 3. Test the Backend APIs

### Test `POST /api/reservations`

```bash
curl -X POST http://localhost:3000/api/reservations \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Clara Lindqvist",
    "email": "clara@example.com",
    "phone": "+1 (555) 234-5678",
    "date": "2026-10-15",
    "time": "19:30",
    "guests": 4,
    "specialRequest": "Corner table near the hearth if available"
  }'
```

### Test `POST /api/contact`

```bash
curl -X POST http://localhost:3000/api/contact \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Marcus Thorne",
    "email": "marcus@example.com",
    "message": "We would like to inquire about a private dining room buyout for 18 guests next month."
  }'
```

---

## 4. Build for Production

```bash
npm run lint
npm run build
```

This compiles and bundles the production frontend into the `dist/` directory.

---

## 5. Deploy to Vercel

1. Push this repository to GitHub, GitLab, or Bitbucket.
2. Import the project in the [Vercel Dashboard](https://vercel.com/new) or run `npx vercel` from the project root.
3. Vercel automatically detects `vite` + `vercel.json`:
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
   - **Serverless API Routes**: `api/reservations.ts` and `api/contact.ts` are deployed automatically at `/api/reservations` and `/api/contact`.
4. *(Optional)* Add environment variables (`DATABASE_URL`, `RESEND_API_KEY`, `GOOGLE_CALENDAR_ID`, etc.) under **Project Settings → Environment Variables** when connecting a real database or email service.

---

## 6. Customizing for a New Restaurant Client

1. **`src/data/restaurant.ts` (Primary Customization File)**:
   - Update `name`, `tagline`, `hero`, `about`, `contactInfo`, `openingHours`, `socialLinks`, `menuItems`, `reviews`, `gallery`, and `reservationSettings`.
2. **`index.html` & `metadata.json`**:
   - Update the `<title>` and `<meta name="description">` tags with the client's restaurant name and city.
3. **`api/reservations.ts` & `api/contact.ts`** *(Optional)*:
   - Connect the validated `sanitized` payload to the client's database (`DATABASE_URL`), transactional email service (`RESEND_API_KEY`), or Google Calendar (`GOOGLE_CALENDAR_ID`).
