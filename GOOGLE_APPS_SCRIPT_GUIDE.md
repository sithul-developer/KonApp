# Google Apps Script Project Update Guide

This guide explains how to update your Google Apps Script project that powers the FeulOps Fuel Management Dashboard.

## Current Google Apps Script URL
```
https://script.google.com/macros/s/AKfycbyApOlY-o8qfL7P2cdOrzAKoLKBbtEhyJh3q6ovBft4ozf2iGmkYhm6-2OgcMPwKkTlAQ/exec
```

## Understanding Your Setup

Your website (`Index.html`) embeds a Google Apps Script web app as an iframe. The Google Apps Script likely:
1. Connects to Google Sheets for data storage
2. Processes fuel management data
3. Generates reports/analytics
4. Serves HTML/CSS/JavaScript for the dashboard

## How to Update Your Google Apps Script

### Method 1: Access via Google Drive

1. **Open Google Drive**: Go to [drive.google.com](https://drive.google.com)
2. **Find the Script**: Look for files with `.gs` extension or search for "FeulOps"
3. **Open Script Editor**: Right-click on the script file → "Open with" → "Google Apps Script"

### Method 2: Direct Script Editor Access

1. **Go to Scripts Home**: Visit [script.google.com/home](https://script.google.com/home)
2. **Find Your Project**: Look for "FeulOps" or similar project name
3. **Open the Project**: Click on the project to open the editor

### Method 3: Using the Script ID

If you have the Script ID (from the URL), you can access it directly:
1. Extract the Script ID from your URL (the long alphanumeric string)
2. Go to: `https://script.google.com/d/{SCRIPT_ID}/edit`
3. Replace `{SCRIPT_ID}` with your actual script ID

## Common Update Scenarios

### 1. **Update Data Source (Google Sheets)**
```javascript
// Example: Change spreadsheet ID
var SPREADSHEET_ID = 'your-new-spreadsheet-id-here';
var sheet = SpreadsheetApp.openById(SPREADSHEET_ID);
```

### 2. **Modify Dashboard Layout/Design**
- Edit HTML/CSS files in the script project
- Look for `.html` files in the left sidebar
- Update styles, layout, or add new features

### 3. **Add New Features**
```javascript
// Example: Add new data processing function
function processNewData() {
  var sheet = SpreadsheetApp.getActiveSpreadsheet();
  var data = sheet.getDataRange().getValues();
  // Process data here
  return processedData;
}
```

### 4. **Update Deployment (After Making Changes)**
1. Click **"Deploy"** → **"New deployment"**
2. Choose deployment type: **"Web app"**
3. Configure:
   - **Execute as**: "Me" (your account)
   - **Who has access**: "Anyone" or "Anyone with Google account"
4. Click **"Deploy"**
5. **Copy the new web app URL**
6. Update the URL in `Index.html` and `.env` files

## Step-by-Step Update Process

### Step 1: Access Your Script
1. Log into your Google account
2. Navigate to the script editor using one of the methods above

### Step 2: Make Your Changes
1. **Code Files (`.gs` files)**: Add/update functions
2. **HTML Files**: Update dashboard interface
3. **Configuration**: Update spreadsheet IDs, API keys, etc.

### Step 3: Test Your Changes
1. Click **"Run"** to test functions
2. Use **"Debug"** mode for troubleshooting
3. Check execution logs under **"Executions"**

### Step 4: Redeploy
1. Go to **"Deploy"** → **"Manage deployments"**
2. Click the pencil icon (edit) on your existing deployment
3. Choose **"New version"**
4. Add version description (e.g., "Added monthly reports")
5. Click **"Deploy"**

### Step 5: Update Your Website
1. **Get the new deployment URL** (ends with `/exec`)
2. Update `Index.html`:
   ```html
   <iframe src="YOUR_NEW_URL_HERE" ...>
   ```
3. Update `.env` and `.env.example` files:
   ```
   GOOGLE_APPS_SCRIPT_URL=YOUR_NEW_URL_HERE
   ```
4. Commit and push changes to GitHub

## Troubleshooting

### Common Issues:

1. **"Script not found" error**
   - Check if you're logged into the correct Google account
   - Verify script sharing permissions

2. **"You do not have permission" error**
   - Update web app deployment settings to "Anyone" or "Anyone with Google account"
   - Re-deploy with new permissions

3. **Data not loading**
   - Check spreadsheet sharing permissions
   - Verify spreadsheet ID in code
   - Check Google Sheets API is enabled

4. **Changes not appearing**
   - Clear browser cache
   - Ensure you redeployed after making changes
   - Check you're using the latest deployment URL

## Best Practices

1. **Version Control**: Use Google Apps Script's built-in version history
2. **Backup**: Regularly export your script (File → Download)
3. **Testing**: Test changes in a copy before updating production
4. **Documentation**: Comment your code and keep this guide updated
5. **Environment Variables**: Store sensitive data in script properties:
   ```javascript
   // Set properties
   PropertiesService.getScriptProperties().setProperty('API_KEY', 'your-key');
   
   // Get properties
   var apiKey = PropertiesService.getScriptProperties().getProperty('API_KEY');
   ```

## Security Considerations

1. **API Keys**: Never hardcode API keys in your script
2. **Permissions**: Regularly review who has access to your script and spreadsheet
3. **Data Validation**: Validate all user inputs
4. **Rate Limiting**: Implement rate limiting for API calls

## Getting Help

1. **Google Apps Script Documentation**: [developers.google.com/apps-script](https://developers.google.com/apps-script)
2. **Stack Overflow**: Use tag `google-apps-script`
3. **Google Workspace Developers Community**: [developers.google.com/community](https://developers.google.com/community)

## Quick Reference

- **Script Editor**: `https://script.google.com`
- **Current Script ID**: `AKfycbyApOlY-o8qfL7P2cdOrzAKoLKBbtEhyJh3q6ovBft4ozf2iGmkYhm6-2OgcMPwKkTlAQ`
- **Deployment URL**: The URL in your `Index.html` file
- **Spreadsheet**: Likely connected to a Google Sheets document

Remember to test all changes thoroughly before updating the production dashboard!