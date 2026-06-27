# Owner Email Template Setup Guide

## Template Configuration for Owner Notification Email

### Email Settings (Right Panel):

1. **To Email**: `hsnotecraft@gmail.com` (or your owner email)
   - This is a fixed email address for order notifications

2. **From Name**: `H&S NoteCraft Orders`
   - Business name for order notifications

3. **From Email**: 
   - Use your default EmailJS email address
   - OR enter: `hsnotecraft@gmail.com`

4. **Reply To**: `hsnotecraft@gmail.com`
   - Where you want replies to go

5. **Bcc**: (Optional - add backup email for order tracking)

6. **Cc**: (Leave empty)

### Subject Line:

```
🔔 New Order: {{product_name}} - Rs {{total_price}}
```

OR

```
New Order Received - {{customer_name}} - {{order_date}}
```

### Content Section:

Copy the HTML code from `OWNER_EMAIL_TEMPLATE_EMAILJS.html` and paste it into the Content field in EmailJS.

## Available Variables in Owner Payload:

Based on your `ownerEmailParams`, you can use these variables:

- `{{to_email}}` - Owner email (hsnotecraft@gmail.com)
- `{{customer_name}}` - Customer full name
- `{{customer_email}}` - Customer email (clickable)
- `{{customer_phone}}` - Customer phone (clickable)
- `{{product_name}}` - Product title
- `{{product_size}}` - Selected size (A4/A5)
- `{{product_binding}}` - Selected binding (Spiral/Perfect)
- `{{quantity}}` - Order quantity
- `{{total_price}}` - Total price (Rs XXX)
- `{{delivery_address}}` - Full delivery address
- `{{city}}` - City name
- `{{postal_code}}` - Postal code
- `{{order_notes}}` - Order notes (or "None")
- `{{order_date}}` - Formatted order date
- `{{order_time}}` - Order time

## Step-by-Step Setup:

1. **Go to EmailJS Dashboard** → Email Templates
2. **Click "Create New Template"**
3. **Set Template Name**: "Owner Order Notification" or "New Order Alert"
4. **In the Content tab**:
   - Switch to "Desktop" view
   - Click "Edit Content" (pencil icon)
   - Paste the HTML from `OWNER_EMAIL_TEMPLATE_EMAILJS.html`
   - Click "Save"
5. **In the Settings** (right panel):
   - **To Email**: `hsnotecraft@gmail.com` (your owner email)
   - **From Name**: `H&S NoteCraft Orders`
   - **From Email**: Use default or your email
   - **Reply To**: `hsnotecraft@gmail.com`
6. **Set Subject**: `🔔 New Order: {{product_name}} - Rs {{total_price}}`
7. **Click "Save"** button
8. **Note the Template ID** - you'll need this for `confirmation.html`

## Update confirmation.html:

After creating the owner template, update line ~426 in `confirmation.html`:

```javascript
await emailjs.send(
    'service_zp6nb5h', // Your Service ID
    'YOUR_OWNER_TEMPLATE_ID', // Replace with your Owner Template ID
    ownerEmailParams
);
```

Replace `YOUR_OWNER_TEMPLATE_ID` with the actual template ID from EmailJS.

## Template Features:

✅ **Alert-style design** - Red header to grab attention
✅ **Customer contact info** - Clickable email and phone links
✅ **Complete order details** - All information needed to process order
✅ **Action items** - Clear list of what needs to be done
✅ **Quick contact section** - Easy access to customer details
✅ **Order timestamp** - Date and time of order

## Testing:

1. Click "Test It" button in EmailJS
2. Fill in test values for all variables
3. Send test email to your owner email
4. Verify all information displays correctly

