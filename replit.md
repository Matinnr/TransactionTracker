# Personal Finance Dashboard

## Overview

This is a **personal finance dashboard** application that helps users track their spending, manage subscriptions, and gain insights into their financial habits. The application allows users to upload CSV transaction data, automatically analyzes spending patterns, detects recurring subscriptions, and provides intelligent alerts about unusual spending or cashflow warnings.

**Key Features:**
- CSV transaction import with automatic parsing
- Intelligent financial analysis using Python-based ML algorithms
- Subscription detection and tracking (active, unused, payment holidays)
- Salary inference from transaction patterns
- Monthly surplus calculations and trend analysis
- Cashflow projections with warning system
- Budget tracking with category breakdowns
- Interactive charts and visualizations
- Dark/light theme support

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework:** React with TypeScript
- **Routing:** Wouter (lightweight client-side routing)
- **State Management:** TanStack Query (React Query) for server state management
- **UI Library:** shadcn/ui components built on Radix UI primitives
- **Styling:** Tailwind CSS with custom design system
- **Build Tool:** Vite for fast development and optimized production builds

**Design System:**
- Material Design-inspired approach focused on data clarity and trust
- Typography: Inter for UI elements, JetBrains Mono for monetary values
- Custom color system with HSL-based theming supporting light/dark modes
- Consistent spacing using Tailwind's 4/6/8 unit system
- Chart colors defined as CSS variables for consistent data visualization

**Key Frontend Patterns:**
- Component-based architecture with reusable UI primitives
- Custom hooks for mobile detection and toast notifications
- Path aliases (@/ for client, @shared/ for shared types)
- Responsive layouts using CSS Grid and Flexbox

### Backend Architecture

**Framework:** Express.js with TypeScript (ESM modules)
- **API Pattern:** RESTful endpoints under `/api` prefix
- **File Upload:** Multer for CSV file handling (in-memory storage)
- **Session Management:** Express sessions with PostgreSQL store (connect-pg-simple)
- **Development:** Hot module replacement via Vite middleware in dev mode
- **Production:** Compiled bundle with esbuild

**Storage Layer:**
- **In Development:** In-memory storage implementation (MemStorage class)
- **Production Ready:** PostgreSQL via Neon serverless database
- **ORM:** Drizzle ORM with type-safe schema definitions
- **Migration Strategy:** Schema-first with drizzle-kit

**Data Processing:**
- Python microservices for financial analysis
- Child process spawning to run Python scripts from Node.js
- JSON-based communication between Node and Python processes
- Analysis modules: salary inference, subscription detection, surplus calculation, cashflow projection

**API Endpoints:**
- `GET /api/transactions` - Fetch all transactions
- `POST /api/transactions/upload` - Upload and parse CSV file
- `GET /api/insights` - Run Python analysis on transaction data

### Database Schema

**Tables:**

1. **users**
   - id (UUID primary key)
   - username (unique text)
   - password (text)
   
2. **transactions**
   - id (UUID primary key)
   - date (timestamp)
   - description (text)
   - merchant (text)
   - amount (real/float)
   - category (text)
   - accountId (integer, default 1)

**Schema Management:**
- Drizzle ORM for type-safe queries
- Zod schemas for runtime validation
- Shared TypeScript types between frontend and backend

### Python Analysis Engine

**Purpose:** Sophisticated financial analysis that would be complex in JavaScript

**Modules:**
1. **salary_inference.py** - Detects recurring income patterns (26-33 day intervals)
2. **subscription_detector.py** - Identifies recurring charges with low variance
3. **surplus_calculator.py** - Analyzes monthly income vs expenses trends
4. **cashflow_projector.py** - Projects future balance based on historical patterns
5. **run_analysis.py** - Orchestrates all analyses and returns unified JSON response

**Integration Pattern:**
- Node.js spawns Python process with transaction CSV data via stdin
- Python processes data with pandas and numpy
- Results returned as JSON via stdout
- Error handling via stderr

**Key Algorithms:**
- Time-series analysis for detecting payment patterns
- Statistical variance checking for subscription detection
- Weekday-based spending averages for cashflow projection
- Anomaly detection for unusual transactions (>£400)

## External Dependencies

### Third-Party Services

**Database:**
- **Neon Serverless PostgreSQL** - Production database with connection pooling
- Environment variable: `DATABASE_URL`

**Development Tools:**
- **Replit-specific plugins** - Cartographer, dev banner, runtime error overlay
- Custom Python environment at `/home/runner/workspace/.pythonlibs/bin/python3`

### Key NPM Packages

**UI Framework:**
- @radix-ui/* - Accessible component primitives (25+ components)
- class-variance-authority - Type-safe component variants
- tailwindcss - Utility-first CSS framework
- recharts - Composable charting library

**Data & State:**
- @tanstack/react-query - Server state management
- drizzle-orm - TypeScript ORM
- zod - Schema validation
- date-fns - Date manipulation

**Backend:**
- express - Web framework
- multer - File upload handling
- connect-pg-simple - PostgreSQL session store

**Build & Development:**
- vite - Build tool and dev server
- tsx - TypeScript execution for Node.js
- esbuild - Production bundling

### Python Packages (Required)

- pandas - Data manipulation and analysis
- numpy - Numerical computing
- Standard library: json, sys, io, datetime

**Note:** Python dependencies must be pre-installed in the Replit environment at the specified Python path.