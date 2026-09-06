# Data model overview

The production system uses tables including products, suppliers, tags, product_tags, stock_transactions, waste_logs, activity_logs, recycle_bin, profiles, stock_transfers, inventory_settings, purchase_orders and master_orders.

## Product stock fields

Products track physical stock, safety stock, supplier, pack/SKU information, off-peak max hold, peak max hold and quantity currently on order.

## Purchase orders

Purchase-order lines belong to a master order and track product, supplier, quantity ordered, quantity received, order date, expected arrival, status and notes.

## Stock transfers

Transfers record whether stock was borrowed or given, counterparty, quantity, return progress, dates and the user who created the record.

## Auditability

Operational actions are written to transaction/activity history so stock movements and order actions can be reviewed later.
