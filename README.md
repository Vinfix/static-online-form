# CINTEL Association – Supabase Registration Form

A responsive Google Forms-inspired static form that stores real submissions in Supabase.

## Features

- 7+ form fields
- Text, email, radio, checkbox, dropdown, number and date inputs
- Required-field validation
- Email and numeric validation
- Date validation
- Clear inline errors
- Loading state
- Success state
- Responsive mobile layout
- Supabase database integration
- Row Level Security (RLS) insert policy

## 1. Create the Supabase table

Open Supabase Dashboard -> SQL Editor and run `supabase.sql`.

The table is:

`responses(id, name, email, year, domain, skills, experience, available_date, about, created_at)`

## 2. Add your Supabase credentials

Open `config.js` and replace:

- `SUPABASE_URL`
- `SUPABASE_ANON_KEY`

Use the public/anon key, NOT a service-role key. Never expose a service-role key in frontend code.

## 3. Run locally

Because this is a static site, you can use VS Code Live Server, or any static HTTP server.

Example with Python:

```bash
python -m http.server 5500
```

Then open:

`http://localhost:5500`

## 4. Deploy

You can deploy this folder to any static hosting service such as GitHub Pages, Netlify, Vercel, or Cloudflare Pages.

After deployment, the same Supabase URL and anon key can be used from the frontend.

## Data flow

User
  ↓
Web form
  ↓
JavaScript frontend
  ↓
Supabase REST API
  ↓
PostgreSQL database

## Security note

RLS is enabled. The supplied policy permits anonymous INSERT only when basic database-side checks pass.

For a real production application, add stronger abuse protection such as CAPTCHA/rate limiting and consider authenticated admin access for viewing responses.

## Files

- `index.html` – UI
- `style.css` – responsive styling
- `script.js` – validation + Supabase insert
- `config.js` – Supabase project configuration
- `supabase.sql` – database schema + RLS
- `README.md` – setup instructions
