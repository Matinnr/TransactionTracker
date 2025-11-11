# Personal Finance Dashboard - Design Guidelines

## Design Approach

**Selected Approach:** Design System + Financial Dashboard Reference

**Justification:** This is a utility-focused, information-dense application where clarity, trust, and efficiency are paramount. I used Material Design principles combined with inspiration from leading fintech dashboards (Mint, YNAB, Stripe Dashboard) to create a professional, data-focused experience.

**Core Principles:**
- Data clarity above all else
- Professional, trustworthy aesthetic
- Scannable information hierarchy
- Minimal cognitive load for financial decisions

## Typography

**Font Families:**
- Primary: Inter (via Google Fonts) - headings, UI elements, data labels
- Monospace: JetBrains Mono - monetary values, transaction amounts

**Hierarchy:**
- Page Titles: text-3xl font-bold (dashboard sections)
- Section Headers: text-xl font-semibold
- Card Titles: text-lg font-medium
- Body Text: text-base font-normal
- Data Labels: text-sm font-medium
- Monetary Values: text-lg font-mono font-semibold (or text-2xl for key metrics)
- Helper Text: text-xs

## Layout System

**Spacing Primitives:** Use Tailwind units of 2, 4, 6, 8, 12 consistently
- Component padding: p-4, p-6
- Section spacing: gap-6, gap-8
- Card spacing: space-y-4
- Tight groupings: gap-2

**Grid Structure:**
- Dashboard container: max-w-7xl mx-auto px-4
- Two-column layout for desktop: grid grid-cols-1 lg:grid-cols-3 gap-6
- Sidebar: lg:col-span-1 (navigation, filters)
- Main content: lg:col-span-2
- Metric cards: grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4

## Component Library

### Dashboard Layout
**Sidebar Navigation:**
- Fixed left sidebar on desktop (w-64)
- Collapsible on mobile (hamburger menu)
- Navigation items with icon + label
- Active state with subtle highlight
- Sections: Dashboard, Transactions, Subscriptions, Budget, Upload

**Top Bar:**
- Account selector dropdown
- Date range picker
- Search transactions input (w-full max-w-md)
- User profile menu (right-aligned)

### Data Display Components

**Metric Cards:**
- Elevated cards (shadow-sm) with rounded-lg borders
- Large monetary value with context label above
- Trend indicator (icon + percentage change)
- Sparkline chart for context (optional mini-graph)
- Padding: p-6

**Charts:**
- Monthly spending area chart (primary dashboard view)
- Category breakdown pie/donut chart
- Income vs expenses bar chart comparison
- Use chart.js or recharts for clean, professional visualizations
- Chart containers: bg-white rounded-lg p-6 shadow-sm

**Transaction List:**
- Table layout with alternating row background (striped)
- Columns: Date, Merchant, Category (badge), Amount (right-aligned, monospace)
- Color coding: green for income, red for expenses
- Clickable rows with hover state
- Pagination at bottom

**Subscription Cards:**
- Grid of cards (grid-cols-1 md:grid-cols-2 gap-4)
- Each card shows: Service icon/logo, Name, Amount, Frequency
- Status badge: "Active", "Unused" (grayed out), "Payment Holiday"
- Action buttons: View details, Cancel

**Category Badges:**
- Small rounded-full pills
- Subtle background tints (not bright colors)
- text-xs font-medium
- Categories: Income, Rent, Utilities, Subscription, Food, Transport, Shopping, Other

### Forms & Inputs

**CSV Upload:**
- Drag-and-drop zone with dashed border
- File input with clear label
- Upload progress indicator
- Success/error states with appropriate messaging
- Padding: p-8, text-center

**Filters Panel:**
- Dropdown selects for category, date range
- Search input for merchant
- Amount range sliders
- "Apply Filters" and "Reset" buttons

**Date Range Picker:**
- Quick presets: This Month, Last Month, Last 3 Months, Custom
- Calendar popup for custom selection

### Interactive Elements

**Buttons:**
- Primary: filled, rounded-md, px-4 py-2
- Secondary: outlined
- Text buttons for tertiary actions
- Icon buttons for compact actions (filters, settings)

**Anomaly Highlights:**
- Transaction cards with yellow/orange left border for unusual spending
- Tooltip explaining why flagged (e.g., "150% above category average")
- Dismissible alert banner for major anomalies

**Loading States:**
- Skeleton screens for data tables and charts
- Spinner for CSV processing
- Progressive data loading (show what's ready)

## Visual Treatments

**Cards:** All data containers use rounded-lg with shadow-sm, bg-white with p-6 padding

**Borders:** Minimal use, subtle gray dividers between sections (border-gray-200)

**Elevation:** Three levels only - flat (bg-gray-50), elevated (shadow-sm), dialog (shadow-lg)

**Iconography:** Use Heroicons (outline style) via CDN for consistency - financial icons, navigation, status indicators

## Responsive Behavior

**Mobile (< 768px):**
- Single column layout
- Sidebar converts to overlay drawer
- Metric cards stack vertically
- Charts maintain aspect ratio, scroll horizontally if needed
- Transaction table converts to card list view

**Tablet (768px - 1024px):**
- Two-column metric grid
- Sidebar remains visible
- Charts at full width

**Desktop (> 1024px):**
- Full three-column layout
- Side-by-side chart comparisons
- Expanded transaction table

## Accessibility

- All monetary values include currency symbol and semantic markup
- Color is never the only indicator (use icons + text for status)
- Keyboard navigation for all interactive elements
- Focus states clearly visible (ring-2 ring-blue-500)
- ARIA labels for chart data points
- High contrast text (min 4.5:1 ratio)

## Images

**No Hero Image Required** - This is a dashboard application, not a marketing page. Launch directly into the functional interface.

**Service Logos:** Use small brand icons (24x24px) for subscription services (Netflix, Spotify, etc.) - these can be placeholder colored circles with initials if real logos unavailable.