# Architecture

## Frontend

The application is a static single-page interface built with HTML, CSS and vanilla JavaScript. It connects to Supabase using the browser client and is suitable for Cloudflare static deployment.

## Backend

Supabase PostgreSQL stores products, suppliers, tags, stock transactions, waste logs, stock transfers, purchase orders, master orders, inventory settings and audit/activity data.

## Authentication and security

Users sign in with Supabase Auth. Database access is protected with Row Level Security. Sensitive state-changing operations are implemented through authenticated RPC functions where appropriate.

## Inventory authority

Keyline counts are the authoritative source of physical stock-on-hand. Ordering and receiving manage expected stock separately through On Order. This prevents receiving, waste or ordering from silently rewriting the physical count.

## Ordering flow

A master order groups multiple purchase-order lines. Draft orders do not affect On Order. When confirmed, each line contributes its ordered quantity to On Order. Receiving then reduces the outstanding amount.

## Deployment

The frontend is designed for static hosting on Cloudflare Workers/static assets, while Supabase provides database and authentication services.
