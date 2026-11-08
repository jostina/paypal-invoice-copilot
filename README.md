PayPal Invoice Copilot
PayPal Invoice Copilot helps freelancers turn project notes into a polished invoice draft, review the wording and line item, and collect payment through PayPal Sandbox. AI-generated invoices are drafts only; review every detail before sharing.

Features
AI drafts an invoice title, service description, payment terms, and client note from a short project summary.
Edit invoice details and keep invoices in this browser with local storage.
Create and capture PayPal Sandbox orders from the invoice screen.
Show clear setup states when AI or PayPal credentials are not configured.
Build and run in Replit
Install dependencies and check the project:

pnpm install
pnpm run typecheck
PORT=5173 BASE_PATH=/ pnpm run build
Add these values in Tools → Secrets:

OPENAI_API_KEY — required for AI invoice drafting.
PAYPAL_CLIENT_ID and PAYPAL_CLIENT_SECRET — PayPal Developer Sandbox app credentials.
Start the API Server workflow and the PayPal Invoice Copilot workflow from Replit's Run panel. Their commands are:

pnpm --filter @workspace/api-server run dev
pnpm --filter @workspace/paypal-invoice-copilot run dev
Run these through the configured Replit workflows so the required ports and preview paths are supplied.

Open the PayPal Invoice Copilot preview.

The app uses the shared /api route, so run it in Replit with the API Server workflow rather than starting only the web preview.

Push to your public GitHub repository
Create a public repository on GitHub named paypal-invoice-copilot without initializing a README or license. Then, from the Replit Shell, run:

git remote add origin https://github.com/YOUR-USERNAME/paypal-invoice-copilot.git
git add .
git status --short
git commit -m "Build PayPal Invoice Copilot"
git push -u origin main
Review git status --short before committing. Never put API keys or PayPal credentials in project files; keep them in Replit Secrets.

PayPal Sandbox setup
Create a REST app in the PayPal Developer Dashboard using the Sandbox environment. Save its Client ID and Secret as Replit Secrets with the names above. The server is intentionally pinned to PayPal's Sandbox API; it does not create live payments. Use a PayPal sandbox buyer account to approve a payment.

Never commit API keys or PayPal credentials to the repository. The PayPal Client ID is returned to the browser only after both sandbox credentials are configured; the Client Secret stays on the server.

AI and privacy
Invoice drafting sends the client name, work description, total amount, currency, and due date to OpenAI. Add an OpenAI API key as a Replit Secret before using this feature. Invoices are stored in the browser's local storage, not in a shared database. Do not enter sensitive client information.

Repository structure
artifacts/paypal-invoice-copilot — React web app.
artifacts/api-server — AI drafting and PayPal Sandbox API routes.
lib/api-spec/openapi.yaml — source contract for generated client and validation schemas.
License
This project is open source under the MIT License. See LICENSE.
