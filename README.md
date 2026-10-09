# Solstice Bistro

Restaurant website built with React and Vite. Reservation requests are handled by a Vercel
serverless function and emailed through Resend.

## Reservation email setup

1. Create a [Resend](https://resend.com/) account, create an API key, and verify the domain
   used for the sender address.
2. In Vercel, open the project’s **Settings → Environment Variables** and add:
   - `RESEND_API_KEY`: the Resend API key
   - `RESERVATION_EMAIL`: the inbox that should receive reservation requests
   - `RESEND_FROM_EMAIL`: a sender address on your verified Resend domain, such as
     `Reservations <reservations@example.com>`
3. Redeploy the Vercel project so the function receives the new variables.

Never put the Resend API key in frontend code or commit it to Git.

## Local development

Install dependencies and run the full Vercel app locally with the Vercel CLI:

```sh
npm install
npm install --global vercel
vercel link
vercel dev
```

Copy `.env.example` to `.env.local` and set real values before testing email delivery. The Vite
development server (`npm run dev`) serves the frontend only; it does not run the `/api` function.

## Project commands

- `npm run dev` — frontend-only Vite development server
- `npm run build` — production frontend build
- `npm run lint` — lint the project
- `npm run preview` — preview the built frontend
