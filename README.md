# AI Loan Eligibility Checker — FinVision AI 🏦✨

> **AI-Powered BFSI Financial Assistance & Analytics Web Platform**

FinVision AI is a premium, modern, dark-themed BFSI (Banking, Financial Services, and Insurance) web application built to empower users with intelligent loan eligibility estimation, credit score health analysis, interactive EMI calculation with month-by-month amortization schedules, and personalized AI financial advice powered by **Claude AI**.

---

## 🌟 Key Features

1. **Loan Eligibility Checker**:
   - Calculates disposable monthly income, Debt-to-Income (DTI) ratio, and maximum borrowing capability.
   - Computes risk indicators and health summaries with status badges (`Likely Eligible`, `Potentially Eligible`, `Needs Improvement`).
   - Includes a **⚡ Try Demo Data** button for instant demonstration.

2. **Credit Score Analyzer**:
   - Categorizes score into standard bureau tiers (*Poor*, *Fair*, *Good*, *Very Good*, *Excellent*).
   - Visual SVG radial gauge meter with dynamic animation.
   - Evaluates key factors: Payment History (35%), Utilization % (30%), Credit History Age (15%), Credit Mix (10%), and Hard Inquiries (10%).

3. **EMI & Amortization Calculator**:
   - Standard mathematical EMI formula: $EMI = P \times R \times \frac{(1+R)^N}{(1+R)^N - 1}$
   - Supports tenure selection in **Months** or **Years**.
   - HTML5 Canvas donut chart visualizing Principal vs Interest breakdown.
   - Full month-by-month amortization table with Print & PDF download functionality.

4. **AI Financial Assistant (Claude AI Integration)**:
   - Proxy API endpoint querying Claude 3.5 Sonnet with financial system prompt constraints.
   - Provides tailored advice on credit score improvement, debt reduction, savings ratios, and EMI optimization.
   - Built-in intelligent offline AI fallback when API keys are not configured.

5. **Financial Dashboard**:
   - Aggregated overview displaying income, expenses, disposable margin, credit standing, and borrowing capacity.
   - Calculates a 0–100 composite Financial Health Score with an animated progress bar.

6. **Persistence & Google Sheets Integration**:
   - Secure server endpoint appending user submission metrics to Google Sheets.
   - Smart fallback automatically saving submissions to browser `localStorage`.

7. **Premium Glassmorphism UI**:
   - Dark fintech aesthetic featuring deep navy background (`#050816`), electric blue (`#00F2FE`), cyan (`#4FACFE`), and glowing purple (`#7F00FF`) accents.
   - Fully responsive across Desktop, Laptop, Tablet, and Mobile.

---

## 🏗️ Project Architecture

```
d:\janhavi\
├── index.html                # Main semantic HTML5 interface for all 8 major sections
├── server.js                 # Express server handling AI proxy, Google Sheets & static file serving
├── package.json              # App dependencies (@anthropic-ai/sdk, express, cors, dotenv, googleapis)
├── vercel.json               # Vercel serverless deployment config
├── .env.example              # Environment variables reference template
├── .gitignore                # Git ignored patterns
├── README.md                 # Complete documentation
├── css/
│   └── style.css             # Glassmorphism theme styling, responsive grid, animations, gauge & toast CSS
├── js/
│   ├── app.js                # Main initializer, navigation tab switcher, mobile drawer menu
│   ├── validation.js         # Input sanitization and rule-based form validation
│   ├── utils.js              # Indian Rupee (INR) currency formatter, toast engine, counter animations
│   ├── loan.js               # Loan math engine, DTI calculation, risk badges, demo data prefill
│   ├── credit.js             # Credit score categorizer, SVG gauge arc, factor breakdown & tips
│   ├── emi.js                # EMI formula, Canvas donut chart renderer, amortization table & print helper
│   ├── ai.js                 # Claude AI chat widget interface, quick prompt chips, typing simulation
│   ├── sheets.js             # Client bridge for Google Sheets submission & localStorage backup
│   └── dashboard.js          # Financial Health Score & metric sync controller
└── assets/
    └── favicon.svg           # Custom fintech emblem icon
```

