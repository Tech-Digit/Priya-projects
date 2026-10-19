# Order Management Task Summary..

All work is on the new inventory overview (/inventory-new) and its sub-pages.

## Sep 29

**Inventory overview: new analytics cards.** Added Stock Transfer (grouped "From <warehouse>" routes), Warehouse Map ("Find any shelf's exact location") and Can't Find Items (shelf items marked "Can't Find") cards. (Update)
- InventoryOverViewNew.vue

## Sep 30

**Manage Shelve Stock: warehouse-specific view.** Opened from a warehouse card, the page shows only that warehouse's details, with no "All" or other-warehouse tabs. The "View all" header link keeps the full filter set. (Manage shelve changes, Correction)
- InvShelves.vue, InventoryOverViewNew.vue

**Refill History page (new).** Overall refill history read from shelf_stock_update_logs, newest first, with the action shown as a "Type" column, a SKU search and a back button. Read-only. (Define refill history page)
- InventoryController.php (getOverallRefillHistory), routes/api.php
- InvRefillHistory.vue (new page), Router.js, InventoryOverViewNew.vue

**Manage Shelve Stock History page (new).** History of manual shelf fixes (manual shelf, capacity and location fixed), newest first, with a SKU search. Read-only. (Manual shelves fix log)
- InventoryController.php (getManualShelfHistory), routes/api.php
- InvManualShelfHistory.vue (new page), Router.js, InventoryOverViewNew.vue

**Transfer History page changes.** A Warehouse (From → To) column, a Transfer History button on the Stock Transfer card, and a back button that returns to the card it was opened from. (Transfer history page changes)
- InvTransferHistory.vue, InventoryOverViewNew.vue

**Add F2-F3 Products Location popup.** An "Add F2-F3 Products Location" popup with a warehouse picker, CSV upload, sample CSV format and a row limit checked before submit (UI only at this stage). (Correction)
- InvShelves.vue

**Stock transfer rules: F2-F3 as the main destination.** (Stock transfer rule change 1 to 7)
- Cables, connectors and transformers (by subcategory keyword) keep going to UK Unit 3 and never show as "into F2-F3" transfers. (Stock transfer rule change 1)
- Products with a usable F2-F3 shelf (warehouse 33 with a location and capacity) are routed to F2-F3, not to Unit 3. A product with no F2-F3 shelf stays on Unit 3. (Stock transfer rule change 2)
- Source priority for transfers into F2-F3 is Unit 4, then Unit 18, with Unit 3 only if neither has stock. If Unit 4 can't cover the shortfall, the rest overflows to Unit 18. (Stock transfer rule change 3)
- Urgent Stock Transfer flag: the destination shelf won't cover today's demand (Inprogress plus on-hold orders). Urgent transfers are listed first, and the Urgent sub-tab badge and list use the same source as the Urgent Refill page. (Stock transfer rule change 4)
- Transfer History route filter with five routes: Unit 4 → F2-F3, Unit 18 → F2-F3, Unit 4 → Unit 3, Unit 18 → Unit 3 and Unit 3 → Unit 4, each with a row count. (Stock transfer rule change 5)
- Manual transfers warn, but don't block, when the quantity is more than the source warehouse's shelf stock. The user confirms and the request is retried. (Stock transfer rule change 6)
- Transfer History shows "Created: System / Manual" and an Urgent flag on transfers that are still open. (Stock transfer rule change 7)
- InventoryController.php, InvTransferHistory.vue, InvManualTransfers.vue, InventoryOverViewNew.vue

## Oct 1

**Suggested transfer qty.** Shows the suggested quantity and an overflow tag on Into F2-F3 transfers. (Show suggested transfer qty)
- InvTransfers.vue

**Overview and sub-page structure change.** Replaced the old "Shelf Status Overview" layout with the card structure, and added F2-F3 and Unit 3/4/18 pair counts for the Stock Transfer route counts. (Structure change)
- InventoryOverViewNew.vue, InventoryOverView.vue
- InvShelves.vue, InvTransfers.vue, InvTransferHistory.vue, InvRefillHistory.vue, InvManualShelfHistory.vue

**Refill section: F2-F3 and Unit 3 cards.** The Refill section shows only F2-F3 (default, the main warehouse) and Unit 3, each with its own band counts and Top/Temporary Urgent split. A card opens the Urgent Refill page on that warehouse's tab only. (Refill section change)
- InventoryController.php (per-warehouse urgent counts)
- InvTask.vue, InvUrgent.vue, InventoryOverView.vue, InventoryOverViewNew.vue

**Stock Transfer section order.** The F2-F3 outgoing routes lead the card. (Stock transfer section change, Typo correction)
- InvUrgent.vue, InventoryOverView.vue, InventoryOverViewNew.vue

## Oct 2

**F2-F3 location upload on the Manage Shelves page.** The Add Products Location popup now uploads the CSV, the same as the F2-F3 popup on /inventory-new. The file is cleared after submit so the same CSV can't be sent twice, and the list refreshes so new locations show. (F2f3 location upload issue check on invshelve page)
- InvShelves.vue

## Oct 13

**F2-F3 location change history.** A new "F2-F3 Location History" popup lists uploads from inventory_logs (url f2f3-products-location-upload), with a SKU search, paging and dates shown as "13 Oct 2026, 14:32:05". (Add f2f3 location change history view)
- InventoryController.php (getF2F3LocationHistory), routes/api.php
- InvShelves.vue

**Download CSV for F2-F3 location history.** Downloads every matching row (respecting the SKU search), not just the loaded page. The file has a BOM so Excel reads it as UTF-8. (Download csv for f2f3 location)
- InventoryController.php, InvShelves.vue

**Back-navigation fix.** Going back from Manage Shelves now returns to the Manage Shelve Stock card instead of the top of the page. (Navigation user friendly issue fixed)
- InvShelves.vue, InventoryOverView.vue, InventoryOverViewNew.vue
