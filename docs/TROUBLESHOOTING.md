# Troubleshooting Guide

## 🔧 Common Issues & Solutions

### Login Problems

#### ❌ "Invalid username or password"

**Possible Causes:**
1. Typo in username or password
2. Password not hashed correctly
3. User account doesn't exist
4. Wrong credentials for your role

**Solutions:**
1. Double-check spelling (case-sensitive)
2. Ask admin to verify your credentials
3. Verify user exists in USER_CREDENTIALS sheet
4. For admin access, verify your account has `ADMIN_REPORT` as LocationName

---

#### ❌ "This account is for admin reports"

**Problem:** You're trying to login as admin user to the regular form

**Solution:**
- Use the **admin URL** (with `?app=admin`)
- Or use different credentials with a location name

---

#### ❌ Page loading blank or showing errors

**Problem:** Frontend files not loading

**Solutions:**
1. **Check URL**
   - Ensure it's the correct deployment URL
   - Should be: `https://script.google.com/macros/d/[ID]/userweb?app=user` or `?app=admin`

2. **Check Internet**
   - Verify you have internet connection
   - Try refreshing the page (Ctrl+F5 or Cmd+Shift+R)

3. **Clear Cache**
   - Ctrl+Shift+Delete (Chrome)
   - Cmd+Shift+Delete (Firefox)
   - Settings → Privacy → Clear history (Safari)

4. **Try Different Browser**
   - Chrome, Firefox, Safari, Edge all supported
   - Some browsers cache more aggressively

---

### Data Entry Issues

#### ❌ "Data for this date already exists"

**Problem:** You entered data for the same date twice

**Solutions:**
1. **Use a different date**
   - Submit data for a different day
   - System doesn't allow duplicate dates per location

2. **Edit existing entry** (admin only)
   - Contact admin to modify the Google Sheet directly
   - Once deleted, you can re-enter correct data

---

#### ❌ "Online Collection cannot exceed Total Collection"

**Problem:** Online amount is larger than total

**Example:**
- Total: 5000
- Online: 6000 ← ERROR!

**Solution:**
- Online must be ≤ Total
- Check your calculation
- Example: 5000 total with 4000 online is OK

---

#### ❌ "Date cannot be in the future"

**Problem:** You entered tomorrow's date or a future date

**Solution:**
- Select today or a past date only
- Cannot submit data for dates not yet arrived

---

#### ❌ Amounts showing as NaN or invalid

**Problem:** Invalid number format entered

**Solutions:**
1. **Use only numbers** (0-9 and decimal point)
   - ❌ "5000.00 rupees" → ✅ "5000.00"
   - ❌ "5,000" → ✅ "5000"

2. **Allow decimals**
   - ✅ "1500.75" is OK
   - ✅ "1500" is OK
   - ❌ "1500.7.5" is NOT OK

3. **No negative numbers**
   - ❌ "-1000" → ✅ "0" (or leave as 0)

---

### Submission Problems

#### ❌ "Submit button doesn't work" or appears stuck

**Problem:** Form not submitting, button stays loading

**Solutions:**
1. **Check internet connection**
   - Make sure you're online
   - Try on WiFi instead of mobile data

2. **Verify form is complete**
   - All fields must be filled (marked with *)
   - All fields must be valid

3. **Wait for confirmation dialog**
   - Don't click multiple times
   - Wait 3-5 seconds for popup

4. **Try again**
   - Refresh page (Ctrl+F5)
   - Fill form again
   - Submit once

5. **Check Apps Script logs** (admin)
   - Go to Apps Script editor
   - Click "Execution" menu
   - Look for errors

---

#### ❌ "Submission cancelled" but you didn't cancel

**Problem:** Accidental cancel click on confirmation dialog

**Solution:**
- Fill the form again
- Click Submit
- Click **Confirm** (not Cancel)
- The green button is Confirm

---

### Report Issues

#### ❌ "No data found for this period"

**Problem:** Report shows no data even though you entered data

**Possible Causes:**
1. Date range doesn't include your data
2. Data is in a different location
3. Data hasn't synced yet

**Solutions:**
1. **Verify date range**
   - From Date: First day of period
   - To Date: Last day of period
   - Make sure dates include when you entered data

2. **Check location**
   - Verify you're logged in as correct location
   - Your location shows at top of form

3. **Wait a moment**
   - Data syncs within seconds
   - If very slow internet, wait 10 seconds
   - Then refresh report

4. **Verify data was saved**
   - Check if you saw "Data submitted successfully!" message
   - If no message, submission failed

---

#### ❌ Tables not showing data correctly

**Problem:** Report shows but amounts look wrong

**Solutions:**
1. **Check currency format**
   - All amounts in Indian Rupees (₹)
   - Formatted with 2 decimal places
   - Thousands have commas: 10,000.00

2. **Verify your math**
   - Cash = Total - Online (verify this)
   - All values should be positive

3. **Scroll horizontally on mobile**
   - If table is cut off, swipe left/right
   - All columns are there, just need scrolling

---

