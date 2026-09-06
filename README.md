# Hotfix — Kitchen Inventory Management System

A custom inventory and ordering system built for a busy kitchen operation to replace paper stock sheets and basic spreadsheet workflows with a faster, mobile-friendly web app.

## What it does

- Dashboard with live stock and low-stock visibility
- Product management with pack size, SKU, supplier, safety stock and peak/off-peak max hold
- Keyline counts as the authoritative physical stock-on-hand record
- Smart ordering using current stock, on-order quantity, usage and supplier delivery schedules
- Master purchase orders with **Save Draft**, **Continue Draft** and **Confirm Order**
- Receiving that reduces On Order without changing physical Keyline stock
- Waste logging kept separate from physical stock adjustments
- Stock transfers for borrowed/given stock with partial return tracking
- Insights and reports for transactions, waste, purchase orders, receiving and Keyline history
- CSV and print/PDF exports
- Supabase email/password authentication
- Responsive desktop/mobile UI

## Operational model

The core rule is simple: **Keyline is the physical truth.**

- Keyline sets physical Stock on Hand.
- Ordering increases **On Order**.
- Receiving reduces **On Order** when deliveries arrive.
- Waste is logged separately.

## Tech stack

- Frontend: HTML, CSS and vanilla JavaScript
- Backend: Supabase / PostgreSQL
- Authentication: Supabase Auth
- Database security: Row Level Security (RLS) and authenticated RPC functions
- Hosting: Cloudflare Workers / static assets
- Exports: CSV plus browser Print → Save as PDF

## Purchase-order workflow

1. Add items to the order basket.
2. **Save Draft** without affecting On Order.
3. Re-open with **Continue Draft**.
4. **Confirm Order** when the supplier order is actually being placed.
5. Confirmed quantities are added to On Order.
6. Receiving records what arrived and reduces On Order.

## Running the project

This repository intentionally does **not** contain live production credentials. Configure `index.html` with your own Supabase URL and publishable key. The matching database schema and RPC functions must also exist in that Supabase project.

## Security

The production system uses Supabase Row Level Security and authenticated database functions. Service-role keys, passwords and other private credentials should never be committed to this repository.

## Live deployment

Production deployment: https://inventorymanagment.rafet2922.workers.dev/

Authentication is required, so the public repository is intended mainly as a portfolio/code showcase.

## Project background

Hotfix started as a practical solution to a real kitchen workflow problem: paper-based stock handling and basic spreadsheets made counting, ordering, receiving and tracking stock unnecessarily slow. The system evolved into a PostgreSQL-backed operational tool designed around how the kitchen actually works.

## Status

Portfolio snapshot based on the working V12.7 codebase with the master-order workflow, Save Draft / Confirm Order, Keyline authority model, stock transfers, receiving and reporting features.

## Access control

New users cannot create accounts through the public sign-up option. Access is restricted to approved team members who are invited or provisioned by an administrator.

Supabase Auth enforces this restriction server-side, so the live link cannot be used for self-service registration. The sign-up control may remain visible in the interface as a visual element, but it does not provide account creation access.
