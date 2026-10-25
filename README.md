# ShipBox Checkout

Package-forwarding checkout with a sign-up coupon that can't be double-dipped, honest payment outcomes and shipment tracking.

> **Status: in development.** This repo is the plan and the write-up; the interactive demo is being built next.
> **Demo preview:** https://julynard.github.io/shipbox-checkout/ (becomes the live demo when it ships).

Part of [Julynard Tago-on's portfolio](https://julynardtago-on.netlify.app/#projects). Based on the package-forwarding platform at CoreProc where I shipped the sign-up coupon program and hardened payment confirmation.
Client code is private, so this is a clean-room demo with fictional data. No client names or real data.

## What the demo will show

- [ ] Sign up, "verify" your email (inbox preview) and receive a sign-up coupon (code, percentage, 30-day expiry)
- [ ] The coupon discounts the shipping fee on the **first checkout only**
- [ ] A **"Try to double-dip"** button opens a second order and shows the guard blocking it
- [ ] Payment outcomes (success / failed / expired session) are recorded with a reason the customer can see
- [ ] Shipment tracking timeline (Received → Verified → Paid → In transit → Delivered, future steps greyed)

Every key action will have an **"In production"** note explaining how the real system does it.

## How the production system works

The real system runs on Laravel. The demo simulates these behaviours in the browser so it can stay fast and always on.

- A legacy Laravel app extended safely with regression tests around money paths
- The coupon is claimed on **confirmed payment**, inside an atomic transaction, and only one discounted order can be paid
- Coupon issuance never breaks registration; the coupon email goes out after verification
- Every payment-gateway outcome stored with status and failure reason

## Planned stack

- Vue 3 + TypeScript + Vite
- Tailwind CSS v4
- Pinia (state saved in the browser, with a **Reset demo** button)
- Vitest for the domain logic, ESLint + Prettier + `vue-tsc` in CI
- GitHub Actions → GitHub Pages (free, always on)

## Roadmap

1. Project scaffold, CI (lint, type-check, test, build) and GitHub Pages deploy
2. Domain logic with Vitest tests
3. UI with seeded data, guided steps and "In production" notes
4. Screenshot/GIF in this README and the live demo link

## Author

**Julynard Tago-on**, Laravel / PHP full-stack engineer · [Portfolio](https://julynardtago-on.netlify.app) · [GitHub](https://github.com/Julynard) · [LinkedIn](https://www.linkedin.com/in/julynard-tago-on/)

## License

[MIT](LICENSE)
