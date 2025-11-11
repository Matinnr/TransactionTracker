# Personal Finance Dashboard

A privacy-first, explainable financial insights platform that analyzes transaction data to provide actionable insights about your finances.

Features

Core Analysis
Salary Inference - Automatically detects monthly income patterns with confidence indicators

Subscription Detection - Identifies recurring payments and alerts for unused subscriptions

Cashflow Projection - 30-day spending forecast with confidence levels

Spending Analysis - Category breakdown and monthly trend visualization

Anomaly Detection - Flags unusual spending spikes

Explainable AI
Confidence Indicators - All insights include confidence levels (Low/Medium/High)

Evidence Panels - Each insight shows the reasoning and data behind it

Fuzzy Matching - Consolidates duplicate merchants (NETFLIX, NETFLIX.COM, etc.)

 Interactive Visualizations
- Income vs Spending trend charts
- Category breakdown pie charts
- Transaction history with filters

Getting Started

 Prerequisites
- Node.js 18+
- PostgreSQL database (provided by Replit)

### Installation

1. Install dependencies:
```bash
npm install
```

2. Start the development server:
```bash
npm run dev
```

3. Upload transaction data in CSV format with columns:
   - `date` (YYYY-MM-DD)
   - `merchant` (e.g., "TESCO")
   - `amount` (positive for income, negative for expenses)
   - `category` (e.g., "FOOD", "RENT", "INCOME")

### Sample Data

Two sample CSV files are provided:
- **sample_transactions.csv** - Clean dataset (10 months, high confidence results)
- **edge_case.csv** - Tests fuzzy matching and anomaly detection

## Technical Architecture

### Backend
- **Express.js** - REST API server
- **Python Analysis Engine** - Financial calculations and pattern detection
- **PostgreSQL** - Transaction storage
- **Drizzle ORM** - Type-safe database queries

### Frontend
- **React** + **TypeScript** - UI framework
- **TanStack Query** - Data fetching and caching
- **Recharts** - Interactive visualizations
- **Shadcn UI** - Component library
- **Tailwind CSS** - Styling

### Analysis Modules
- `salary_inference.py` - Income pattern detection
- `subscription_detector.py` - Recurring payment identification with fuzzy matching
- `cashflow_projector.py` - Future spending predictions
- `category_breakdown.py` - Spending categorization and trends
- `surplus_calculator.py` - Monthly surplus analysis

## Confidence System

All analyses include confidence levels based on data availability:

- **High** (6+ months): Reliable long-term patterns
- **Medium** (3-5 months): Reasonable estimates
- **Low** (<2 months): Limited data, use with caution

## Privacy & Security

- All analysis runs locally - no data sent to external services
- In-memory processing - transactions deleted when analysis completes
- No tracking or analytics
- Open source and auditable

## Contributing

This is a demonstration project. For production use, consider:
- Adding user authentication
- Implementing proper error handling
- Adding comprehensive test coverage
- Setting up CI/CD pipelines

