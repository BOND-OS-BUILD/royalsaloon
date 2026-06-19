# Royal Salon — Purkhoo

Single self-contained `index.html` with a real Supabase backend for live
slot tracking. No build step — just static HTML + JS that talks to Supabase
directly over its REST API.

## Structure
App-style single-page site, 4 views (Home, Info, Gallery, Appointment)
switching via JavaScript — no page reloads.

- **Home** — hero + 3 action cards
- **Info** — about, services with pricing, hours, gallery CTA, contact
- **Gallery** — full photo gallery
- **Appointment** — booking form with LIVE slot availability

## How slot booking works
- Picking a date fetches real bookings for that date from Supabase and
  greys out taken slots — accurate for every visitor, not just the
  browser that made the booking.
- Submitting a booking inserts a row into the `bookings` table. A unique
  constraint on (date, time_slot) means two people can't double-book the
  same slot even if they submit at the same moment.
- After a booking is saved, the form opens WhatsApp with the full details
  pre-filled, sent to the salon's number.

## Owner: managing bookings
Scroll to the bottom of the Appointment page → "Owner: Manage Bookings".
Enter the date and the owner passcode to see who's booked and free up
any slot (e.g. if a customer cancels by phone).

**Owner passcode:** royal2026free
(Change this in the Supabase database function `delete_booking_with_passcode`
if you want a different one — ask Claude to update it.)

## Backend (Supabase)
- Project: `royal-salon-purkhoo` (separate from any other Supabase projects)
- Project URL: https://pwinuwysyewmnolgejsk.supabase.co
- Table: `bookings` (date, time_slot, customer_name, phone, service, payment_method, notes)
- Row Level Security: public can read & insert (needed for the public booking
  form); deletes only happen through a passcode-protected database function.

## Run locally
Open `index.html` directly, or:

    python3 -m http.server 8000

## Deploy with Vercel
1. Push this folder to a GitHub repo
2. vercel.com → New Project → Import your repo
3. Leave all build settings blank (no framework, no build command)
4. Deploy

## Key details
- WhatsApp booking number: +91 98580 94890
- UPI ID: sahilbhagat010203@okicici
- Instagram: @royal_saloon.01
- Location: Near Royal Farm, Purkhoo, Jammu & Kashmir
- Hours: Mon/Wed–Sat 10AM–9PM, Tuesday closed, Sunday 10AM–10PM
- Capacity: 10 slots/day weekdays, 15 slots/day Sunday (shown as info only —
  actual enforcement is per-slot via the live availability system)
