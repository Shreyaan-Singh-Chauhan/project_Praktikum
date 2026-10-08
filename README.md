# MicroIntern — starter

Next.js (App Router) + Supabase (Postgres, Auth, Row Level Security).

## What works now
- Sign up (choose student or business/individual), email verification, log in/out, password reset
- Role-based accounts; database-level security so users only see/change what they should
- Profiles (college/skills for students, business name for employers)
- Employers post tasks; students browse, search and apply; employers accept/reject; mark complete
- Payments tab: **layout only** — no money moves yet

## Setup (about 10 minutes)
1. Create a free project at https://supabase.com.
2. In Supabase: **SQL Editor → New query**, paste all of `supabase/schema.sql`, click **Run**.
3. In Supabase: **Authentication → Providers → Email**, keep "Confirm email" ON.
4. In Supabase: **Authentication → URL Configuration**: set Site URL to `http://localhost:3000`
   and add `http://localhost:3000/auth/callback` to Redirect URLs (add your real domain later).
5. Copy `.env.example` to `.env.local` and fill in the Project URL and anon key
   (Supabase → Project Settings → API).
6. Run:
   ```
   npm install
   npm run dev
   ```
   Open http://localhost:3000.

## Making an admin / verifying users (until an admin panel exists)
In the Supabase SQL Editor:
```sql
update public.profiles set verified = true where id = '<user-uuid>';
update public.profiles set role = 'admin' where id = '<your-user-uuid>';
```

## Deploying
Push to GitHub, import into Vercel, add the same two env vars, and add your Vercel domain to
Supabase's Site URL / Redirect URLs. Note: Vercel's free Hobby plan is for non-commercial use.

## Next steps (not built yet)
1. Escrow payments via Razorpay Route or Cashfree Easy Split (needs a registered business + KYC).
2. Verification: college-email (.ac.in) check and business GSTIN/OTP check.
3. Chat, reviews, notifications, admin panel, disputes.
4. Under-18 flow: guardian consent, age gating (get legal advice first).
5. Before launch: terms, privacy policy, and a rate-limit/CAPTCHA on signup.

## Known simplifications
- Employers can technically edit any column of an application on their own tasks via the API; tighten
  with a column-level trigger before launch.
- Task search is simple `ilike`; switch to Postgres full-text search as data grows.
# project_Praktikum
