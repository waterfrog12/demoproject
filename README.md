# KiranaPro – Grocery Management App Blueprint for Indian Kirana Stores

This document describes a **practical, easy-to-use, and detailed app design** for Indian kirana stores. It focuses on real daily workflows: buying stock, selling items quickly, handling customer udhaar (credit), managing expiry, reconciling cash, and understanding store performance.

---

## 1) Product Vision

Build a mobile-first and desktop-friendly app that helps kirana owners:
- Run billing fast at the counter.
- Keep accurate stock without complex setup.
- Track supplier dues and customer credit in one place.
- Avoid stock-outs and expiry losses.
- Accept and reconcile cash, UPI, and card payments.
- Get simple daily insights in their preferred language.

### Target Users
- Store owner (often primary decision maker)
- Billing/counter staff
- Family member helping with accounts
- Part-time inventory helper

---

## 2) Core Design Principles (for low-tech comfort)

1. **3-tap operations** for common tasks (new bill, add stock, record payment).
2. **Large touch-friendly buttons** + clear icons + minimal text clutter.
3. **Offline-first support** (continue billing even with weak internet).
4. **Regional language support** with easy toggle and transliteration search.
5. **Voice-assisted data entry** (optional): “Add 10 kg sugar received”.
6. **Error prevention**: confirmations for delete/edit, duplicate invoice checks.
7. **Trust through transparency**: visible audit trail for stock and cash changes.

---

## 3) App Modules (What the app should include)

## A. Inventory Tracking Module
**Purpose:** Real-time stock visibility and control.

### Key Features
- Product master with:
  - Name (English + regional language)
  - Barcode/SKU or local code
  - Category (atta, rice, pulses, snacks, dairy, etc.)
  - Unit type (kg, litre, piece, packet)
  - Purchase price, selling price, MRP
  - GST/slab if applicable
  - Batch number and expiry date (for packaged items)
- Stock in/out entries (purchase, return, damage, wastage, manual adjustment)
- Multi-pack handling (e.g., 1 box = 24 packets)
- Reorder level and safety stock per item
- Slow-moving vs fast-moving item tags

### Challenges Solved
- “Stock is available but not visible in system” → quick adjustment with reason code
- “Owner does not know what is near expiry” → expiry dashboard and alerts

---

## B. Billing & Invoicing Module (POS)
**Purpose:** Fast checkout and professional invoices.

### Key Features
- Quick bill creation:
  - Search by name, barcode, phonetic search in regional language
  - Frequently sold items shortcuts
- Auto-calculate discounts (item-level or bill-level)
- Split payments in a single invoice (cash + UPI + card)
- Print/WhatsApp/SMS invoice
- GST-ready invoice format (where needed)
- Return/refund and exchange flows
- Queue hold/resume for busy counter hours

### Challenges Solved
- “Rush-hour billing is slow” → one-screen quick billing + item favorites
- “Payment mode confusion at day-end” → mode-wise collection auto-summary

---

## C. Supplier Management Module
**Purpose:** Manage procurement and payable accounts.

### Key Features
- Supplier profile with contact details and typical lead time
- Purchase order (PO) creation and status tracking
- Goods Received Note (GRN) with quantity mismatch handling
- Supplier bill upload/photo and due date reminders
- Supplier return handling for damaged/expired stock
- Supplier ledger (opening balance, purchases, payments, dues)

### Challenges Solved
- “Forgot due payments to distributor” → payable reminders and due calendar
- “Delivered quantity mismatch” → GRN variance capture

---

## D. Stock Replenishment & Alerts Module
**Purpose:** Never run out of high-demand products.

### Key Features
- Daily auto-generated reorder suggestions:
  - Based on sales velocity + seasonality + lead time
- Low-stock alerts with urgency labels:
  - Critical (stockout in <2 days)
  - Warning (stockout in <5 days)
- Festival-aware demand hints (Diwali, Eid, Pongal, etc.)
- One-tap convert “reorder suggestions” to supplier PO

### Challenges Solved
- “Hot items get sold out suddenly” → predictive reorder list

---

## E. Customer Management & Loyalty Module
**Purpose:** Increase repeat purchases and manage regular customers.

### Key Features
- Customer profiles (name, phone, area, preferred language)
- Purchase history and preferences
- Loyalty points / cashback rules (optional)
- WhatsApp offers to selected customer groups
- Household monthly basket insights (e.g., staples re-order cycle)

### Challenges Solved
- “No record of regular customer habits” → personalized restock/sales strategy

---

## F. Credit (Udhaar) & Debt Management Module
**Purpose:** Track receivables and payables reliably.

### Key Features
- Udhaar bill marking at checkout
- Customer-wise outstanding balance and ageing buckets
  - 0–15 days, 16–30, 31–60, 60+
- Auto reminders via SMS/WhatsApp in regional language
- Part-payment support and receipt generation
- Family/shared customer accounts
- Supplier dues in same financial dashboard (payables)

### Challenges Solved
- “Cash flow stuck in pending udhaar” → automated follow-up and ageing visibility

---

## G. Expiry & Loss Prevention Module
**Purpose:** Reduce wastage and margin leakage.

