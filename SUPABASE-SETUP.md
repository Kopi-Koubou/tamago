# Supabase Setup Guide

## Quick Setup (10 minutes)

### Step 1: Create Project

1. Go to https://supabase.com
2. Click **"New Project"**
3. Fill in:
   - **Name:** `tamago`
   - **Database Password:** (generate strong password, save in 1Password)
   - **Region:** (closest to you — e.g., `Singapore (ap-southeast-1)`)
   - **Pricing Plan:** Free tier (500MB DB, 1GB storage)
4. Click **"Create new project"**
5. Wait ~2 minutes for provisioning

---

### Step 2: Run Schema

1. In your project dashboard, go to **SQL Editor** (left sidebar)
2. Click **"New query"**
3. Copy entire contents of `app-rn/supabase/schema.sql`
4. Paste into SQL Editor
5. Click **"Run"** (or Cmd+Enter)

**Expected output:**
```
Success. No rows returned
```

This creates:
- `users` table (XP, streaks, achievements)
- `recipes` table (for Phase 3 UGC)
- `cooking_sessions` table (cook history)
- `user_achievements` table (badges)
- RLS policies (user isolation)
- Indexes (performance)

---

### Step 3: Get Credentials

1. Go to **Settings** (gear icon, bottom left)
2. Click **"API"**
3. Copy these values to `app-rn/.env`:

**Project URL:**
```
EXPO_PUBLIC_SUPABASE_URL=https://xxxxx.supabase.co
```

**anon/public key:**
```
EXPO_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

---

### Step 4: Test Connection

In your app, check console for:
```
✅ Supabase connected
```

If you see:
```
⚠️ Supabase not configured. Using mock client.
```

Then credentials aren't set correctly. Check `.env` and restart:
```bash
npx expo start -c
```

---

## Verification Checklist

- [ ] Project created at https://supabase.com
- [ ] Schema run successfully (no errors)
- [ ] `.env` updated with URL + anon key
- [ ] App shows "✅ Supabase connected"
- [ ] Test: Complete a recipe → Check Supabase table for new row

---

## Troubleshooting

### "Invalid API key"
- Double-check you copied the **anon/public** key (not service_role)
- Ensure no trailing spaces in `.env`

### "Relation does not exist"
- Schema didn't run successfully
- Re-run `supabase/schema.sql` in SQL Editor

### "Network request failed"
- Check internet connection
- Supabase project might still be provisioning (wait 2 min)

---

## Cost Tracking

**Free tier includes:**
- 500MB database (~250K users)
- 1GB file storage
- 50,000 monthly active users
- 2GB bandwidth/month

**Tamago estimated usage:**
- Database: ~10KB per user (XP, streaks, sessions)
- Storage: ~500KB per user (profile pics, dish photos)
- **Well within free tier for MVP**

---

## Next Steps After Setup

1. ✅ Test user signup (if implementing auth)
2. ✅ Test cloud sync (XP persists across devices)
3. ✅ Test achievement unlocking (cloud-backed)
4. ⏳ Deploy to TestFlight

---

**Questions?** Check `app-rn/STATUS.md` for build state.
