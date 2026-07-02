# 📱 Income Data Entry System

A mobile-first web application for managing daily income data entry across multiple outlets. Built with **HTML/CSS/JavaScript** (frontend in GitHub) and **Google Apps Script** (backend in Google Sheets).

## 🎯 Features

- ✅ **Mobile-First Design** - 100% responsive for phones, tablets, and desktops
- ✅ **User Authentication** - Secure login system with SHA-256 password hashing
- ✅ **Daily Data Entry** - Simple form to submit collection data
- ✅ **Personal Reports** - View aggregated data for your location
- ✅ **Admin Dashboard** - Consolidated reports from all locations
- ✅ **PDF & CSV Export** - Download reports in multiple formats
- ✅ **No External Database** - All data stored in Google Sheets
- ✅ **Offline-Ready** - Works even with poor connectivity

## 📋 Quick Start

### For Users

1. **Get the Web App URL** from your administrator
2. **Open in browser** (mobile or desktop)
3. **Login** with your credentials
4. **Enter daily data** - Date, Total Collection, Online Collection, Remittance
5. **View reports** - See your monthly data breakdown

### For Administrators

See [Admin Setup Guide](docs/SETUP_ADMIN.md) for complete deployment instructions.

## 🏗️ Architecture

### Frontend (GitHub - This Repository)
```
Frontend Files:
├── src/
│   ├── index.html          # User data entry form & reports
│   ├── adminReport.html    # Admin consolidated dashboard
│   └── styles/             # CSS styling files (optional)
├── docs/                   # Documentation
└── README.md              # This file
```

### Backend (Google Apps Script - In Google Sheets)
```
Backend:
├── Code.gs                 # All backend logic
├── appsscript.json         # Configuration manifest
└── Google Sheet Database   # Data storage
```

## 📱 Frontend Components

### `index.html` - User Portal
- **Login Form** - Username & password authentication
- **Data Entry Form** - Daily collection submission
- **My Report** - Personal aggregated data & daily breakdown
- **Responsive Design** - Perfect on mobile, tablet, desktop

### `adminReport.html` - Admin Dashboard  
- **Admin Login** - Separate admin authentication
- **Date Range Selection** - Generate reports for any period
- **Consolidated View** - All locations' data in one place
- **Tabs by Location** - Switch between different outlets
- **Export Options** - Download as PDF or CSV
- **Summary Cards** - Overall totals and analytics

## 🔧 How It Works

### Data Flow
```
User Input (Frontend HTML)
    ↓
Google Apps Script (Backend Code.gs)
    ↓
Google Sheets (Database)
    ↓
Query & Process (Code.gs)
    ↓
Display Reports (Frontend HTML)
```

### User Roles

| Role | Can Do | Location |
|------|--------|----------|
| **Regular User** | Enter data, view own reports | Assigned location |
| **Admin User** | View all locations, export reports | Global access |

### Supported Locations

- NETEDC-CAFETERIA
- KETEDC-CAFETERIA
- KETEDC-ECOSHOP
- NETEDC-ECOSHOP
- PETEDC-ECOSHOP
- CHATHEN-ECOSHOP
- CAFETERIA-PTP

## 📊 Data Structure

The system collects and manages:

```
Daily Entry:
├── Date
├── Total Collection      (amount collected)
├── Online Collection     (digital payments)
├── Remittance to Bank    (bank deposit)
└── Cash Collection       (calculated: Total - Online)
```

## 🚀 Deployment Steps

### Step 1: Clone Frontend Files

```bash
git clone https://github.com/avinanair/income-data-entry.git
cd income-data-entry
```

### Step 2: Setup Backend in Google Sheets

1. Open your Google Sheet
2. Go to **Extensions → Apps Script**
3. Copy code from [docs/Code.gs](docs/Code.gs)
4. Deploy as Web App

See [Complete Setup Guide](docs/SETUP_ADMIN.md)

## 📁 File Structure

```
income-data-entry/
├── README.md                    # Project overview
├── .gitignore                   # Git ignore rules
│
├── src/
│   ├── index.html              # User form (mobile-optimized)
│   └── adminReport.html        # Admin dashboard (mobile-optimized)
│
├── docs/
│   ├── SETUP_ADMIN.md          # Admin deployment guide
│   ├── USER_GUIDE.md           # User instructions
│   ├── MOBILE_FEATURES.md      # Mobile optimization details
│   ├── TROUBLESHOOTING.md      # Common issues & solutions
│   └── Code.gs                 # Backend code reference
│
└── images/
    ├── login-screenshot.png    # UI examples
    ├── data-entry.png
    └── admin-dashboard.png
```

## 💻 System Requirements

- Google Account
- Google Sheet (as database)
- Web browser (Chrome, Safari, Firefox, Edge)
- Internet connection

## 📱 Mobile Features

✅ Responsive layout adapts to all screen sizes  
✅ Touch-friendly buttons (44×44px minimum)  
✅ Proper mobile keyboards (number, date, email)  
✅ Safe area support (notches, home indicators)  
✅ Horizontal scroll for tables  
✅ Smooth animations and transitions  
✅ Fast loading and offline capability  

## 🔒 Security

- Passwords hashed with **SHA-256**
- Authentication required for all access
- Role-based access control (User vs Admin)
- No sensitive data in client-side code
- Google Sheets native security and sharing

## 🆘 Troubleshooting

### Login Issues
- Verify username/password in USER_CREDENTIALS sheet
- Check if account is created
- Try clearing browser cache

### Data Not Saving
- Check internet connection
- Verify master sheet exists
- Ensure date is not in future
- Check Apps Script logs for errors

### Reports Show No Data
- Verify date range is correct
- Check data exists in Google Sheet
- Ensure location name matches exactly

See [TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) for more solutions.

## 📞 Support & Documentation

- [Setup Guide for Admin](docs/SETUP_ADMIN.md)
- [User Guide](docs/USER_GUIDE.md)
- [Mobile Features](docs/MOBILE_FEATURES.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)

## 📝 License

This project is for internal use. Modify and distribute as needed for your organization.

## 👥 Team

Created for Division Office Income Tracking System

---

**Repository:** Frontend files only  
**Backend:** Google Apps Script (in Google Sheets)  
**Last Updated:** 2024  
**Version:** 1.0
