# Live Q&A — GitHub Pages + Supabase

## Pages
- `index.html` — audience submission form
- `admin.html` — moderator dashboard; new questions appear live
- `public.html` — approved questions; approvals appear live

## 1. Create Supabase project
Create a free Supabase project.

## 2. Create database
Open **SQL Editor**, paste `supabase.sql`, and run it.

## 3. Create moderator login
In Supabase Dashboard → Authentication → Users, create a user with email/password.
Only signed-in users can read pending questions or approve/reject them.

For a simple single-event deployment, only create moderator accounts for trusted people.

## 4. Add browser credentials
Open Supabase's **Connect** dialog (or Settings → API Keys).
Copy:
- Project URL
- Publishable key (`sb_publishable_...`)

Put both into `config.js`.

The publishable key is intentionally browser-visible. Security comes from the database RLS rules.
NEVER put a Supabase secret/service-role key in this repository.

## 5. Deploy on GitHub Pages
Upload these files to a GitHub repository.
Then: Settings → Pages → Deploy from branch → `main` / root.

Your URLs will look like:
- Audience: `https://USERNAME.github.io/REPO/`
- Admin: `https://USERNAME.github.io/REPO/admin.html`
- Public: `https://USERNAME.github.io/REPO/public.html`

Make a QR code pointing to the Audience URL.

## Important
This starter is suitable for a small event, but it deliberately stays minimal.
Before using it for an untrusted/public audience, consider anti-spam/rate-limiting (for example CAPTCHA/Turnstile via a server-side function).

The admin page is protected with Supabase Auth + RLS, not a password embedded in JavaScript.
