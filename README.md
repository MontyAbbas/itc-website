# Intelligent Transportation Concepts, LLC — website

A static, single-page site. No build step, no framework, no database.
Live at https://itc-expert.com once DNS is pointed (see below).

```
website/
  index.html                    the page
  styles.css                    all styling (light and dark themes)
  favicon.svg                   browser-tab icon
  robots.txt                    lets search engines index the site
  CNAME                         tells GitHub Pages which custom domain to serve
  .nojekyll                     tells GitHub Pages to publish the files as-is
```

Open `index.html` in a browser to preview it locally.

## Hosting: GitHub Pages

The site is published from the GitHub repository `MontyAbbas/itc-website`, branch `main`,
root folder. GitHub Pages serves it free over HTTPS.

To update the site: edit the files in this folder, then

```
git add -A
git commit -m "Describe the change"
git push
```

The live site refreshes within a minute or two.

## Pointing the domain (one-time, done at Squarespace Domains)

`itc-expert.com` is registered at Squarespace Domains, so DNS is edited at
https://account.squarespace.com/domains → itc-expert.com → DNS → DNS Settings.

1. Delete the Squarespace parking records: the `A` records for `@` pointing to 198.185.159.x /
   198.49.23.x, and the `CNAME` for `www` pointing to Squarespace.
2. Add four `A` records for `@`:

   | Type | Host | Data             |
   |------|------|------------------|
   | A    | @    | 185.199.108.153  |
   | A    | @    | 185.199.109.153  |
   | A    | @    | 185.199.110.153  |
   | A    | @    | 185.199.111.153  |

3. Add a `CNAME` record with host `www` and data `montyabbas.github.io`.
4. Leave every `MX` and `TXT` record alone. They carry email.
5. Wait for DNS to propagate (minutes to an hour). Then in GitHub:
   https://github.com/MontyAbbas/itc-website/settings/pages → confirm the green check →
   tick **Enforce HTTPS** once it becomes available.

Check progress from a terminal:

```
nslookup itc-expert.com
```

It should list the four 185.199.x.153 addresses.

## Professional email on the domain

Google Workspace (about $7 per user per month). If the domain was bought during Workspace
signup, email is already configured. Otherwise sign up at workspace.google.com with the
domain and paste the MX, SPF, and DKIM records Google shows into the same Squarespace DNS
page. Moving the website does not affect email; only the `A` and `www` records change.

## Keeping the site current

1. **Email address.** The page uses `abbas@itc-expert.com` in five places (header button, hero
   button, contact button, contact list, JSON-LD block). Search and replace if it ever changes.
2. **CV.** The CV is not published; the page says it is provided to counsel on request.

Optional: add a headshot. A professional photo belongs in the hero, to the left of the
event-log figure. Ask Claude to add it once you have the file.

## Content that was deliberately kept off the site

Reviewed against the signed engagement letters on 2026-09-14.

- The caption of the patent litigation and the name of retaining counsel (confidential
  under the engagement letter; testimony is listed by court, side, type, and year only).
- The Kirkland & Ellis consulting engagement by name, and any description of that work
  (the retention letter keeps activities and conclusions confidential; listed only as an
  unnamed consulting-expert line).
- The subject of opinions given in the Richland County matter (attorney work product).
- The full CV PDF; it is sent to counsel on request instead.
- Hourly rates, the retainer amount, and contract not-to-exceed values. The page says
  the fee schedule is available on request.
- The SCC contract number and case number.
- The Virginia Tech office address and phone; the site uses the company phone only.

Everything on the page comes from the clean (non-redline) CV and the general terms in the
fee schedule and engagement agreement. Do not commit the fee schedule, the engagement
agreement, or the redline CV to this repository; it is public.
