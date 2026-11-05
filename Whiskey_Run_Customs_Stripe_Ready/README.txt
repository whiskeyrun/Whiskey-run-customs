WHISKEY RUN CUSTOMS - STRIPE CHECKOUT PROJECT

What's included:
- public/index.html: updated storefront with the prices you supplied.
- netlify/functions/create-checkout.mjs: server-side Stripe Checkout session creator.
- netlify.toml: Netlify publish and Functions configuration.
- package.json: Stripe server SDK dependency.

Fixed prices configured in both the storefront and server-side price validation:
- Laser-Engraved RFID Wallets: $60
- Slate Coasters: $20
- Small Slate Charcuterie Boards: $25
- Large Slate Charcuterie Boards: $50

Quote-only items:
- One-of-a-Kind Lazy Susans (price varies by size/design)
- Custom Wood Charcuterie Boards (custom quote)
- 3D CNC Wood Carvings & Military Seals (price varies by size/design)

IMPORTANT BEFORE DEPLOYMENT:
1. Do not put Stripe keys in public/index.html or any public browser code.
2. Add STRIPE_SECRET_KEY as a Netlify environment variable. The current rk_live key is a live restricted key; confirm it has Checkout Sessions: Write permission. Do not paste it into chat.
3. Test with a Stripe test-mode restricted key (rk_test_...) first, and test mode in Stripe. Do not use a live key for test transactions.
4. Configure shipping charges and tax rules before accepting real orders. This project collects a US shipping address but does not add a shipping fee or calculate tax.
5. Add an order fulfillment/payment webhook workflow before relying on automatic order processing. This starter sends customers to Stripe-hosted Checkout but does not yet send an order notification to the store.
6. Deploy the full project with Netlify build/deploy support so Netlify processes netlify/functions. A plain static upload of only public/index.html will NOT deploy the serverless function.

Netlify environment variable:
Name: STRIPE_SECRET_KEY
Value: your Stripe test restricted key while testing; replace with a properly scoped live restricted key only after successful testing.

Stripe key scope:
- Checkout Sessions: Write (minimum required by the Checkout Session creation endpoint)
Keep unrelated permissions disabled. If Stripe returns a permission error, use the error details/request logs to adjust the key rather than granting broad access.
