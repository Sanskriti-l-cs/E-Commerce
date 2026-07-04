# ShopEase

A little e-commerce demo I put together — think Amazon/Flipkart, but scaled way down and running entirely in your browser. No server, no database, no `npm install`. Just open the HTML file and it works.

## What's actually in here

As a shopper you can:
- Browse products across five categories (Electronics, Fashion, Home & Kitchen, Books, Beauty)
- Search by name or description
- Click into a product for the full details
- Add stuff to your cart, adjust quantities, remove items
- Check out with a simple form (name, phone, address) — it's cash-on-delivery style, no payment gateway
- Land on a confirmation page once the order goes through

As the vendor you can:
- Log into `/#/admin/login` (demo credentials below)
- Add, edit, and delete products
- Set price, stock, category, description, and an image (just paste a URL — there's no real file upload here)
- See every order that's come in and update its status (Pending → Processing → Shipped → Delivered, or Cancelled)

## How to run it

Open `shopease.html` in any browser. That's it — double-click it or drag it into a tab.

## Vendor login

```
Email:    vendor@example.com
Password: admin123
```

## The honest part: how this is built

There's no backend. I know the original ask was for a full-stack app with a real Express server and database, and I did build that version too — but this file is the "just show me the website" version, so I stripped the backend out entirely and faked it with `localStorage`.

That means:
- All your products, cart items, and orders are saved in *your browser's* local storage, not on any server
- If you clear your browser data (or open the file in a different browser/incognito window), everything resets back to the default sample products
- The "vendor login" is just a hardcoded email/password check in JavaScript — there's no encryption, no real authentication, no session security. Anyone who looks at the source can see the password. Please don't use this pattern for anything real.
- Nothing here is shared between devices or people — if you open this on your phone and your laptop, they're two completely separate stores

Basically: it's a working *simulation* of the full app, good for demos, portfolio screenshots, or getting a feel for the UX — not something you'd deploy for real customers.

## Tech used

Plain HTML, CSS, and vanilla JavaScript. No React, no build step, no dependencies. There's a tiny hash-based router (`#/`, `#/cart`, `#/admin/dashboard`, etc.) so it feels like a real multi-page app while still being one file.

## If you wanted to make this real

The pieces you'd swap in:
- A real backend (Node/Express, Django, whatever) with an actual database instead of `localStorage`
- Real password hashing and session/JWT-based auth for vendors
- Real image uploads (to S3, Cloudinary, or similar) instead of pasting URLs
- Payment integration if you want actual checkout instead of cash-on-delivery
- Some way to keep one vendor's inventory separate from another's, if you want multiple sellers

If you want, I can also hand you the full-stack version with the real Express + JWT backend — I built that one earlier in this project, just with actual server code instead of the browser-only trick.
