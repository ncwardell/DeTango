# GitHub Pages Setup Guide

## Quick Setup (5 minutes)

Follow these steps to deploy your DeTango interface to GitHub Pages:

### 1. Enable GitHub Pages

1. Go to your repository on GitHub: `https://github.com/ncwardell/DeTango`
2. Click on **Settings** (top navigation)
3. Scroll down to **Pages** (left sidebar under "Code and automation")
4. Under **Source**, select:
   - **Deploy from a branch**
5. Under **Branch**, select:
   - Branch: `claude/contango-custom-ui-01FdwWmSzdzUL58hpPmbY9De` (or whichever branch you want to deploy)
   - Folder: `/ (root)`
6. Click **Save**

### 2. Wait for Deployment (1-2 minutes)

GitHub will automatically build and deploy your site. You can monitor the progress:
- Go to the **Actions** tab in your repository
- You'll see a workflow named "pages build and deployment"
- Wait for it to complete (green checkmark)

### 3. Access Your Site

Once deployed, your site will be available at:
```
https://ncwardell.github.io/DeTango/
```

The custom position builder will be at:
```
https://ncwardell.github.io/DeTango/contango-custom.html
```

## What Was Configured

✅ **index.html** - Professional landing page with feature highlights
✅ **contango-custom.html** - Enhanced custom position builder
✅ **_config.yml** - GitHub Pages configuration
✅ **.nojekyll** - Ensures all files are properly served
✅ **README-CUSTOM.md** - Updated with deployment info

## Updating Your Site

To update the live site:

1. Make changes to the HTML files locally or via Claude
2. Commit the changes:
   ```bash
   git add .
   git commit -m "Update UI"
   git push
   ```
3. GitHub Pages will automatically rebuild (1-2 minutes)

## Custom Domain (Optional)

Want to use your own domain like `detango.xyz`?

1. Buy a domain from a registrar (Namecheap, Google Domains, etc.)
2. In your domain's DNS settings, add a CNAME record:
   - **Host**: `@` or `www`
   - **Value**: `ncwardell.github.io`
3. In GitHub Pages settings:
   - Enter your custom domain (e.g., `detango.xyz`)
   - Enable "Enforce HTTPS"

## Troubleshooting

### Site not loading?
- Wait 2-3 minutes after enabling Pages
- Check the Actions tab for build errors
- Ensure branch name is correct in Pages settings

### 404 errors?
- Verify the branch has the HTML files
- Check that `.nojekyll` file exists
- Confirm you're accessing the correct URL

### Changes not showing?
- Clear your browser cache (Ctrl+Shift+R or Cmd+Shift+R)
- Wait 1-2 minutes for GitHub to rebuild
- Check GitHub Actions to see if deployment completed

## Security Notes

✅ **Safe to deploy**: All code runs client-side in the browser
✅ **No server needed**: Pure HTML/CSS/JavaScript
✅ **No API keys**: All blockchain interactions via user's wallet
⚠️ **HTTPS enforced**: GitHub Pages automatically provides SSL

## Support

- **GitHub Pages Docs**: https://docs.github.com/en/pages
- **DeTango Issues**: Open an issue in this repository
- **Contango Protocol**: https://docs.contango.xyz/

---

**Ready to go!** Your fee-free Contango interface is now accessible to anyone with the link. Share it with friends who want to avoid UI fees! 🚀
