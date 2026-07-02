# User Guide - Income Data Entry System

## 📱 Getting Started

### Before You Start

You should have received:
- ✅ The web app URL from your administrator
- ✅ Your username
- ✅ Your password
- ✅ Your assigned location name

## 🔐 Login

1. **Open the web app URL** provided by your admin
2. **Enter your username and password**
3. **Click Login**
4. You'll see a success message and be taken to the data entry form

### Troubleshooting Login

- ❌ **"Invalid username or password"** → Check spelling and ask admin to verify
- ❌ **Page not loading** → Check internet connection and refresh browser
- ❌ **"Account is for admin reports"** → Use the admin URL instead

## 📝 Entering Daily Data

### Step-by-Step

1. **Your location name appears at the top**
   - Example: "NETEDC-CAFETERIA"

2. **Fill in the form:**

   | Field | What to Enter | Example |
   |-------|--------------|----------|
   | **Date** | Today's date or past date | 15-07-2024 |
   | **Total Collection** | All money collected today | 5000.00 |
   | **Online Collection** | Digital payment amount | 2000.00 |
   | **Remittance to Bank** | Amount sent to bank | 3000.00 |

3. **The system automatically calculates:**
   - **Cash Collection** = Total Collection - Online Collection
   - In example above: 5000 - 2000 = 3000

4. **Review the data carefully**

5. **Click "Submit Data"**

6. **Confirm the submission**
   - A popup appears asking "Are you sure?"
   - Click "Confirm" to submit
   - Click "Cancel" to go back and edit

7. **See the success message** ✓
   - "Data submitted successfully!"
   - Form clears automatically
   - You can enter more data

### Rules & Validation

⚠️ **Date Rules:**
- Cannot be in the future
- Can be today or any past date
- Cannot duplicate same date twice

⚠️ **Amount Rules:**
- Must be numbers (decimals allowed)
- Cannot be negative
- Online Collection ≤ Total Collection

✅ **Example of valid entry:**
- Date: 15-07-2024
- Total: 5000.00
- Online: 2000.00
- Remittance: 3000.00

❌ **Example of invalid entry:**
- Total: 5000
- Online: 6000 ← ERROR! (Online > Total)

## 📊 View Your Reports

### Quick Report View

After submitting data, click **"View Report"** in the "My Data Report" section.

### Detailed Report Steps

1. **Select date range:**
   - **From Date:** Start of period
   - **To Date:** End of period
   - Defaults to current month

2. **Click "View Report"**

3. **See your summary:**
   - Total Collection (all money)
   - Online Collection (digital)
   - Cash Collection (physical money)
   - Remittance to Bank (sent to bank)

4. **See daily breakdown:**
   - Scroll down to see "Daily Details" table
   - Shows each day's data
   - Dates in DD-MM-YYYY format

### Understanding Your Report

```
Summary Cards (top):
┌─────────────────┐  ┌─────────────────┐
│ Total Collection│  │  Online Payment │
│   ₹ 50,000.00   │  │   ₹ 15,000.00   │
└─────────────────┘  └─────────────────┘
┌─────────────────┐  ┌─────────────────┐
│  Cash Payment   │  │  Bank Remittance│
│   ₹ 35,000.00   │  │   ₹ 25,000.00   │
└─────────────────┘  └─────────────────┘

Daily Details (below):
┌────────────┬─────────┬────────┬──────┐
│    Date    │  Total  │ Online │ Cash │
├────────────┼─────────┼────────┼──────┤
│ 01-07-2024 │ 2000.00 │ 500.00 │ 1500 │
│ 02-07-2024 │ 2500.00 │ 800.00 │ 1700 │
│ 03-07-2024 │ 1500.00 │ 200.00 │ 1300 │
└────────────┴─────────┴────────┴──────┘
```

## 📱 Mobile Use

### Optimized for Phones

✅ All forms work great on mobile  
✅ Buttons sized for thumb taps  
✅ Proper keyboards for number input  
✅ Tables scroll horizontally if needed  
✅ Works offline with poor connectivity  

### Tips for Mobile Users

1. **Use landscape mode** for better visibility
2. **Tap directly on date field** to open date picker
3. **Swipe left/right** to scroll tables
4. **Numbers appear right-aligned** for easy reading
5. **Keep screen on** while entering data to avoid timeout

## 🔄 Common Tasks

### Edit Previous Entry

❌ **Cannot edit directly**

✅ **Solution:** Contact your administrator to:
1. Delete the incorrect entry from Google Sheet
2. You can then re-enter the correct data

### Submit Data for Previous Day

1. **Open the app**
2. **Click the Date field**
3. **Select the previous date**
4. **Fill in amounts**
5. **Submit as normal**

### Check Last Month's Report

1. **In "My Data Report" section**
2. **Click "From Date" field**
3. **Select first day of last month**
4. **Click "To Date" field**
5. **Select last day of last month**
6. **Click "View Report"**

### Compare Different Periods

1. **View one report** and note the totals
2. **Click "View Report" again** with different dates
3. **Compare the numbers**

## 💡 Tips & Best Practices

✅ **DO:**
- Enter data daily for accuracy
- Double-check amounts before submitting
- Review monthly report
- Keep your password safe
- Report login issues to admin

❌ **DON'T:**
- Share your login credentials
- Leave the app running unattended
- Clear browser cache if you want to stay logged in
- Try to edit past entries
- Use negative numbers

## 🐛 Troubleshooting

### "Date cannot be in the future"

**Problem:** You're trying to enter a future date  
**Solution:** Select today or a past date

### "Online Collection cannot exceed Total Collection"

**Problem:** Online amount is higher than total  
**Solution:** Check the numbers:
- Online should be ≤ Total
- Example: If Total is 5000, Online max is 5000

### "Data for this date already exists"

**Problem:** You already entered data for that date  
**Solution:**
1. Choose a different date
2. Contact admin if you need to change the entry

### "No data found for this period"

**Problem:** No entries in the date range  
**Solution:**
1. Check if you entered data for those dates
2. Expand the date range to include more days
3. Try a different period

### Form not submitting

**Problem:** Submit button doesn't work  
**Solution:**
1. Check internet connection
2. Refresh the page (F5)
3. Try again
4. Contact admin if problem persists

## 📞 Getting Help

**For questions about:**
- 👤 Login issues → Contact your administrator
- 💰 Amount validation → Review rules in "Rules & Validation" section above
- 📊 Report interpretation → Check "Understanding Your Report" section
- 🔧 Technical problems → Contact your administrator with screenshot

## ✨ Features Available to You

✅ Enter daily collection data  
✅ View your personal reports  
✅ See daily breakdown by date  
✅ View summary totals  
✅ Submit multiple times per day (different dates)  
✅ Access from phone, tablet, or computer  
✅ Logout when done  

❌ Cannot (admin only):
- See other locations' data
- Edit or delete entries
- Export reports as PDF/CSV
- View consolidated reports

---

**Ready to get started?** 🚀 Open your web app URL and login!
