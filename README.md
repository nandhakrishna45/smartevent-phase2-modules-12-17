# SmartEvent Phase 2 — Modules 12–17

A runnable starter implementation for:
- Module 12: simulated payments and payment confirmation
- Module 13: coupon validation and discounts
- Module 14: event reviews and average ratings
- Module 15: in-app notifications
- Module 16: event search, filters and sorting
- Module 17: responsive React UI

## Important
This is a standalone Phase 2 starter scaffold. It is **not merged with your existing Phase 1 repository**, because the Phase 1 source files were not attached in this chat. Merge these modules into your existing project before replacing any Phase 1 files.

## Requirements
- Python 3.10+
- Node.js 18+

## Run the backend
```bash
cd backend
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload
```
API docs: http://127.0.0.1:8000/docs

The database `smartevent.db` is created automatically. Demo seed data is included.

## Run the frontend
Open a second terminal:
```bash
cd frontend
npm install
npm run dev
```
Open the local URL printed by Vite.

## Demo flow
1. Browse/search events.
2. Select an event and enter a booking ID (demo booking IDs are shown in the API docs/seed data).
3. Apply coupon `WELCOME10` or `FLAT100`.
4. Simulate payment and see the confirmation state.
5. Use the review and notification panels.

## API overview
- `GET /events` — search/filter/sort events
- `POST /bookings/{booking_id}/checkout` — calculate checkout with optional coupon
- `POST /bookings/{booking_id}/pay` — simulate payment
- `GET /payments/{payment_id}` — payment status
- `GET /events/{event_id}/reviews` — reviews and average rating
- `POST /events/{event_id}/reviews` — submit review (JWT required)
- `GET /notifications` — current user's notifications (JWT required)
- `PATCH /notifications/{notification_id}/read` — mark read (JWT required)
- `POST /coupons` — create coupon (demo/admin use)
- `POST /auth/demo-token` — issue a demo JWT for a seeded user

## Security notes
This scaffold demonstrates JWT-protected endpoints and server-side validation. The payment endpoint is deliberately a **simulation**, not a real payment gateway. Before production, add real payment-provider signature/webhook verification, proper user registration and role management, rate limiting, migrations, tests, and secrets management. Set `JWT_SECRET` in the environment.
