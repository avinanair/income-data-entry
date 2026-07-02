# Admin Setup Guide - Complete Deployment Instructions

## 🚀 Overview

This guide walks you through setting up the Income Data Entry System for your organization. The frontend files are hosted in GitHub, while the backend (Google Apps Script) runs in your Google Sheet.

## 📋 Prerequisites

- ✅ Google Account with Google Drive access
- ✅ Google Sheet for storing data
- ✅ Access to Google Apps Script
- ✅ Web browser (Chrome, Firefox, Safari, Edge)

## 🏗️ Architecture

```
GitHub Repository (Frontend)
    ↓
    HTML files (index.html, adminReport.html)
    ↓
User Opens URL → Web App loads frontend → Calls Google Apps Script
    ↓
Google Sheet (Backend & Database)
    ↓
    Code.gs (Apps Script)
    ↓
Google Sheets (Data Storage)
```

## 📝 Step 1: Prepare Your Google Sheet

### 1.1 Create Master Data Sheets

For each location, create a sheet named `MASTER-[LOCATION]`:

```
MASTER-NETEDC-CAFETERIA
MASTER-KETEDC-CAFETERIA
MASTER-KETEDC-ECOSHOP
MASTER-NETEDC-ECOSHOP
MASTER-PETEDC-ECOSHOP
MASTER-CHATHEN-ECOSHOP
MASTER-CAFETERIA-PTP
```

### 1.2 Add Headers to Each Master Sheet

In each master sheet's first row, add:

```
| Date | Total Collection | Online Collection | Remittance to Bank |
|------|------------------|-------------------|--------------------|
```

**Format the columns:**
- Column A (Date): Format as Date
- Columns B, C, D: Format as Currency/Number with 2 decimal places

### 1.3 Create USER_CREDENTIALS Sheet

Create a new sheet named `USER_CREDENTIALS` with headers:

```
| Username | HashedPassword | LocationName |
|----------|----------------|---------------|
```

