Royal Salon — Purkhoo

Single self-contained index.html — no build step, no dependencies beyond
two Google Fonts (loaded via CDN). All photos, logo, and the UPI QR code
are embedded as base64 data URIs.

Structure

This is an app-style single-page site with 4 views (Home, Info, Gallery,
Appointment) that switch via JavaScript — no page reloads, no routing.


Home — hero + 3 action cards (Salon Info / Gallery / Book Appointment)
Info — about, services with pricing, hours, gallery CTA, contact
Gallery — full photo gallery (opened via CTA in Info, or directly from Home)
Appointment — booking form, sends full details to WhatsApp on submit


Run locally

Just open index.html in a browser, or:

python3 -m http.server 8000   # then visit http://localhost:8000

Deploy with Vercel


Push this folder to a GitHub repo
Go to vercel.com → New Project → Import your repo
Leave all build settings blank (no framework, no build command)
Deploy — Vercel will serve index.html automatically


Key details


WhatsApp booking number: +91 98580 94890
UPI ID: sahilbhagat010203@okicici
Instagram: @royal_saloon.01
Location: Near Royal Farm, Purkhoo, Jammu & Kashmir
Hours: Mon/Wed–Sat 10AM–9PM, Tuesday closed, Sunday 10AM–10PM
Capacity: 10 slots/day weekdays, 15 slots/day Sunday
