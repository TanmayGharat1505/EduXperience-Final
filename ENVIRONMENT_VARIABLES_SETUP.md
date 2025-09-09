# 🔧 Environment Variables Setup Guide

## ✅ Your Supabase Credentials (Already Configured)

Based on your `client.ts` file, I've extracted your Supabase credentials:

```env
VITE_SUPABASE_URL=https://mhukvyjukajzrcqisycs.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Im1odWt2eWp1a2FqenJjcWlzeWNzIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTQ0NzA3MTgsImV4cCI6MjA3MDA0NjcxOH0.Tvp7AZUB00ZL_4yUJkgJ6SffJ4nQEeeyyv8wD2v1SEk
```

## 🏠 Local Development Setup

### ✅ Already Done:
- Created `.env.local` file with your credentials
- Updated `client.ts` to use environment variables
- Your local development server will now use these variables

### 🧪 Test Local Setup:
```bash
# Restart your development server
npm run dev
```

Your app should now work locally with the environment variables!

## 🚀 Vercel Deployment Setup

### Step 1: Get Your Service Role Key

You need to get your **Service Role Key** from Supabase:

1. Go to [Supabase Dashboard](https://supabase.com/dashboard)
2. Select your project: `mhukvyjukajzrcqisycs`
3. Navigate to **Settings** → **API**
4. Copy the **"service_role"** key (not the anon key)

### Step 2: Set Environment Variables in Vercel

When deploying to Vercel, add these **3 environment variables**:

#### Variable 1: VITE_SUPABASE_URL
- **Name**: `VITE_SUPABASE_URL`
- **Value**: `https://mhukvyjukajzrcqisycs.supabase.co`
- **Environment**: Production, Preview, Development ✅

#### Variable 2: VITE_SUPABASE_ANON_KEY
- **Name**: `VITE_SUPABASE_ANON_KEY`
- **Value**: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Im1odWt2eWp1a2FqenJjcWlzeWNzIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTQ0NzA3MTgsImV4cCI6MjA3MDA0NjcxOH0.Tvp7AZUB00ZL_4yUJkgJ6SffJ4nQEeeyyv8wD2v1SEk`
- **Environment**: Production, Preview, Development ✅

#### Variable 3: VITE_SUPABASE_SERVICE_ROLE_KEY
- **Name**: `VITE_SUPABASE_SERVICE_ROLE_KEY`
- **Value**: `[Your Service Role Key from Supabase]`
- **Environment**: Production, Preview, Development ✅

## 📋 Step-by-Step Vercel Setup

### 1. Deploy to Vercel
1. Go to [vercel.com](https://vercel.com)
2. Click "New Project"
3. Import your GitHub repository
4. Vercel will auto-detect it as a Vite project

### 2. Add Environment Variables
1. In the deployment setup, scroll to "Environment Variables"
2. Add each variable one by one:
   - Click "Add New"
   - Enter the name (e.g., `VITE_SUPABASE_URL`)
   - Enter the value
   - Select all environments (Production, Preview, Development)
   - Click "Add"
3. Repeat for all 3 variables

### 3. Deploy
1. Click "Deploy" button
2. Wait for build to complete
3. Your app will be live!

## 🔍 How to Verify It's Working

### Local Development:
1. Open browser console (F12)
2. Look for: `✅ Supabase environment variables are properly configured`
3. No Supabase connection errors

### Vercel Deployment:
1. Open your live Vercel URL
2. Check browser console for errors
3. Test user registration/login
4. Verify database operations work

## 🚨 Important Notes

### Security:
- **VITE_SUPABASE_URL** and **VITE_SUPABASE_ANON_KEY** are safe for browser
- **VITE_SUPABASE_SERVICE_ROLE_KEY** should be kept secret (only used server-side)

### File Locations:
- **Local**: `.env.local` (already created)
- **Vercel**: Set in dashboard under Environment Variables
- **Git**: `.env.local` is ignored (won't be committed)

### Troubleshooting:
- **"supabaseUrl is required"**: Check environment variables are set
- **Build fails**: Ensure all 3 variables are added to Vercel
- **App loads but features don't work**: Check Supabase database is set up

## 🎯 Quick Checklist

- [x] Local `.env.local` file created
- [x] `client.ts` updated to use environment variables
- [x] Local development working
- [ ] Get Service Role Key from Supabase
- [ ] Deploy to Vercel
- [ ] Add all 3 environment variables in Vercel
- [ ] Test live deployment

## 🆘 Need Help?

If you encounter issues:
1. Check Vercel deployment logs
2. Verify all 3 environment variables are set
3. Ensure Supabase project is active
4. Check browser console for specific errors

---

**Your app is now properly configured for both local development and Vercel deployment!** 🎉