---

## 🛠️ Technology Stack

- **Frontend**: HTML5, CSS3 (CSS Variables, Flexbox/Grid, Glassmorphism, Keyframe Animations), Vanilla JavaScript (ES6+).
- **Visualization**: HTML5 2D Canvas API & SVG Radial Gauge.
- **Backend / Proxy**: Node.js & Express.
- **AI Integration**: Anthropic Claude AI API (`@anthropic-ai/sdk`).
- **Data Persistence**: Google Sheets API (`googleapis`) & Browser `localStorage`.

---

## 🚀 Quick Start & Installation

### Prerequisites
- Node.js (v18.0.0 or higher recommended)
- npm or yarn

### 1. Clone or Open Workspace
```bash
cd d:\janhavi
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Configure Environment Variables
Copy the `.env.example` file to create a `.env` file:
```bash
cp .env.example .env
```
Open `.env` and fill in your API credentials (optional for offline demo mode):
```env
PORT=3000
CLAUDE_API_KEY=your_claude_api_key_here
GOOGLE_SHEETS_ID=your_google_sheet_id_here
GOOGLE_SERVICE_ACCOUNT_EMAIL=your_service_account@project.iam.gserviceaccount.com
GOOGLE_PRIVATE_KEY="-----BEGIN PRIVATE KEY-----\nYOUR_KEY_HERE\n-----END PRIVATE KEY-----\n"
```

### 4. Run the Development Server
```bash
npm start
```
Open your browser and navigate to:
```
http://localhost:3000
```

---

## 🔑 AI & Google Sheets Integration Setup

### Claude AI Setup
1. Sign up at [Anthropic Console](https://console.anthropic.com/).
2. Generate an API Key under Account Settings.
3. Add the key to `.env` under `CLAUDE_API_KEY`.
4. *Note*: If no API key is provided, the application seamlessly runs in **Smart Offline AI Mode** providing instant responses.

### Google Sheets Setup
1. Create a Google Cloud Project and enable the **Google Sheets API**.
2. Create a Service Account and download the JSON key.
3. Share your Google Sheet with the Service Account email address (`Editor` permissions).
4. Add `GOOGLE_SHEETS_ID`, `GOOGLE_SERVICE_ACCOUNT_EMAIL`, and `GOOGLE_PRIVATE_KEY` to `.env`.
5. *Note*: If Google credentials are not set up, submissions automatically save to browser `localStorage`.

---

## 🌐 Deploying to Vercel

The application is pre-configured with `vercel.json` for Vercel deployment:

1. Push your code to GitHub / GitLab.
2. Import the repository into your **Vercel Dashboard**.
3. Under **Environment Variables**, add:
   - `CLAUDE_API_KEY`
   - `GOOGLE_SHEETS_ID`
   - `GOOGLE_SERVICE_ACCOUNT_EMAIL`
   - `GOOGLE_PRIVATE_KEY`
4. Click **Deploy**. Vercel will build and serve the static files and serverless API endpoints.

---

## 🔒 Security & Safety Notes

- **Zero Client-Side Secrets**: All API keys and private service keys reside strictly in backend environment variables.
- **Input Sanitization**: User-entered inputs are sanitized before DOM insertion to prevent XSS vulnerabilities.
- **Educational Disclaimer**: Results and AI recommendations are explicitly labeled as non-binding educational estimates and not guaranteed bank approvals.

---

## 🔭 Future Scope & Roadmap

- **Bank API Integrations**: Open Banking API connectors for real-time account aggregations.
- **Credit Bureau Connectors**: Direct integration with CIBIL / Experian for instant credit report retrieval.
- **Loan Comparison Engine**: Side-by-side comparison of loan products across top banks.
- **Document Analysis**: AI-powered document scanner for salary slips and bank statements.
- **Multilingual Support**: Support for regional Indian languages (Hindi, Marathi, Tamil, etc.).
- **Mobile Native App**: React Native / Flutter cross-platform mobile companion.

---

## 📜 License & Acknowledgments

Created for academic research, engineering projects, and hackathon demonstrations. Developed with love by **Antigravity AI**.
