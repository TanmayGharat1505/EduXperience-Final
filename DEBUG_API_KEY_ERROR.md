# 🔍 Debug "Invalid API key" Error

## 🚨 The Error
```
Error: Invalid API key
```

This error means Supabase can't authenticate with the provided API key.

## 🔍 Step-by-Step Debugging

### Step 1: Verify Environment Variables in Vercel

1. **Go to your Vercel project dashboard**
2. **Click "Settings" → "Environment Variables"**
3. **Check that these 3 variables exist:**

   ✅ **VITE_SUPABASE_URL** = `https://mhukvyjukajzrcqisycs.supabase.co`
   ✅ **VITE_SUPABASE_ANON_KEY** = `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...`
   ✅ **VITE_SUPABASE_SERVICE_ROLE_KEY** = `[Your service role key]`

4. **Make sure ALL environments are selected** (Production, Preview, Development)

### Step 2: Verify Your Supabase API Keys

1. **Go to [Supabase Dashboard](https://supabase.com/dashboard)**
2. **Select your project: `mhukvyjukajzrcqisycs`**
3. **Go to Settings → API**
4. **Verify these values match what you set in Vercel:**

   - **Project URL**: `https://mhukvyjukajzrcqisycs.supabase.co`
   - **anon public key**: Should match your `VITE_SUPABASE_ANON_KEY`
   - **service_role key**: Should match your `VITE_SUPABASE_SERVICE_ROLE_KEY`

### Step 3: Check if API Keys Have Changed

**If the keys don't match:**
1. **Copy the current keys from Supabase**
2. **Update them in Vercel Environment Variables**
3. **Redeploy your project**

### Step 4: Test Local vs Production

**Test locally first:**
```bash
# Your local .env.local should work
npm run dev
# Visit http://localhost:8080
# Check if login works locally
```

**If local works but Vercel doesn't:**
- Environment variables aren't set correctly in Vercel
- Need to redeploy after setting variables

### Step 5: Add Debug Logging

Let me add some debug logging to help identify the issue:

```typescript
// Add this to your client.ts temporarily for debugging
console.log('🔍 Debug Info:');
console.log('SUPABASE_URL:', SUPABASE_URL);
console.log('SUPABASE_PUBLISHABLE_KEY:', SUPABASE_PUBLISHABLE_KEY?.substring(0, 20) + '...');
console.log('Using env vars:', {
  hasUrl: !!import.meta.env.VITE_SUPABASE_URL,
  hasKey: !!import.meta.env.VITE_SUPABASE_ANON_KEY
});
```

## 🚨 Common Issues & Solutions

### Issue 1: Environment Variables Not Set
**Symptom**: App works locally but not on Vercel
**Solution**: Set all 3 environment variables in Vercel dashboard

### Issue 2: Wrong API Key
**Symptom**: "Invalid API key" error
**Solution**: Copy fresh keys from Supabase dashboard

### Issue 3: Keys Regenerated
**Symptom**: Worked before, now doesn't work
**Solution**: Supabase keys were regenerated, need to update Vercel

### Issue 4: Wrong Environment Selected
**Symptom**: Variables set but not working
**Solution**: Make sure to select ALL environments (Production, Preview, Development)

## 🔧 Quick Fix Steps

1. **Get fresh API keys from Supabase**
2. **Update Vercel environment variables**
3. **Redeploy the project**
4. **Test the live URL**

## 📋 Verification Checklist

- [ ] Vercel has all 3 environment variables
- [ ] All environments selected (Production, Preview, Development)
- [ ] API keys match Supabase dashboard
- [ ] Project redeployed after setting variables
- [ ] Local development works (for comparison)
- [ ] Browser console shows no other errors

## 🆘 If Still Not Working

1. **Check Vercel build logs** for any errors
2. **Check browser console** for more specific error messages
3. **Try regenerating API keys** in Supabase
4. **Verify project is active** in Supabase dashboard

---

**The most common cause is environment variables not being set correctly in Vercel!** 🎯
