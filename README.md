## TradeHut Dynamic Site

This adds a lightweight backend (Express + SQLite) with authentication and Stripe payments to the existing static site.

### Prerequisites
- Node 18+
- Stripe account (test mode is fine)

### Setup
1. Open a terminal in `TradeHut/` and install deps:
   - `npm install`
2. Create `.env` in `TradeHut/` with:
   - `PORT=3000`
   - `JWT_SECRET=change_me`
   - `STRIPE_SECRET_KEY=sk_test_xxx`
   - `STRIPE_WEBHOOK_SECRET=whsec_xxx`
   - `CLIENT_URL=http://localhost:3000`

### Run
- Start the server: `npm run dev`
- Visit `http://localhost:3000`

### Auth Pages
- `signup.html`, `login.html` create/login accounts
- `dashboard.html` shows investments and lets you add funds via Stripe

### Stripe Webhook
Expose your local server and register the endpoint:
- Endpoint: `http://localhost:3000/api/webhook/stripe`
- Events: `checkout.session.completed`, `checkout.session.expired`

Using Stripe CLI:
```
stripe listen --forward-to localhost:3000/api/webhook/stripe
```


