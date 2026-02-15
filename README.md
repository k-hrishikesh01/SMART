# 📱 AMS QR — Smart Attendance Management System

A QR-based attendance management system for VTU colleges featuring **real GPS geofencing**, **cross-device sync**, and **Google Sheets** as the backend.

![Status](https://img.shields.io/badge/status-active-brightgreen) ![Stack](https://img.shields.io/badge/stack-React%20%2B%20Google%20Sheets-blue)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔐 **Real Authentication** | Login with USN/Email + password (stored in Google Sheets) |
| 📷 **QR Code Scanning** | Faculty generates QR, students scan to mark attendance |
| 🔄 **Token Rotation** | QR codes rotate every 30 seconds for anti-proxy security |
| 📍 **GPS Geofencing** | Real GPS verification using Haversine formula (100m radius) |
| 🚫 **Duplicate Prevention** | Server-side check prevents double marking |
| 📊 **Live Dashboard** | Real-time attendance logs, subject-wise stats, low-attendance alerts |
| 🌐 **Cross-Device Sync** | Faculty laptop + student phones share data via Google Sheets API |
| 🎯 **Demo Mode** | Works offline with mock data — no API setup needed |

---

## 🚀 Quick Start

### 1. Clone & Install

```bash
git clone https://github.com/BHUVI2192/SMART.git
cd SMART
npm install
```

### 2. Configure API URL

Create a file named `.env.local` in the project root:

```
VITE_APPS_SCRIPT_URL=https://script.google.com/macros/s/AKfycbxrrd-4TdVB9yCrP9_oOyopGqSyeWrgxCa2XXNKiy5w3oTOhaSzfR1vNjcdt-PN0R_F/exec
```

> 💡 **Skip this step** if you just want to explore the UI — the app will run in **Demo Mode** with mock data.

### 3. Run

```bash
npm run dev
```

Open **http://localhost:3000** in your browser.

---

## 🔑 Login Credentials

| Role | User ID | Password |
|------|---------|----------|
| 👨‍💼 Admin | `admin@vtu.ac.in` | `admin123` |
| 👩‍🏫 Faculty | `harshitha@vtu.ac.in` | `faculty123` |
| 🎓 Student | `4PM21CS001` | `student123` |

---

## 🏗 Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 19, TypeScript, Vite, TailwindCSS |
| **Backend** | Google Apps Script (REST API) |
| **Database** | Google Sheets |
| **Libraries** | `qrcode`, `jsqr`, `lucide-react`, `react-router-dom` |

---

## 📂 Project Structure

```
├── App.tsx                    # Main app with routing
├── data.ts                    # Mock data for demo mode
├── types.ts                   # TypeScript interfaces
├── components/
│   └── Layout.tsx             # Sidebar + header layout
├── pages/
│   ├── Login.tsx              # Dual-mode login (API + Demo)
│   ├── admin/
│   │   ├── AdminDashboard.tsx # KPI cards, alerts, charts
│   │   ├── AdminStudents.tsx  # Student records table
│   │   └── AdminTimetable.tsx # Day-based timetable view
│   ├── faculty/
│   │   ├── FacultyDashboard.tsx # Today's schedule
│   │   ├── SessionView.tsx      # QR generation + live logs
│   │   └── FacultyRecords.tsx   # Session history
│   └── student/
│       ├── StudentDashboard.tsx # Stats + active class
│       ├── ScanPage.tsx         # QR scan + GPS verification
│       └── StudentHistory.tsx   # Attendance history
├── services/
│   ├── api.ts                 # Central API client
│   ├── auth.ts                # Login/logout + session
│   ├── sessions.ts            # Session CRUD + token rotation
│   ├── attendance.ts          # Mark attendance + stats
│   └── geolocation.ts         # GPS + Haversine distance
└── google-apps-script/
    └── Code.gs                # Google Apps Script backend
```

---

## 🔧 Backend Setup (For Developers)

If you want to set up your own backend:

1. Create a new **Google Sheet**
2. Go to **Extensions → Apps Script**
3. Paste the contents of `google-apps-script/Code.gs`
4. Replace `YOUR_GOOGLE_SHEET_ID_HERE` with your Sheet ID
5. **Deploy → New Deployment → Web App** (access: Anyone)
6. Copy the URL into `.env.local`
7. Seed data: visit `YOUR_URL?action=seedData` in your browser

---

## 👥 Team

Built for VTU college demo — [BHUVI2192](https://github.com/BHUVI2192)

---

## 📄 License

MIT

## 🔐 Security Architecture

A detailed security architecture, threat model, and integrity analysis of the system is documented in:

docs/SECURITY_ANALYSIS.md

This includes:
- Token lifecycle analysis
- API vs Offline mode security comparison
- GPS validation model
- Duplicate prevention mechanisms
- Attack surface assessment
- Residual risk evaluation
