# Deployment Guide - Railway.app

## ✅ What I've Done

Your project is now ready for deployment! I've made these changes:

1. ✅ Updated `settings.py` for production
2. ✅ Created `.gitignore` (protects your secrets)
3. ✅ Created `.env.example` (template for environment variables)
4. ✅ Created `Procfile` (tells Railway how to run your app)
5. ✅ Created `runtime.txt` (specifies Python version)
6. ✅ Updated `requirements.txt` (added deployment packages: gunicorn, whitenoise)

---

## 🚀 Now: Deploy to Railway.app (FREE)

### Step 1: Create GitHub Repository
1. Go to https://github.com/new
2. Create a new repository called `construction-mgmt`
3. Push your code:

```bash
cd d:\work\villa\construction_mgmt
git init
git add .
git commit -m "Initial commit - ready for deployment"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/construction-mgmt.git
git push -u origin main
```

### Step 2: Create Railway Account
1. Go to https://railway.app
2. Click "Start Project"
3. Sign up with GitHub (easy way)

### Step 3: Deploy
1. Click "New Project" → "Deploy from GitHub"
2. Select your `construction-mgmt` repository
3. Railway will automatically detect it's Django

### Step 4: Add Environment Variables
In Railway dashboard:
1. Go to your project
2. Click "Variables" tab
3. Add these:
   - `SECRET_KEY`: Put a random string here (make one: https://djecrety.ir/)
   - `DEBUG`: `False`
   - `ALLOWED_HOSTS`: `your-app-name.railway.app`

### Step 5: Get Your URL
- After deployment, Railway gives you a URL like:
  - `https://construction-mgmt-xxxx.railway.app`
- Send this link to your father's boss! ✅

---

## ⚠️ Important Notes

### 1. Database Reset Warning
- Your SQLite database (`db.sqlite3`) will **NOT** be uploaded to the cloud
- You need to:
  - Export your current data from SQLite or
  - Recreate/seed it after deployment

### 2. If You Want to Keep Data
Run this locally first to export:
```bash
python manage.py dumpdata > data.json
```

Then in Railway, set:
```bash
python manage.py loaddata data.json
```

### 3. Login Credentials
- You'll need to recreate superuser account in Railway
- Or use Django admin to create users

---

## 📋 Checklist

Before deploying:
- [ ] Git repository created
- [ ] Code pushed to GitHub
- [ ] Railway account created
- [ ] Environment variables set in Railway
- [ ] App deployed and URL working

---

## 🆘 If Something Goes Wrong

Check Railway logs:
1. Dashboard → Project
2. "Deployments" tab
3. Click latest deployment
4. View logs to see errors

Common errors:
- **Port error**: Fixed (Railway auto-configures)
- **Static files**: Fixed (WhiteNoise handles it)
- **Database**: Use SQLite (works on Railway)

---

## 📞 Next Steps

1. **Deploy** following steps above
2. **Test** the URL in browser
3. **Send** URL to boss
4. **He can view** expenses without needing files or setup!

Questions? Let me know! 🚀
