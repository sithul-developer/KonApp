# FeulOps - Fuel Management System

This is a simple web application that displays fuel management reports and analytics using an embedded PDF from Google Apps Script.

## Project Structure

- `Index.html` - Main HTML file with embedded PDF viewer
- `vercel.json` - Vercel deployment configuration
- `package.json` - Project metadata and scripts

## Deployment to Vercel

### Option 1: Deploy via Vercel CLI
1. Install Vercel CLI: `npm i -g vercel`
2. Login: `vercel login`
3. Deploy: `vercel --prod`

### Option 2: Deploy via GitHub Integration
1. Connect your GitHub repository to Vercel
2. Vercel will automatically detect the project as a static site
3. Configure build settings:
   - Build Command: (leave empty for static site)
   - Output Directory: (leave empty for static site)
   - Install Command: (leave empty for static site)

### Option 3: Deploy via Vercel Dashboard
1. Go to [vercel.com](https://vercel.com)
2. Click "New Project"
3. Import your GitHub repository
4. Configure project settings:
   - Framework Preset: Other
   - Build Command: (leave empty)
   - Output Directory: (leave empty)
5. Click "Deploy"

## Troubleshooting

If you encounter a "404: NOT_FOUND" error when deploying to Vercel:

1. **Check Vercel Project Settings**:
   - Ensure the project is correctly linked to your GitHub repository
   - Verify the root directory is set correctly

2. **Verify Configuration Files**:
   - Ensure `vercel.json` exists in the root directory
   - Check that `package.json` exists (optional but helpful)

3. **Check Build Logs**:
   - In Vercel dashboard, check the deployment logs for errors
   - Look for any missing files or configuration issues

4. **Test Locally**:
   - Open `Index.html` in a browser to verify it works
   - Check browser console for any errors related to the embedded PDF

## Local Development

Simply open `Index.html` in any modern web browser. No build process or server is required.

## Google Apps Script Integration

The dashboard embeds a Google Apps Script web application that provides:
- Real-time data processing from Google Sheets
- Interactive reports and analytics
- Dynamic chart generation

### Updating the Google Apps Script
For detailed instructions on how to update your Google Apps Script project, see:
[GOOGLE_APPS_SCRIPT_GUIDE.md](GOOGLE_APPS_SCRIPT_GUIDE.md)

## Notes

- The application embeds a Google Apps Script web app as an iframe
- If the dashboard doesn't load, check the Google Apps Script service accessibility
- The application includes fallback instructions and direct link to the dashboard

## License

MIT
