# NovaPulse AI — premium AI platform starter

A responsive, dark, premium-style AI workspace built with Node.js + Express. It is designed to deploy on Railway and also run locally in Termux.

## Included
- Premium responsive dashboard and chat interface
- Demo chat mode when no API key is configured
- Optional OpenAI-compatible chat API integration
- Optional image generation endpoint (provider/model access and billing required)
- Admin page protected by `ADMIN_PASSWORD` (basic starter protection)
- File upload endpoint with size/type limits
- Conversation history saved in the browser
- Feature cards for writing, coding, documents, voice, and image workflows
- Security headers and API rate limiting

## Important limitations
- The no-key demo mode is a UI/demo, not a real AI model.
- Real AI replies and image generation require a valid API key, provider access, and may incur charges. Railway hosting and AI provider billing are separate.
- This starter does not yet include production-grade user accounts, payments, multi-user database, voice transcription, or persistent cloud file storage. Do not advertise those as implemented until added.
- The basic admin password gate is for a starter, not a complete production identity system. Before public launch, add proper authentication, database-backed users, CSRF protections, audit logs, and secure file storage.
- Railway free resources are limited; check the current Railway pricing page before launch.

## Run locally
Requires Node.js 20+.

```bash
npm install
cp .env.example .env
npm start
```

Open http://localhost:3000

## Termux
```bash
pkg update
pkg install nodejs-lts git
cd novapulse-ai
npm install
cp .env.example .env
nano .env
npm start
```
If `cp` or `nano` behaves differently in your Termux version, create `.env` using a text editor. Keep `OPENAI_API_KEY` blank to test demo mode.

## Enable live AI
1. Get an API key from your AI provider.
2. Add it to `.env` locally, or Railway → your service → Variables → `OPENAI_API_KEY`.
3. Optionally set `OPENAI_MODEL` and `OPENAI_IMAGE_MODEL` to models available to your account.
4. Restart/redeploy. Never put the API key in `public/` or browser JavaScript.

## Deploy to Railway using GitHub
1. Create a GitHub repository named `novapulse-ai`.
2. Upload these project files to the repository root.
3. In Railway, choose **New Project → Deploy from GitHub Repo** and select the repository.
4. Railway detects Node.js and runs `npm start`.
5. Open the service **Settings → Networking → Generate Domain**.
6. In **Variables**, set `ADMIN_PASSWORD` to a long unique password and set `OPENAI_API_KEY` only if you want live AI.
7. Check **Deployments → View Logs** if the service fails to start.

Do not commit `.env` or share API keys. Railway may have limited free credits/resources; the app itself can be tested in demo mode without an AI API key.
