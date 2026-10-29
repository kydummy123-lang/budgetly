BUDGETLY — SUPABASE SETUP NOTES

This version uses Supabase Auth and the existing public.budgetly_records table.

1. In Supabase, confirm Authentication > URL Configuration:
   Site URL: https://kydummy123-lang.github.io/budgetly/
   Redirect URL: https://kydummy123-lang.github.io/budgetly/

2. Confirm the public.budgetly_records table exists and Row Level Security is enabled.
   Policies must restrict SELECT/INSERT/UPDATE/DELETE to authenticated users where auth.uid() = user_id.

3. Publish the contents of this folder to the root of the GitHub Pages repository.
   Ensure index.html is at the repository root, not inside an extra nested folder.

4. Open the website, click Sign in / Profile, enter the Supabase project URL and the publishable key (sb_publishable_... or legacy anon key), then click Connect Supabase.
   Do NOT enter a database password, secret key, or service_role key.

5. Create an account or sign in. If email confirmation is enabled, confirm the email before signing in.

CLOUD DATA MODEL
This version saves the full Budgetly state in one row per user in public.budgetly_records with record_type='state'. The table should have the columns id, user_id, record_type, record_data, created_at, updated_at. The app does not currently implement separate cloud profiles; the profile label remains local to this browser.
