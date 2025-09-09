# 🚀 Vercel Deployment Guide for EduXperience

## Prerequisites
- GitHub account
- Vercel account (free tier available)
- Supabase project with database set up

## Step 1: Prepare Your GitHub Repository

### 1.1 Initialize Git (if not already done)
```bash
cd /Users/tanmaygharat/Downloads/EduXperience-final-main
git init
git add .
git commit -m "Initial commit: EduXperience project setup"
```

### 1.2 Create GitHub Repository
1. Go to [GitHub.com](https://github.com) and sign in
2. Click the "+" icon in the top right corner
3. Select "New repository"
4. Name it: `eduxperience` (or your preferred name)
5. Make it **Public** (required for free Vercel deployment)
6. **Don't** initialize with README, .gitignore, or license (we already have these)
7. Click "Create repository"

### 1.3 Push Your Code to GitHub
```bash
# Add your GitHub repository as remote origin
git remote add origin https://github.com/YOUR_USERNAME/eduxperience.git

# Push your code
git branch -M main
git push -u origin main
```

## Step 2: Get Your Supabase Environment Variables

### 2.1 Access Your Supabase Project
1. Go to [Supabase Dashboard](https://supabase.com/dashboard)
2. Select your project
3. Navigate to **Settings** → **API**

### 2.2 Copy Required Values
You'll need these three values:

```
VITE_SUPABASE_URL=https://your-project-id.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
VITE_SUPABASE_SERVICE_ROLE_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

**Where to find them:**
- **Project URL**: Copy the "Project URL" from the API settings
- **Anon Key**: Copy the "anon public" key (safe for browser)
- **Service Role Key**: Copy the "service_role" key (keep this secret!)

## Step 3: Deploy to Vercel

### 3.1 Connect GitHub to Vercel
1. Go to [Vercel.com](https://vercel.com) and sign in
2. Click "New Project"
3. Click "Import Git Repository"
4. Connect your GitHub account if not already connected
5. Find and select your `eduxperience` repository
6. Click "Import"

### 3.2 Configure Project Settings
Vercel should auto-detect this as a Vite project. Verify these settings:

- **Framework Preset**: Vite
- **Root Directory**: `./` (leave as default)
- **Build Command**: `npm run build` (should be auto-filled)
- **Output Directory**: `dist` (should be auto-filled)
- **Install Command**: `npm install` (should be auto-filled)

### 3.3 Set Environment Variables
**This is the most important step!**

1. In the "Environment Variables" section, add these three variables:

   **Variable 1:**
   - Name: `VITE_SUPABASE_URL`
   - Value: `https://your-project-id.supabase.co` (your actual Supabase URL)
   - Environment: Production, Preview, Development (select all)

   **Variable 2:**
   - Name: `VITE_SUPABASE_ANON_KEY`
   - Value: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...` (your actual anon key)
   - Environment: Production, Preview, Development (select all)

   **Variable 3:**
   - Name: `VITE_SUPABASE_SERVICE_ROLE_KEY`
   - Value: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...` (your actual service role key)
   - Environment: Production, Preview, Development (select all)

2. Click "Add" for each variable
3. **Important**: Make sure all three variables are added before deploying

### 3.4 Deploy
1. Click "Deploy" button
2. Wait for the build to complete (usually 2-3 minutes)
3. Your app will be available at: `https://your-project-name.vercel.app`

## Step 4: Verify Deployment

### 4.1 Test Your Live App
1. Open your Vercel URL in a browser
2. Check if the app loads without errors
3. Test key features:
   - User registration/login
   - Database connectivity
   - All major pages load correctly

### 4.2 Check for Errors
1. Open browser developer tools (F12)
2. Check the Console tab for any errors
3. If you see Supabase connection errors, double-check your environment variables

## Step 5: Configure Custom Domain (Optional)

### 5.1 Add Custom Domain
1. In your Vercel dashboard, go to your project
2. Click "Settings" → "Domains"
3. Add your custom domain
4. Follow Vercel's DNS configuration instructions

## Troubleshooting

### Common Issues:

**1. "supabaseUrl is required" Error**
- Check that all environment variables are set correctly in Vercel
- Ensure variable names start with `VITE_`
- Redeploy after adding variables

**2. Build Fails**
- Check that all dependencies are in `package.json`
- Ensure TypeScript compilation passes locally
- Check Vercel build logs for specific errors

**3. App Loads but Features Don't Work**
- Verify Supabase database is properly set up
- Check that RLS (Row Level Security) policies are configured
- Ensure your Supabase project is active

**4. Environment Variables Not Loading**
- Make sure variables are set for all environments (Production, Preview, Development)
- Redeploy after adding new variables
- Check variable names match exactly (case-sensitive)

## Post-Deployment Checklist

- [ ] App loads without errors
- [ ] User registration works
- [ ] Database queries work
- [ ] All pages are accessible
- [ ] Mobile responsiveness works
- [ ] No console errors
- [ ] Supabase connection established

## Next Steps

After successful deployment:
1. Set up your Supabase database tables using the SQL migrations in the `supabase/migrations/` folder
2. Configure Row Level Security (RLS) policies
3. Test all features thoroughly
4. Consider setting up monitoring and analytics

## Support

If you encounter issues:
1. Check Vercel deployment logs
2. Check browser console for errors
3. Verify Supabase connection in your dashboard
4. Ensure all environment variables are correctly set

---

**🎉 Congratulations!** Your EduXperience app should now be live and accessible worldwide!
