# Todo OS (accounts + cloud storage)

Static site (no build step). Sign-in and data storage use Supabase (project `todo-os`, Mumbai). Each person's records are protected by row-level security, so one account can never read another's.

## Deploy
1. Unzip. 2. github.com > New repository `todo-os` (Private) > "uploading an existing file" > drag in everything (including the `api` and `supabase` folders) > Commit.
3. vercel.com > Add New > Project > import `todo-os` > Framework Preset **Other**, leave build settings empty > Deploy.
4. **Supabase settings (important):** supabase.com > project `todo-os` > Authentication:
   - **URL Configuration:** set Site URL to your Vercel link (for example `https://todo-os.vercel.app`) and add it under Redirect URLs. Password-reset emails use this.
   - **Sign In / Providers > Email:** for easiest setup turn **Confirm email** off. If you keep it on, new accounts must click the emailed link before signing in (the free email sender is limited to a few emails per hour).
5. Open the Vercel link, **Create account** with Sumi's email and a password, then sign in. On her other devices sign in with the same email and password.
6. Phone: Chrome > menu > **Add to Home screen** (iPhone: Safari > Share > Add to Home Screen).

## How data is stored
Records and settings are saved to her account about 2 seconds after each change, and checked every minute and when the app is reopened. The browser keeps a local copy so the app still opens offline. If two devices change the same item at once, this device's version is kept and new items from the other are added. Use More > Import / Export for a backup file now and then.

## Not included yet
Background reminders (needs n8n and a delivery channel such as email or Telegram), Cloudinary attachments, and a Figma review. Reminders currently only ring while the app is open, so set a phone alarm for critical deadlines.

## Optional: photo reading
Add `ANTHROPIC_API_KEY` in Vercel > Settings > Environment Variables and redeploy. The `/api/read` address is public, so only enable it if you accept that risk.
