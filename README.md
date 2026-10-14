# Pleasant Street Pizza Pub — website

A one-page site for **Pleasant Street Pizza Pub**, the beer-dough pizzeria at
603 NW 6th St in Gainesville's Pleasant Street historic district. They have no
website today — only a [Facebook page](https://www.facebook.com/p/Pleasant-Street-Pizza-Pub-61568619609896/)
and the ordering pages below.

Open `index.html` in a browser. Everything is relative, so it works straight off
the disk — no server, no build step.

## What's on it

| Section | What it does |
|---|---|
| Header | Sticky. Phone number is a tap-to-call button; Order Now sits next to it |
| Hero | Their storefront, then Order Now (pickup), Order Delivery and Call |
| Rating strip | 4.8★ / 174 Google reviews, with what reviewers keep mentioning |
| Made here | Three photo cards — beer dough, happy hour, wings & sauces |
| On the menu | Pizza, wings, sides and prices, pulled from their Toast menu |
| Order now | All three routes — Toast, 352 Delivery, phone |
| What people say | Six real Google reviews with star rows |
| Find us | Address, phone, full hours, happy hour, amenities, map |

On phones the nav collapses, the phone number becomes a full-width red button,
and a fixed **Order Now** bar sits at the bottom of the screen.

## The ordering links

Every "Order Now" button points at a platform they already run. Nothing on this
site takes an order itself.

| Button | Goes to |
|---|---|
| Order Now · Pickup | `order.toasttab.com/online/tbd-munecas-new-concept-603-northwest-6th-street` |
| Order Delivery | `352delivery.com/glue/pleasant-street-pizza-pub-menu/233` |
| Call | `tel:+13525055777` |

The Toast link is the same one Google's "Order online" button uses. They are not
on DoorDash, Uber Eats or Grubhub as far as I could find. To change or add a
platform, edit the `href`s in `index.html` — the Toast URL appears four times
(header, hero, menu CTA, footer) and the 352 Delivery URL three times.

## Where the content came from

Checked 14 October 2026.

- **Rating, reviews, address, hours, happy hour** — their Google Business
  listing. 4.8 stars from 174 reviews. Reviews are verbatim, trimmed to whole
  sentences and attributed by name.
- **Menu and prices** — their own Toast ordering menu.
- **Photographs** — all theirs: `storefront`, `pizza-sausage` from the owner
  uploads on their Google listing, `pizza-pepperoni`, `slice` and `boxes` from
  their Facebook page. No customer photos are used.

## Things to confirm with the owners

1. **Photos.** These are the best versions publicly available, but `slice.jpg`
   (541px) and `boxes.jpg` (900px) are small. Originals from their phone would
   look better, and a wings shot is the obvious gap.
2. **Hours.** Google says Tue–Sat 11am–10pm, Sun 11am–7pm, closed Monday, and a
   recent visitor update says "Open Sunday!!". Worth a sanity check — Yelp still
   lists older 11am–9pm hours.
3. **Prices.** Taken from the Toast menu, which is the live one, but the site
   says so in small print under the menu in case it drifts.
4. **Domain.** Currently deploys to a `.vercel.app` subdomain. If they own a
   domain, point it at the Vercel project and update `<link rel="canonical">`,
   the `og:*` URLs and `sitemap.xml`.

## Deploying

Static — no framework, no build command. On Vercel, import the repo at
[vercel.com/new](https://vercel.com/new/import?s=https://github.com/michaeljpreviti-ops/pleasant-street-pizza-pub),
accept the defaults and it ships; every push to `main` redeploys.

`vercel.json` sets `cleanUrls`, a one-year immutable cache on `/images/*`, and
`X-Content-Type-Options`, `Referrer-Policy` and `X-Frame-Options`.
