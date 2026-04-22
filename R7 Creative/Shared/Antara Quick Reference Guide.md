# Antara Quick Reference Guide

*Source: Google Drive (shared by grobenmarketing@gmail.com) — https://docs.google.com/document/d/1SyuqROwgX-9MtyQoDBCtrAsehGJeCSSQBJdNyuW22o0*

## Order Management

### Creating New Orders
1. Navigate to **Orders** > **New Order**
2. Select customer from dropdown
3. Enter order details and products
4. Set delivery date and ship date
5. Click **Save** to create draft or **Book** to finalize

### Cloning Orders
1. Open existing order
2. Click **Actions** > **Clone Order**
3. System creates duplicate with "Copied from [Order ID]" notation
4. Modify cloned order as needed
5. Update delivery/ship dates
6. Book when ready

### Converting Orders to Quotes
- Use clone function on existing order
- Change order type to **Quote** in dropdown
- Adjust pricing and details as needed
- Quote ID will reference original order

## Art Card Management

### Attaching Art Cards
1. In order details, locate **Art Card** section
2. Upload file or attach existing art card
3. Select appropriate file type (artwork, proof, reference)
4. Tag files for vendor if needed

### Tagging Art Files for Vendors
1. Upload artwork to art card
2. Use **Tag** function to mark as "Vendor Info"
3. Only vendor-tagged files will be sent to supplier
4. Internal files (Word docs, references) should NOT be tagged for vendors

### Tracking Art Hours
- Art department logs hours in designated field
- Hours are tracked separately from order costs
- Review hours in art card summary section

## Pricing Management

### Adding Setup Charges
1. In product line items, add **Miscellaneous** item
2. Label as "Setup Charge" or specific fee name
3. Enter setup amount
4. Setup appears as separate line item on PO/invoice

### Handling Decorations and Transfers
- Add decoration as separate product line
- Link decoration to specific garment/product
- Set quantity to match parent product
- Price includes labor and materials

## Credit Memos

### Creating a Credit Memo
1. Open original order
2. Click **Actions** > **Clone Order**
3. Change type to **Credit Memo**
4. Update Order ID to: "Credit Memo for [Original Order ID]"
5. Remove products NOT being credited
6. Keep only items being refunded

### Important Notes on Credit Memos
- Delivery/ship dates still required (system requirement — ignore values)
- Order Total displays but is NOT a profit (this is a credit)
- System label clearly marks as "Credit Memo"
- Credit posts to QuickBooks when booked

### Inventory Returns
After booking, popup asks about inventory return:
- **Yes** — return items to inventory (restores at original lot cost)
- **No** — if items are damaged or not returned
- Feature may not be enabled in all systems

### Reconciling Credits with Payments
- Credit memo creates credit note in QuickBooks automatically
- Antara does NOT track actual refund payment
- If issuing refund: manually record removal in Antara ledger
- If applying to next order: leave credit on account, no ledger entry needed

**Critical:** QuickBooks shows expected credit; Antara requires manual reconciliation of actual payment.

## Common Issues

### Test Orders
- Delete test orders to keep system clean
- Verify deletion process: **Actions** > **Delete Order** > Confirm

### Data Import Issues
- Format mismatches during system migration may cause errors
- Billing configurations may need manual correction
- Contact support for bulk data cleanup

### File Upload Tips
- Supported formats: PDF, JPG, PNG, Word, Excel
- Tag appropriately for intended recipient
- Keep file names descriptive
- Avoid special characters in filenames

## Best Practices

### Order Entry
- Complete all required fields before booking
- Double-check delivery dates
- Verify customer information
- Review pricing before finalizing

### Art Card Workflow
- Upload all art files before booking
- Tag vendor files separately from internal files
- Include proofs when needed
- Track art hours for billing purposes

### Credit Memo Processing
- Always reference original order ID
- Book credit memo only after verification
- Document reason for credit
- Reconcile with accounting immediately
