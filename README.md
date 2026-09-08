# Hotfix Inventory Management

I started this project because paper stock sheets and basic spreadsheets were making kitchen stock work slower than it needed to be. The aim was to put counting, ordering, receiving, waste and transfers into one mobile-friendly system.

## Main features

- Stock dashboard with low-stock warnings
- Product and supplier records
- Pack sizes, SKUs, safety stock and maximum holding levels
- Keyline stock counts
- Suggested ordering based on stock, usage and delivery schedules
- Purchase orders with draft and confirmed stages
- Delivery receiving and on-order quantity updates
- Waste records
- Borrowed and transferred stock with return tracking
- Activity history and operational reports
- CSV and print/PDF exports
- Email and password authentication

## How the stock process works

The Keyline count is treated as the physical stock figure.

1. A Keyline count records what is physically available.
2. Confirming a purchase order increases the quantity on order.
3. Receiving a delivery reduces the quantity on order.
4. Waste and transfers are recorded separately, so there is a clear activity history.

Draft purchase orders can be saved and reopened without changing the on-order total. The total changes only when an order is confirmed.

## Technology

- HTML, CSS and JavaScript
- Supabase and PostgreSQL
- Supabase Auth
- Row Level Security and authenticated database functions
- Cloudflare Workers and static assets

## Running your own copy

Live credentials are not stored in this repository. A separate Supabase project is required, along with its database tables, policies and functions. The front end must then be configured with the project's URL and publishable key.

Never put service-role keys, passwords or private production credentials in the repository.

## Live version

https://inventorymanagment.rafet2922.workers.dev/

The live system requires an approved account. Public self-registration is disabled, so the repository is mainly available to show the code and project structure.

## Current version

This repository is a portfolio snapshot of the working V12.7 project. It includes the master-order workflow, Keyline stock model, stock transfers, receiving and reporting features.
