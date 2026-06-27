# Email Setup Instructions for Order Confirmation

This document explains how to set up EmailJS to send order confirmation emails to customers and order notifications to the website owner.

## Step 1: Create EmailJS Account

1. Go to https://www.emailjs.com/
2. Sign up for a free account (free tier includes 200 emails/month)
3. Verify your email address

## Step 2: Add Email Service

1. In EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the setup instructions for your provider
5. Note down your **Service ID** (e.g., `service_abc123`)

## Step 3: Create Email Templates

### Template 1: Customer Confirmation Email

1. Go to **Email Templates** in EmailJS dashboard
2. Click **Create New Template**
3. Name it: "Customer Order Confirmation"
4. Use this template:

**Subject:** Order Confirmation - H&S NoteCraft

**Content:**
```
Dear {{customer_name}},

Thank you for your order with H&S NoteCraft!

Order Details:
- Product: {{product_name}}
- Size: {{product_size}}
- Binding: {{product_binding}}
- Quantity: {{quantity}}
- Total Price: Rs {{total_price}}

Delivery Information:
- Address: {{delivery_address}}
- City: {{city}}
- Postal Code: {{postal_code}}

Order Date: {{order_date}}

We will process your order shortly and you will receive a confirmation call within 24 hours. 
Standard delivery time is 7 business days via Cash on Delivery (COD).

If you have any questions, please contact us.

Best regards,
H&S NoteCraft Team
```

5. Note down the **Template ID** (e.g., `template_xyz789`)

### Template 2: Owner Notification Email

1. Create another template
2. Name it: "New Order Notification"
3. Use this template:

**Subject:** New Order Received - {{product_name}}

**Content:**
```
New Order Received!

Customer Information:
- Name: {{customer_name}}
- Email: {{customer_email}}
- Phone: {{customer_phone}}

Order Details:
- Product: {{product_name}}
- Size: {{product_size}}
- Binding: {{product_binding}}
- Quantity: {{quantity}}
- Total Price: Rs {{total_price}}

Delivery Information:
- Address: {{delivery_address}}
- City: {{city}}
- Postal Code: {{postal_code}}
- Order Notes: {{order_notes}}

Order Date: {{order_date}}
Order Time: {{order_time}}

Please process this order and contact the customer within 24 hours.
```

4. Note down the **Template ID** (e.g., `template_def456`)

## Step 4: Get Your Public Key

1. Go to **Account** → **General** in EmailJS dashboard
2. Find your **Public Key** (e.g., `abc123xyz789`)
3. Copy it

## Step 5: Update confirmation.html

Replace the following placeholders in `confirmation.html`:

1. **Line with `emailjs.init("YOUR_PUBLIC_KEY")`**:
   - Replace `YOUR_PUBLIC_KEY` with your actual EmailJS Public Key

2. **In the `sendEmails` function, replace:**
   - `YOUR_SERVICE_ID` with your Service ID (appears twice)
   - `YOUR_CUSTOMER_TEMPLATE_ID` with your Customer Template ID
   - `YOUR_OWNER_TEMPLATE_ID` with your Owner Template ID

3. **Update owner email:**
   - Replace `'owner@kaghaz.pk'` with your actual owner/administrator email address

## Example Configuration

After setup, your code should look like this:

```javascript
emailjs.init("abc123xyz789"); // Your Public Key

await emailjs.send(
    'service_abc123', // Your Service ID
    'template_xyz789', // Customer Template ID
    customerEmailParams
);

await emailjs.send(
    'service_abc123', // Your Service ID
    'template_def456', // Owner Template ID
    ownerEmailParams
);
```

## Testing

1. Place a test order
2. Click "Proceed" button
3. Check both customer and owner email inboxes
4. Verify all order details are correctly displayed in emails

## Troubleshooting

- **Emails not sending**: Check browser console for errors
- **Template variables not working**: Ensure variable names match exactly (case-sensitive)
- **Service connection issues**: Re-authenticate your email service in EmailJS dashboard
- **Rate limiting**: Free tier has 200 emails/month limit

## Security Note

The Public Key is safe to expose in frontend code. However, for production, consider:
- Using environment variables
- Implementing rate limiting
- Adding server-side validation

