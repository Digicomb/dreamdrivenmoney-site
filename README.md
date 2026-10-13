# dreamdrivenmoney.com

Astro site for Dream Driven Money (financial coaching with Jennifer Orr), built on the same structure as missional.io and digitalhoneycomb.com.

| Command           | Action                                  |
| :---------------- | :-------------------------------------- |
| `npm install`     | Install dependencies                    |
| `npm run dev`     | Dev server at `localhost:4321`          |
| `npm run build`   | Build to `./dist/`                      |
| `npm run preview` | Preview the production build locally    |

- Content: `src/pages/index.astro` (approach, services, steps and FAQs are arrays at the top).
- Hero art: `src/components/Landscape.astro`. Jennifer's photo slot is the `.portrait` block in the About section.
- Icons: edit `public/favicon.svg` (keep `src/assets/logo.svg` in sync), then run `node scripts/make-icons.cjs`.
- Deploy: `.github/workflows/deploy.yml` publishes to GitHub Pages on push to `main`.

## Contact form

The discovery call form inserts into `ddm_contact_requests` in the shared Digicomb Supabase project (also used by missional.io, which owns the keep-alive job). The public key can insert but not read. A database trigger emails each request through Resend, with the visitor as reply-to.

Setup: run `supabase/migrations/001_ddm_contact_requests.sql` in the Supabase SQL Editor, then create the two Vault secrets listed in it.
