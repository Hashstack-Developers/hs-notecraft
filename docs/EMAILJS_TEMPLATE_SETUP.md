# EmailJS Template Setup Guide

## Template Configuration Based on Your Image

Based on your EmailJS dashboard screenshot, here's how to configure the template:

### Email Settings (Right Panel):

1. **To Email**: `{{to_email}}` or `{{customer_email}}`
   - This will automatically use the customer's email from the order

2. **From Name**: `H&S NoteCraft`
   - Your business name

3. **From Email**: 
   - Check "Use Default Email Address" (your connected email service)
   - OR enter: `hsnotecraft@gmail.com`

4. **Reply To**: `hsnotecraft@gmail.com`
   - Where customers can reply

5. **Bcc**: (Leave empty or add your backup email)

6. **Cc**: (Leave empty)

### Subject Line:

```
Order Confirmed - {{product_name}} - H&S NoteCraft
```

OR

```
Order Confirmation - {{customer_name}}
```

### Content Section:

Copy the HTML code from `CUSTOMER_EMAIL_TEMPLATE_EMAILJS.html` and paste it into the Content field in EmailJS.

## Available Variables in Your Payload:

Based on your `customerEmailParams`, you can use these variables in the template:

- `{{to_email}}` - Customer email address
- `{{to_name}}` - Customer full name
- `{{customer_name}}` - Customer full name
- `{{customer_email}}` - Customer email
- `{{customer_phone}}` - Customer phone number
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

## Step-by-Step Setup:

1. **Go to EmailJS Dashboard** → Email Templates
2. **Click "Create New Template"** or edit existing template `template_nk9829i`
3. **Set Template Name**: "Customer Order Confirmation"
4. **In the Content tab**:
   - Switch to "Desktop" view
   - Click "Edit Content" (pencil icon)
   - Paste the HTML from `CUSTOMER_EMAIL_TEMPLATE_EMAILJS.html`
   - Click "Save"
5. **In the Settings** (right panel):
   - **To Email**: `{{to_email}}`
   - **From Name**: `H&S NoteCraft`
   - **From Email**: Use default or `hsnotecraft@gmail.com`
   - **Reply To**: `hsnotecraft@gmail.com`
6. **Set Subject**: `Order Confirmed - {{product_name}} - H&S NoteCraft`
7. **Click "Save"** button (blue button with checkmark)

## Testing:

1. Click "Test It" button in EmailJS
2. Fill in test values for variables
3. Send test email to verify formatting

## Notes:

- All variables use double curly braces: `{{variable_name}}`
- EmailJS will automatically replace these with actual values
- The template is mobile-responsive
- HTML tables are used for better email client compatibility

