# Project Udyam Digital — working hackathon prototype

This project uses the complete supplied synthetic dataset pack. It includes a React/Vite frontend and Express backend.

## Features
- AI Business Advisor; catalogue-grounded product selection and optional CometAPI explanations.
- Product catalogue and bundle recommendations.
- Quote/checkout with monthly price and setup charges.
- KYC upload and mock GSTIN/Udyam registry matching.
- Order creation and status tracker.
- Admin insights calculated from the 5,000-row lead dataset.
- Original data pack, KYC specimen images, case PDF and submission PPTX template included.

## Run locally
Requires Node.js 18+.

Backend:
```bash
cd backend
npm install
cp .env.example .env
npm run dev
```
Runs at http://localhost:5000

Frontend (second terminal):
```bash
cd frontend
npm install
npm run dev
```
Runs at http://localhost:5173

## CometAPI
Put your key in `backend/.env` as `COMET_API_KEY`. Set `COMET_BASE_URL` and `COMET_MODEL` to the values shown in your CometAPI account. Restart the backend. Never expose this key in frontend code. Without a key, the advisor uses a deterministic catalogue-based explanation.

## API routes
- `GET /api/health`
- `GET /api/products`
- `POST /api/advisor/recommend`
- `POST /api/orders`, `GET /api/orders`, `GET /api/orders/:id`
- `PATCH /api/orders/:id/status`
- `POST /api/kyc/upload`, `POST /api/kyc/verify`
- `GET /api/admin/overview`, `GET /api/admin/leads`

## Demo limitations — read before submission
- Product recommendations and prices are derived from `product_catalogue.csv`; the AI only explains them.
- KYC upload is implemented, and GSTIN/Udyam registry lookup uses the provided mock CSVs. OCR extraction and document-to-registry matching are not implemented yet. Uploading a file does not mean KYC passed.
- Orders are stored in a local JSON file (`backend/store.json`) for easy demo setup, not MongoDB. Replace with MongoDB for production.
- No production authentication/authorization is implemented. Add roles, audit logs, rate limiting, encryption, malware scanning, retention/deletion jobs and secure cloud storage before handling real data.
- All supplied records are synthetic. Registry lookups are mock-only and do not contact government services.

## Suggested 3-minute demo
1. Advisor: select a clinic or kirana business and generate recommendations.
2. Add products and show quote totals.
3. Enter contact/business details, accept consent and place order.
4. Upload a specimen KYC file and test a matching GSTIN/Udyam identifier from CSV.
5. Open tracker and admin insights.

See `docs/PRIVACY_NOTE.md` and `docs/ARCHITECTURE.md`.