#### ❌ PDF or CSV download fails

**Problem:** Download button doesn't work

**Solutions:**
1. **Check date range**
   - Must have data in selected period
   - Download fails if no data

2. **Try CSV first**
   - CSV usually simpler, try before PDF
   - Both require data to exist

3. **Check downloads folder**
   - File may have downloaded
   - Check your Downloads folder

4. **Try smaller date range**
   - Large datasets sometimes timeout
   - Try shorter period first

5. **Disable pop-up blocker**
   - Some browsers block file downloads
   - Check browser settings
   - Allow downloads from this site

---

### Mobile-Specific Issues

#### ❌ Date picker not opening on mobile

**Problem:** Clicking date field doesn't open calendar

**Solutions:**
1. **Try clicking directly on field**
   - Not on label, on the input box
   - Should open system date picker

2. **Check browser**
   - Chrome, Safari, Firefox all support this
   - Older browsers might not

3. **Try typing date manually**
   - Format: YYYY-MM-DD (2024-07-15)
   - Even if picker doesn't work

---

#### ❌ Keyboard covering form on mobile

**Problem:** When typing, keyboard hides submit button

**Solutions:**
1. **Scroll after clicking field**
   - Form auto-scrolls usually
   - If not, manually scroll up

2. **Use landscape mode**
   - Rotate phone for wider view
   - Less chance of keyboard covering content

3. **Fill fields from top**
   - Fill date first
   - Keyboard will hide less

---

#### ❌ Form elements too small to tap

**Problem:** Buttons and inputs hard to click on mobile

**Solutions:**
1. **Update app** (if available)
   - Buttons are 44x44px minimum
   - Already large enough

2. **Rotate to landscape**
   - Bigger view of form
   - Easier to tap buttons

3. **Zoom in** (if allowed)
   - Double-tap to zoom
   - Some pages disable zoom
   - Try pinch to zoom

---

### Google Sheet Issues

#### ❌ "Master sheet not found" error

**Problem:** App can't find data sheets

**Admin Solutions:**
1. **Verify sheet names** (exact spelling required)
   - MASTER-NETEDC-CAFETERIA
   - MASTER-KETEDC-CAFETERIA
   - etc.
   - Names are case-sensitive

2. **Check headers**
   - Each master sheet needs:
     - Date
     - Total Collection  
     - Online Collection
     - Remittance to Bank

3. **Verify CODE.GS references**
   - Check PROJECTS_CONFIG matches sheet names
   - Edit if location names changed

---

#### ❌ "USER_CREDENTIALS sheet not found"

**Admin Solutions:**
1. **Create the sheet**
   - Sheet name: `USER_CREDENTIALS`
   - Headers: Username, HashedPassword, LocationName

2. **Verify spelling**
   - Must be exactly: USER_CREDENTIALS
   - Case-sensitive
   - No spaces before/after

---

#### ❌ "Missing required headers in master sheet"

**Problem:** Headers don't match expected names

**Admin Solutions:**
1. **Check header spelling**
   - "Total Collection" (not "Total")
   - "Online Collection" (not "Online")
   - "Remittance to Bank" (not "Remittance")

2. **Exact spelling required**
   - Spaces matter
   - Capitalization matters

3. **Fix headers**
   - Delete wrong headers
   - Add correct ones
   - Redeploy apps script

---

## 🔍 How to Debug

### For Users

**Check Browser Console:**
1. Press F12 (or Cmd+Option+I on Mac)
2. Click "Console" tab
3. Look for red errors
4. Screenshot and send to admin

**Check Network Status:**
1. Open browser DevTools (F12)
2. Go to "Network" tab
3. Try to login or submit
4. Look for failed requests (red X)

---

### For Admins

**Check Apps Script Logs:**
1. Open Google Sheet
2. Go to Extensions → Apps Script
3. Click on the project
4. Click "Execution" or "View Logs"
5. Look for errors with timestamps

**Check Sheet Data:**
1. Open each MASTER sheet
2. Verify headers are correct
3. Look for data entries
4. Check data format (dates, numbers)

---

## 📞 When to Contact Admin

**Users should contact admin for:**
- ❌ "Invalid username or password" repeated
- ❌ "This account is for admin reports"
- ❌ Need to change/edit past entries
- ❌ Need to add new locations
- ❌ Need account reset

**Admins should contact Google Support for:**
- Google Sheets errors
- Google Apps Script errors
- Quota exceeded errors
- Permission issues

---

## ✅ Quick Fix Checklist

- [ ] Refresh page (Ctrl+F5)
- [ ] Check internet connection
- [ ] Check spelling of username/password
- [ ] Verify correct URL (admin or user)
- [ ] Clear browser cache
- [ ] Try different browser
- [ ] Wait 10 seconds and retry
- [ ] Check date range in reports
- [ ] Verify data exists in Google Sheet
- [ ] Contact admin if still failing

---

**Still stuck?** Contact your administrator with:
- Screenshot of error
- URL you're using
- What you were trying to do
- Browser and device info
- Time of issue