**Add sample users:** (You'll hash passwords in Apps Script)

```
| user1    | (leave empty - will be hashed) | NETEDC-CAFETERIA |
| admin    | (leave empty - will be hashed) | ADMIN_REPORT     |
```

## 🔧 Step 2: Add Backend Code to Google Sheet

### 2.1 Open Google Apps Script

1. Open your Google Sheet
2. Go to **Extensions → Apps Script**
3. You'll see a new tab open with the Apps Script editor

### 2.2 Copy Backend Code

1. Go to [Code.gs](Code.gs) in this repository
2. Copy **ALL** the code
3. In Apps Script editor, replace the default code with the copied code
4. Click **Save** (Ctrl+S or Cmd+S)

### 2.3 Create appsscript.json

1. In Apps Script editor, click **⚙️ Project Settings**
2. Note the **Script ID**
3. Click **Editor** and at the top, click **+ Create New File → appsscript.json** (if not exists)
4. Paste the appsscript.json content from the repository
5. Save

## 👤 Step 3: Create User Accounts

### 3.1 Generate Password Hashes

1. In Apps Script editor, go to **Execution log** area
2. Copy this code in a new Script file and run it:

```javascript
function generatePasswordHashes() {
  const passwords = {
    'user1': 'password123',  // Change to your password
    'admin': 'admin123'      // Change to your admin password
  };
  
  Object.keys(passwords).forEach(username => {
    const password = passwords[username];
    const hashedPassword = Utilities.computeDigest(
      Utilities.DigestAlgorithm.SHA_256,
      password,
      Utilities.Charset.UTF_8
    ).map(byte => (byte < 0 ? byte + 256 : byte).toString(16).padStart(2, '0')).join('');
    
    Logger.log(`${username}: ${hashedPassword}`);
  });
}
```

3. Click **Run** button
4. Check **Execution log** for the hashed passwords
5. Copy the hashes

### 3.2 Add Users to USER_CREDENTIALS Sheet

1. Open your Google Sheet
2. Go to **USER_CREDENTIALS** sheet
3. Add rows:

```
| user1 | [hashed_password_for_user1] | NETEDC-CAFETERIA |
| admin | [hashed_password_for_admin]  | ADMIN_REPORT     |
```

Repeat for each user and location.

## 🚀 Step 4: Deploy as Web App

### 4.1 Deploy the Script

1. In Apps Script editor, click **Deploy** → **New Deployment**
2. Click **Select type** and choose **Web app**
3. Fill in:
   - **Execute as:** Your email/account
   - **Who has access:** "Anyone" (or restrict as needed)
4. Click **Deploy**
5. Click **Copy deployment URL**
6. Save this URL - you'll share it with users

### 4.2 Your Deployment URLs

```
# User Data Entry Form
https://script.google.com/macros/d/[SCRIPT_ID]/userweb?app=user

# Admin Report Dashboard
https://script.google.com/macros/d/[SCRIPT_ID]/userweb?app=admin
```

## 🧪 Step 5: Test the System

### 5.1 Test User Login

1. Open the user URL in a new browser tab
2. Login with your test user credentials (e.g., user1/password123)
3. Try submitting sample data
4. Verify data appears in the Google Sheet

### 5.2 Test Admin Login

1. Open the admin URL
2. Login with admin credentials (e.g., admin/admin123)
3. Generate a report
4. Verify it shows data from all locations
5. Test CSV and PDF download

## 📱 Step 6: Share with Users

### Share User Form

Share this URL with regular users:
```
https://script.google.com/macros/d/[SCRIPT_ID]/userweb?app=user
```

Provide them:
- Their username
- Their password
- Instructions in [USER_GUIDE.md](USER_GUIDE.md)

### Share Admin Form

Share admin URL only with admins:
```
https://script.google.com/macros/d/[SCRIPT_ID]/userweb?app=admin
```

## ⚙️ Step 7: Initial Configuration

### Update Locations (if needed)

If you want to add/remove locations:

1. Edit **Code.gs**
2. Find `PROJECTS_CONFIG` object
3. Add or remove locations:

```javascript
const PROJECTS_CONFIG = {
  "NEW-LOCATION": {
    masterSheet: "MASTER-NEW-LOCATION"
  },
  // ... other locations
};
```

4. Create corresponding master sheets in Google Sheet
5. Save and redeploy

## 📊 Step 8: Data Management

### Backup Your Data

1. Regularly download your Google Sheet as Excel/CSV
2. Store backups securely

### Add More Users

1. Generate password hash (follow Step 3.1)
2. Add row to USER_CREDENTIALS sheet
3. Share login URL with user

### Generate Historical Reports

1. Use Admin URL
2. Select date range
3. Generate and download reports

## 🔒 Security Best Practices

✅ **DO:**
- Use strong passwords for admin accounts
- Regularly review USER_CREDENTIALS sheet
- Backup your data frequently
- Use specific sharing with Google Sheet
- Monitor Apps Script execution logs

❌ **DON'T:**
- Share admin credentials widely
- Store passwords in plain text
- Leave sensitive data in browser history
- Share deployment URLs publicly

## 🐛 Troubleshooting

### "Sheet not found" error

**Solution:** Verify all master sheets exist with exact names:
- MASTER-NETEDC-CAFETERIA
- MASTER-KETEDC-CAFETERIA
- etc.

### "Login failed" message

**Solution:**
1. Check USERNAME and HASHEDPASSWORD in USER_CREDENTIALS sheet
2. Verify password hash is correct
3. Ensure USER_CREDENTIALS sheet exists
4. Check Apps Script logs for errors

### Data not saving

**Solution:**
1. Check master sheet headers are correct
2. Verify user location matches a sheet name
3. Check date is not in the future
4. Review Apps Script execution logs

### PDF/CSV download fails

**Solution:**
1. Ensure there is data in the selected date range
2. Try smaller date ranges first
3. Check browser console (F12) for errors
4. Check Apps Script logs

## 📞 Support

For issues:
1. Check [TROUBLESHOOTING.md](TROUBLESHOOTING.md)
2. Review Apps Script logs (Extensions → Apps Script → Execution)
3. Check browser console (F12 → Console tab)

## ✅ Deployment Checklist

- [ ] Google Sheet created with all master sheets
- [ ] USER_CREDENTIALS sheet created with headers
- [ ] Code.gs copied and saved
- [ ] appsscript.json configured
- [ ] User accounts created with hashed passwords
- [ ] Web app deployed successfully
- [ ] Deployment URLs saved
- [ ] User URL tested and working
- [ ] Admin URL tested and working
- [ ] Users notified with their credentials
- [ ] Backup of Google Sheet created

---

**You're all set!** 🎉 Your Income Data Entry System is now live.
