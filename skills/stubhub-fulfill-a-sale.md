---
name: Fulfill a StubHub sale
description: Poll for new sales and fulfill them by uploading e-tickets or generating a shipping label.
api: openapi/stubhub-sales-openapi.yml
operations: [Sales_GetSalesRecentUpdates, Sales_Get, ETicket_UploadSaleETicket, Shipments_PutOrGetSaleShipmentLabel, Sales_Patch]
---

# Fulfill a StubHub sale

Authenticate with OAuth2 (`write:sales` scope, user-login flow). Bearer token + valid `User-Agent`.

1. Poll `Sales_GetSalesRecentUpdates` (or subscribe to the `sales` webhook topic) for new sales.
2. Read the sale with `Sales_Get`.
3. Fulfill: for electronic delivery use `ETicket_UploadSaleETicket`; for physical shipment call
   `Shipments_PutOrGetSaleShipmentLabel` to print a shipping label.
4. Confirm/update the sale with `Sales_Patch`. Rejecting a sale is `Sales_Delete`.

Acting on a sale that does not support the action returns `invalid_seller_listing_action` (403).
