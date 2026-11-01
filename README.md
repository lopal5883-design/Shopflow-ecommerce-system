# Nairobi Cart

A production-ready e-commerce storefront and admin-ready platform built with Next.js, TypeScript, Tailwind CSS, MongoDB, and secure payment integrations for Kenya-focused commerce.

## Architecture overview

- Frontend: Next.js App Router with server and client components
- Styling: Tailwind CSS
- Data layer: MongoDB + Mongoose models under `models/`
- Shared logic: validation, money formatting, pricing, and order-state utilities in `lib/`
- Payments: Stripe, PayPal, and M-Pesa Daraja hooks and callback handlers under `lib/payment/` and `app/api/`
- Auth: NextAuth-ready setup with Google and credentials support
- Testing: Vitest for business logic validation

## Project structure

```text
app/
  admin/
  api/
  cart/
  checkout/
  login/
  order-confirmation/
  orders/
  products/
  page.tsx
components/
lib/
models/
public/
.env.example
package.json
next.config.ts
vitest.config.ts
```

## Local setup

1. Install dependencies:

```bash
npm install
```

2. Create a local environment file:

```bash
cp .env.example .env.local
```

3. Fill in environment variables for MongoDB, NextAuth, payment providers, and email.

For password recovery email, configure either `RESEND_API_KEY` and a verified `EMAIL_FROM` address, or `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, and `SMTP_PASS`. With SMTP, `EMAIL_FROM` is optional and defaults to `SMTP_USER`. Recovery codes expire after 15 minutes and verification attempts are rate limited. Restart the app after updating `.env.local`.

4. Start the app:

```bash
npm run dev
```

5. Open http://localhost:3000

## Production build

```bash
npm run build
npm run start
```

## Testing

```bash
npm test
```

## Deployment

### Vercel (recommended)

- Import the repository into Vercel
- Set all required environment variables from `.env.example`
- Set the framework to Next.js
- Deploy the app

### Important deployment notes

- Use a secure `NEXTAUTH_SECRET`
- Configure MongoDB Atlas or another managed MongoDB instance
- Add production webhook endpoints for Stripe, PayPal, and M-Pesa callbacks
- Set `APP_URL` and `NEXTAUTH_URL` to the deployed domain
- Keep the payment secrets in Vercel environment variables, not in source code

## Core flows implemented

- Storefront landing page and featured catalog
- Product listing, filtering, sorting, and detail pages
- Cart state and checkout flow
- M-Pesa Daraja STK push scaffolding
- Stripe and PayPal webhook-ready API handling
- Order status validation and utility tests

## Notes

This is a functional storefront shell with production-oriented architecture and sandbox-ready integrations. For live commerce, finish wiring the MongoDB-backed entities and provider credentials, then enable real webhooks and transaction verification in your production environment.
