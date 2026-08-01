---
name: List a ticket for sale on StubHub
description: Create a seller listing for an event, then upload the e-tickets that fulfill it.
api: openapi/stubhub-inventory-openapi.yml
operations: [Events_SearchEvents, Events_GetEvent, SellerListings_CreateListingPreview, SellerListings_CreateListing, ETicket_UploadListingETicket]
---

# List a ticket for sale on StubHub

Authenticate with OAuth2 using the **user-login (authorization_code)** flow and the
`write:sellerlistings` scope. Send the token as `Authorization: Bearer <access_token>`
and always include a valid `User-Agent` header (missing it returns `user_agent_required`).

1. Find the event with `Events_SearchEvents` (Catalog API) or resolve it with `Events_GetEvent`.
2. Preview the listing with `SellerListings_CreateListingPreview` to see fees/proceeds before committing.
   You must supply either `ticket_price` or `ticket_proceeds` or you get `validation_failed`.
3. Create the listing with `SellerListings_CreateListing`.
4. Attach the tickets with `ETicket_UploadListingETicket`.

Responses are `application/hal+json`; follow `_links` for related resources. If the event
cannot currently be listed you get `create_listing_not_allowed` (403).
