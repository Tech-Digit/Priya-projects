# Purchase Dashboard Task Summary..

## Oct 1

**Staff login and Create User page.** Staff can now log in with a username and password checked against the users table. A new Create User page lets an admin add staff. A supplier code can no longer clash with a staff username. (Modifications on login, Define create user page, Update)
- UserController.php (staff login, user create), User.php, SupplierController.php (code clash check)
- LoginPage.vue, CreateUserPage.vue (new page), PurchasingDashboard.vue
- translations.js, routes/api.php

**Header "Create User" button.** Only the hardcoded admin or users-table id 1 sees the button and can open the page. (Header changes)
- PurchasingDashboard.vue

**Change logs show who made the change.** The frontend sends the logged-in user in an X-Change-By header (admin, or the supplier code), and the log table gets Field, Old Value, New Value and Changed By columns. (Logs changes)
- OrderItemController.php
- DashboardPage.vue, PurchasingDashboard.vue, SupplierDetailPage.vue

## Oct 2

**Final container details: stock warning (disabled for now).** Code added to warn when a product sells faster than its stock allows (last 3 months of sales against warehouses 1, 8 and 33), then switched off. (Update)
- ContainerController.php, InvStock.php, SalesHostinger.php
- FinalContainerDetails.vue, routes/api.php

## Oct 5

**Standard carton label: print only selected items.** Labels are printed only for the ticked rows, while serial numbers still run across the whole PO (PO number + 3-digit running number). Bold font file added for the label PDF. (Standard carton label view changes, Font file correction)
- OrderDetailPage.vue
- DejaVuSans.ttf, DejaVuSans-Bold.ttf

**Inspection checklist sample format.** A sample format table is shown when uploading an inspection checklist (the sample Excel download button is disabled for now). (Correction)
- SupplierDocumentManager.vue

**Inspection checklist: merged SKU cell structure fix.** A filled SKU cell starts a new group, and the rows below it with an empty SKU cell belong to that group. SKUs are matched only against their own group's check lines. (Inspection checklist structure issue check)
- XlsxProcessingService.php, FinalContainerDetails.vue

## Oct 7

**Saved invoice loads into the UK and DE invoice screens.** The invoice modal now shows the data from the last saved invoice for the container, with a notice, and can be edited and saved again. The Save button stays at the bottom of the modal. (Saved invoice check)
- FinalContainerDetails.vue, translations.js

**Invoice column translation correction.** The UK and DE invoice table headers (No, Items, HS Code, Name, Units, Price FOB, FOB RMB) now use translated labels. (Translation correction)
- FinalContainerDetails.vue, translations.js

**Carton label: long product name fit.** The name starts at 28pt and shrinks to 12pt. If it still doesn't fit, it wraps onto two lines at a smaller size and is cut off with "…" after the second line. (Update)
- OrderDetailPage.vue

## Oct 12

**BRL label exception.** For supplier BRL, mixed cartons hold up to 4 SKUs at 20 pcs each (80 pcs). Pcs are pooled across SKU lines and cartons are filled, with a new mixed-label PDF page. (BRL label exception)
- OrderDetailPage.vue

**Same product, different colour: colour fields.** Colour (English and Chinese) added to the order item child and child product records, with validation, save and an edit input. (Same product,diff color label exception add)
- OrderItemController.php, ChildItemProduct.php, OrderItemChild.php
- OrderDetailPage.vue

**Same product, different colour: one label.** SKUs that differ only in their last 2 letters print as one label for up to 7 colours. The group takes one carton slot and one serial. (carton label rule modify)
- OrderDetailPage.vue

**Carton count fix.** "Carton x of N" now runs over the selected products' cartons only (all items when nothing is selected). (Correction)
- OrderDetailPage.vue

**AL1 / CND label rule exception and rules info.** An admin-only info button opens a "Carton label rules" modal that explains what Generate Carton Labels does. A child with 0 CTNs rides in the parent's box (colour rule), and the parent stays a plain label only when a child with its own carton has child products. (AL1,CND rule exception, Rule info add, Update)
- OrderDetailPage.vue

## Oct 13

**Label rules modal text.** Heading changed to "Special cases for this order", and only the rules that apply to the order are shown. The colour rule spells out its conditions: same length, base of at least 4 characters, up to 7 colours (more than 7 prints normal labels with a warning). The BRL rule spells out carton filling and "x of N". (Label rule text modify)
- OrderDetailPage.vue

**English description fallback turned off.** When the order item's english_description is empty, the dashboard no longer falls back to the inventory product description (commented out for now). (Remove fallback)
- DashboardController.php