### Key Features
- Batch-level expiry tracking
- Alerts for items expiring in 30/15/7/2 days
- Suggested actions:
  - Discount
  - Bundle offer
  - Supplier return
- Dead stock and spoilage analysis

### Challenges Solved
- “Expired stock discovered too late” → early warnings and action playbook

---

## H. Cash Register & Shift Closure Module
**Purpose:** End-of-day reconciliation without confusion.

### Key Features
- Opening cash entry per shift
- Cash in/out logging with reason (petty expense, change refill)
- Till/balance counter at close:
  - Expected cash vs actual cash
  - Variance capture with reason
- Payment-mode wise totals (cash, UPI, card, credit)
- Shift handover notes

### Challenges Solved
- “Cash mismatch at end of day” → structured closure and variance log

---

## I. Reports & Simple Analytics Module
**Purpose:** Actionable decisions, not complicated BI.

### Daily/Weekly/Monthly Reports
- Sales summary (gross/net/profit estimate)
- Top-selling products and categories
- Low margin items
- Dead stock and near-expiry stock
- Customer credit outstanding and collection trend
- Supplier payable due report
- Payment mode mix trend (cash vs UPI vs card)
- Peak sale hours and staff performance snapshot

### Suggested Smart Insights
- “Increase reorder quantity of Item X by 20% this week.”
- “Item Y has high sales but low margin; review pricing.”
- “Customer segment Z has rising udhaar; tighten credit terms.”

---

## 4) End-to-End Daily Workflow (Practical Store Day)

1. **Morning opening**
   - Start shift, enter opening cash.
   - Check low-stock and expiry alerts.
   - Confirm today’s planned supplier deliveries.

2. **Stock receiving**
   - Receive delivery, scan/input quantities.
   - Capture mismatches and batch expiry details.
   - Update stock automatically.

3. **Counter sales all day**
   - Create bills quickly (barcode/search/favorites).
   - Accept mixed payment modes.
   - Mark udhaar where needed and print/share invoice.

4. **Mid-day checks**
   - Auto low-stock reminders for fast movers.
   - Trigger quick reorder PO for critical products.

5. **Customer follow-ups**
   - Send automated credit reminders.
   - Share offers for expiring inventory clearance.

6. **Shift/day close**
   - Reconcile cash drawer.
   - Review sales, collections, credit additions.
   - Generate daily report and backup/sync data.

---

## 5) Automation & Reminder Engine

### Automated Jobs
- Daily 7 AM: Low-stock + expiry summary
- Every 2 hours: Critical stockout risk monitor
- 6 PM: Pending supplier delivery reminder
- 8 PM: Udhaar collection reminder list
- End of day: Auto-generate day closure report PDF

### Notification Channels
- In-app notifications
- WhatsApp alerts
- SMS fallback (for low-data regions)

---

## 6) Regional Language & Accessibility

### Language Support (Phase-wise)
- Phase 1: English, Hindi
- Phase 2: Marathi, Tamil, Telugu, Bengali, Kannada, Malayalam, Gujarati, Punjabi

### Accessibility Features
- Big-font mode for readability
- High-contrast theme
- Voice prompts for key actions
- Guided onboarding with “demo mode”
- Contextual tooltips in selected language

---

## 7) Recommended Screens (UI Outline)

- Dashboard (today’s sales, alerts, due collections)
- Quick Billing Screen
- Inventory Screen (stock, expiry, adjustments)
- Purchase & Supplier Screen
- Credit Ledger Screen (customer & supplier)
- Reports Screen (simple charts + downloadable statements)
- Settings (language, printer, tax, user roles)

---

## 8) Roles & Permissions

- **Owner/Admin**: full access, analytics, pricing, credit policy
- **Cashier**: billing, returns, basic customer entries
- **Stock Manager**: inventory updates, GRN, reorder drafts
- **Account Assistant**: payments, ledgers, reconciliation

Role-based controls reduce accidental edits and fraud risk.

---

## 9) Data & Operational Safeguards

- Auto cloud sync when internet is available
- Local offline backup queue
- Daily encrypted backup export
- Audit logs for edits (price, stock, ledger, cash)
- PIN/OTP-based sensitive action approvals (refunds, manual stock decrease)

---

## 10) Success Metrics for Store Owners

Track these KPIs in-app:
- Stockout rate
- Expiry loss value
- Credit recovery rate
- Gross margin trend
- Cash variance incidents
- UPI adoption ratio
- Repeat customer contribution

---

## 11) Suggested MVP (First Release)

Must-have for launch:
1. Quick billing with multi-payment support
2. Basic inventory + low-stock alerts
3. Customer udhaar ledger + reminders
4. Supplier ledger + purchase entry
5. Daily sales and cash closure reports
6. Hindi + English support

Then expand with advanced analytics, loyalty, and forecasting.

---

## 12) Implementation Notes (Optional Technical Direction)

- Platform: Android-first app + lightweight web admin
- Offline store: local database with sync queue
- Integrations: thermal printer, barcode scanner, WhatsApp API, SMS gateway, UPI QR support
- Modular architecture so features can be enabled by store size and maturity

---

This blueprint is designed to be practical for small kirana stores while still scalable for growing neighborhood chains.
