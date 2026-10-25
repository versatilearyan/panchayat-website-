# Panchayat — launch landing page

Marketing site for **Panchayat** (PLAY • CHAT • CONNECT), the upcoming social gaming and voice-chat app.
Frontend only: no backend, database, auth, payments or external APIs.

Built with Next.js 16 (App Router), TypeScript, Tailwind CSS v4, Framer Motion and Lucide icons.
Fonts are bundled locally via Fontsource.

## Run it

Requires Node.js 20.9 or newer.

```bash
npm install
npm run dev                  # http://localhost:3000
npm run build && npm start   # production
```

Every route is prerendered, so it deploys as a static site (Vercel, Netlify or any Node host).

## Page

Hero → Features (Voice Rooms, Play Together, Meet Your Community) → Coming Soon → Waitlist → Footer.

## Music

The navbar has a **Play music** button. It plays `public/audio/panchayat-raag.mp3`, an original
instrumental in Raag Bhupali (bansuri-style flute, tanpura drone, tabla in Keherwa taal) that was
synthesised from scratch by `scripts/compose-music.py`, so there are no rights issues.
Music never autoplays (browsers block it, and visitors should choose); it fades in when clicked and loops.

To use a different track, replace the mp3 (keep the name, or change `TRACK` in `components/MusicToggle.tsx`).
Only use music you own or have a licence for.

## Things to set before going public

| What | Where |
| --- | --- |
| Logo | `public/brand/panchayat-logo.png` (official artwork, already in use). Settings in `BRAND` in `lib/site.ts`. |
| Favicon (placeholder crown) | Replace `app/icon.svg`. |
| Open Graph image (generated) | `app/opengraph-image.tsx`, or add a designed `app/opengraph-image.png`. |
| Production domain | `SITE.url` in `lib/site.ts`. |
| Social links / contact email | `SOCIAL_LINKS`, `CONTACT_EMAIL` in `lib/site.ts`. Empty values show as “(soon)”, never dead links. |
| Privacy Policy / Terms | Placeholder pages in `app/privacy` and `app/terms`. |
| Real waitlist | `submitToWaitlist()` in `components/sections/WaitlistForm.tsx`. |

## The waitlist form is a demo

`WaitlistForm` validates the email in the browser and shows a success state. It makes no network
request and stores nothing. To go live, replace the body of `submitToWaitlist()`.

## Structure

```
app/            layout (metadata, fonts), page, globals.css, icon, OG image, placeholder pages
components/
  brand/        Logo (uses the official PNG), Crown
  mock/         Avatar, VoiceRing, GameTile: illustrated mock UI
  sections/     Navbar, HeroSection, FeaturesSection, FeatureCard, ComingSoonSection,
                WaitlistSection, WaitlistForm, Footer, InfoPage
  ui/           Button, Reveal, SectionHeading, FloatingIcon, ComingSoonBadge
  MusicToggle.tsx
lib/            site.ts (config), mock-data.ts (fictional people and games)
public/         brand/ (logo, pattern), audio/ (music)
scripts/        compose-music.py
```
# panchayat-website-
