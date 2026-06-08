# Bethel — Rental Property Financial Dashboard

## What This Project Is

**Bethel** is a residential rental property financial dashboard for a property managed under **Noor Properties**. It tracks monthly income (rent + fees + security deposits), operating expenses, and net P&L across Dec 2025 – May 2026 — covering a tenant transition period. Deployed as a static GitHub Pages page.

---

## The Property

- **Property name:** Bethel Rental Property
- **Managed by:** Noor Properties
- **Dashboard period:** Dec 2025 – May 2026
- **As of date shown:** May 30, 2026

---

## Tenant History

| Tenant | Lease Period | Monthly Rent | Notes |
|--------|-------------|-------------|-------|
| Geethika | Dec 2025 – Apr 2026 | $750–800/mo | $250 security deposit (Dec 2025) |
| *(Vacant)* | May 2026 | — | Transition month — Geethika moved out |
| Shanik Woodson | Jun 2026+ | ~$2,200/mo (projected) | $1,100 security deposit paid May 2026, app fee $55 |

**Status chip in dashboard:** "Tenant Transition" (shown in May 2026 context)

---

## Financial Data (Dec 2025 – May 2026)

### Income by Month

| Month | Rent | Other (App Fee/Storage) | Security Deposit (Liability) | Total Cash |
|-------|------|------------------------|------------------------------|-----------|
| Dec 2025 | $800 | $55 (Geethika app fee) | $250 | $1,105 |
| Jan 2026 | $750 | $0 | $0 | $750 |
| Feb 2026 | $750 | $40 (storage room) | $0 | $790 |
| Mar 2026 | $750 | $0 | $0 | $750 |
| Apr 2026 | $750 | $0 | $0 | $750 |
| May 2026 | $0 | $55 (Shanik app fee) | $1,100 (Shanik deposit) | $1,155 |

**Operating Income = Rent + App Fees + Storage only = $3,950**
Security deposits are **liabilities** (refundable) — excluded from Net P&L.

### Expenses by Month

| Category | Dec 2025 | Jan 2026 | Feb 2026 | Mar 2026 | Apr 2026 | May 2026 |
|----------|---------|---------|---------|---------|---------|---------|
| Mortgage | $0 | $1,887.36 | $1,887.36 | $1,887.36 | $1,887.36 | $1,887.36 |
| Gas | $0 | $272.43 | $248.89 | $157.00 | $157.00 | $157.00 |
| Electricity | $0 | $97.70 | $128.58 | $62.00 | $62.00 | $62.00 |
| Internet | $40.00 | $40.00 | $40.00 | $40.00 | $40.00 | $40.00 |
| Home Setup | $1,764.71 | $0 | $529.26 | $0 | $0 | $0 |
| Maintenance | $0 | $468.03 | $0 | $0 | $0 | $0 |
| Background Check | $40.00 | $0 | $0 | $0 | $0 | $40.00 |

**Home Setup:** appliances, furniture, equipment (one-time setup costs)
**Maintenance:** contractor payment
**Background Check:** tenant screening fee

### Key Financial Notes

- **Starting deficit:** $9,973.40 accumulated Dec 2025 – May 2026
- **Monthly mortgage:** $1,887.36 (fixed)
- **Break-even projection:** Based on Shanik's ~$2,200/mo rent and $1,887.36 mortgage — projected to reach break-even eventually
- **Net P&L** uses operating income ONLY (deposits excluded as liabilities)

---

## Dashboard Features

### KPI Cards (5 cards)
- Operating Income ($3,950 — rent + app fees + storage)
- Deposits / Liability ($1,350 total — refundable, shown separately)
- Total Cash Received (operating income + deposits)
- Total Expenses
- Net P&L (Operating) — operating income minus expenses

### Charts (Chart.js v4.4.0)
1. **Income vs Expenses** — stacked bar chart, income split into Operating Income + Security Deposits, expenses grouped; rich tooltips show month-by-month breakdown
2. **Income Donut** — income composition breakdown
3. **Expense Donut** — expense category breakdown
4. **Break-even Projection Table** — monthly projections forward

### Tenant Timeline
Visual bar showing: `Geethika (Dec 2025 – Apr 2026)` → `Transition` → `Shanik (Jun+)`

### Monthly Cards (Row)
Individual month cards showing income, expenses, and P&L with color-coded footer (red = loss, green = profit).

### Tooltip
Custom HTML tooltip positioned on hover over expense stacks, shows itemized expense breakdown for that month.

---

## Design System

**Light blue/white professional theme** (not dark).

```css
body {
  background: linear-gradient(145deg, #edf1f7 0%, #e5ecf5 100%);
  color: #1e293b;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}
```

**Key colors:**
- Primary text: `#0f172a` / `#1e293b`
- Secondary text: `#64748b` / `#94a3b8`
- Border: `#dde5f0`
- Green (positive): `#16a34a` / `#22c55e`
- Red (negative): `#dc2626` / `#ef4444`
- Chart colors: mortgage `#6366f1`, gas `#f97316`, electricity `#eab308`, internet `#0ea5e9`, homeSetup `#10b981`, maintenance `#f43f5e`, bgCheck `#94a3b8`

**Chart library:** Chart.js v4.4.0 via CDN

---

## Critical Business Logic

### Deposits Are Liabilities
Security deposits ($250 from Geethika Dec 2025, $1,100 from Shanik May 2026) are **NOT income**. They are refundable liabilities. The dashboard shows them separately in KPIs and charts. Net P&L is calculated WITHOUT deposits.

### Operating Income Definition
`Operating Income = Rent + App Fees + Storage Room fees`
Does NOT include security deposits.

### Net P&L Formula
`Net P&L = Operating Income − Total Expenses`

### December 2025 Special Case
No mortgage recorded for Dec 2025 (mortgage started Jan 2026 — possibly first payment). Home setup costs of $1,764.71 were incurred preparing the property.

---

## Tech Stack

- **Pure HTML/CSS/JS** — single self-contained file
- **Chart.js v4.4.0** (CDN) — only external dependency
- **Static** — deploy directly to GitHub Pages

---

## Files in This Project

| File | What It Is |
|------|-----------|
| `bethel-rental-dashboard.html` | The complete financial dashboard — single file, all features |

---

## Git Setup (To Do)

```bash
git init
git add .
git commit -m "Initial commit — Bethel rental property dashboard"
git remote add origin <YOUR_GITHUB_REPO_URL>
git push -u origin main
```

---

## What's Next / Ideas

- [ ] Add June 2026 data once Shanik's rent starts (expected ~$2,200/mo)
- [ ] Track actual vs projected break-even month
- [ ] Add a running deficit/surplus tracker
- [ ] Show cumulative cash flow chart (how much is still in the hole vs recovered)
- [ ] Add Shanik's full lease terms once finalized
- [ ] Consider adding a cash flow projection 12 months forward
- [ ] Clarify gas/electricity tracking — are these owner's costs after tenant transition, or split with tenant?
