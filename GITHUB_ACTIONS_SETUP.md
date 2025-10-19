# GitHub Actions Setup Guide for Portfolio

This guide will walk you through setting up GitHub Actions for your portfolio website.

## 🚀 What We've Set Up

### 1. **Automatic Deployment Workflow** (`.github/workflows/deploy.yml`)
- Deploys to Netlify when you push to the `main` branch
- Runs HTML and CSS linting
- Includes Lighthouse performance checks
- Only deploys on successful linting

### 2. **Pull Request Checks** (`.github/workflows/pr-check.yml`)
- Runs code quality checks on pull requests
- Validates HTML structure
- Checks for broken links and missing images
- Prevents merging of low-quality code

### 3. **Configuration Files**
- `.htmlhintrc` - HTML linting rules
- `.stylelintrc.json` - CSS linting rules
- `.lighthouserc.json` - Performance audit settings
- `package.json` - Dependencies and scripts

## 🔧 Setup Steps

### Step 1: Get Netlify Credentials

1. **Go to your Netlify dashboard**
2. **Navigate to Site Settings → General**
3. **Copy your Site ID** (looks like: `abc123def-456-789`)

4. **Get your Auth Token:**
   - Go to **User Settings → Applications → Personal access tokens**
   - Click **"New access token"**
   - Give it a name like "GitHub Actions"
   - Copy the token (you won't see it again!)

### Step 2: Add Secrets to GitHub

1. **Go to your GitHub repository**
2. **Click Settings → Secrets and variables → Actions**
3. **Add these repository secrets:**

   ```
   NETLIFY_AUTH_TOKEN = [your-netlify-token]
   NETLIFY_SITE_ID = [your-site-id]
   ```

### Step 3: Push Your Changes

```bash
git add .
git commit -m "Add GitHub Actions workflows"
git push origin main
```

### Step 4: Verify Setup

1. **Check the Actions tab** in your GitHub repository
2. **You should see workflows running**
3. **Check your Netlify dashboard** for deployment status

## 📋 What Each Workflow Does

### Deploy Workflow (on push to main)
1. **Lints your HTML and CSS** for quality issues
2. **Deploys to Netlify** if linting passes
3. **Runs Lighthouse audit** for performance metrics
4. **Fails if any step fails** (prevents bad deployments)

### PR Check Workflow (on pull requests)
1. **Validates HTML structure**
2. **Checks for broken links**
3. **Ensures images exist**
4. **Runs linting** to catch issues early

## 🛠️ Local Development

You can run the same checks locally:

```bash
# Install dependencies
npm install

# Run HTML linting
npm run lint:html

# Run CSS linting
npm run lint:css

# Run all linting
npm run lint
```

## 🎯 Benefits

- **Automatic deployments** - No manual deployment needed
- **Code quality** - Catches issues before they go live
- **Performance monitoring** - Lighthouse audits your site
- **Professional workflow** - Shows you understand CI/CD
- **Error prevention** - Stops bad code from being deployed

## 🔍 Monitoring

- **GitHub Actions tab** - See workflow status
- **Netlify dashboard** - Monitor deployments
- **Lighthouse reports** - Track performance over time

## 🚨 Troubleshooting

### If deployment fails:
1. Check the **Actions tab** for error details
2. Verify your **Netlify secrets** are correct
3. Check that your **Site ID** is accurate

### If linting fails:
1. Run `npm run lint` locally to see issues
2. Fix the reported problems
3. Commit and push again

### If Lighthouse fails:
1. Check your site's performance
2. Optimize images and code
3. Consider the suggested improvements

## 📈 Next Steps

Once this is working, you could add:
- **Automated testing** (if you add JavaScript)
- **Security scanning**
- **Dependency updates**
- **Performance budgets**

---

**Your portfolio now has professional CI/CD! 🎉**
