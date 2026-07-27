# [Your Brand Name] — Earbuds Site

A simple 2-page site:
- `index.html` — gallery/landing page showcasing the earbuds
- `payment.html` — UPI QR payment page with a form that emails you the buyer's details

## Before you publish

### 1. Add your real photos
Drop your real product images into `/assets`, keeping the same filenames (or update
the `src="assets/..."` paths in `index.html`):
- `hero-cover.png` — main hero image
- `gallery-1.png` through `gallery-6.png` — gallery grid

### 2. Set your brand name
Search both HTML files for `[Your Brand Name]` and replace with your real
brand/business name (header, footer, page titles). Also update `PAYEE_NAME` near the
top of the `<script>` block in `payment.html` — that's what shows up in the buyer's
UPI app when they scan the code.

### 3. Fill in real specs
`index.html` now has: a features section (Bluetooth chip, driver size, gaming mode,
water resistance, voice assistant — each with its own graphic panel in `/assets`),
a full specifications table, a reviews section, and an FAQ accordion. Every number
is a bracketed placeholder — only state specs you can actually back up.

### 3b. Reviews section
Left intentionally empty ("No reviews yet") rather than filled with invented
testimonials. Once you have real customer feedback, replace that block with actual
quotes — and real photos only if the customer agreed to share one.

### 4. UPI ID and price
UPI ID is set to `6395180733-5@ybl`, price defaults to ₹799 (editable by the buyer on
the payment page, same as your cartoon bundle site). To change either, edit `UPI_ID`
and `DEFAULT_AMOUNT` near the top of the script block in `payment.html`, and the
matching `value="799"` attributes on the two amount inputs.

### 5. EmailJS — confirm your template's variable names
The form sends: `name`, `email`, `address`, `pincode`, `utr`, `amount`, `message`,
`time`, `to_email`. Open your EmailJS template (`template_p6tm18q` in the
`service_dp5zyfr` service) and confirm it uses matching `{{name}}`, `{{email}}`, etc.
placeholders, with "To" set to `pareshrawat101@gmail.com` (or using `{{to_email}}`).

### 6. Turn on EmailJS domain restrictions (recommended)
Same note as your other site — once this has a real domain, restrict allowed
origins in your EmailJS dashboard (Account → Security) so only your real site can
send through your account.

## How the payment flow works
1. Buyer opens `payment.html`, sees a QR code generated live from your UPI ID and the
   amount shown (defaults to ₹799, editable).
2. They scan it with any UPI app and pay.
3. They copy the UTR (transaction reference number) and fill in the form —
   including their delivery address and pincode, since this is a physical product.
4. On submit, details are emailed to you via EmailJS. You check the UTR against your
   bank statement, then manually confirm and ship the order.

This form never asks for a UPI PIN, OTP, or card number.

## Hosting
Both files are static HTML — host for free on GitHub Pages, Netlify, Vercel, or
Cloudflare Pages by uploading this whole folder.
