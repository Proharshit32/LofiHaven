# Lofi Haven
No accounts. Open the site, create a room, copy the link, study together.

## Run locally (Windows, Node 18+)
    npm install
    npm run api      # terminal 1: local room server (wrangler dev, port 8787)
    npm run dev      # terminal 2: app at http://localhost:5173 (use the Network URL on your phone)

## Calls
Public meet.jit.si is test-only for embedding (5-minute cap, no anonymous embeds). Choose one:
1. JaaS free tier (https://jaas.8x8.vc): create an app + API key, copy `.dev.vars.example` to `.dev.vars`.
   Your private key must be PKCS#8 ("BEGIN PRIVATE KEY"); if it says "BEGIN RSA PRIVATE KEY":
   `openssl pkcs8 -topk8 -nocrypt -in key.pk -out key.pk8`
2. Self-hosted Jitsi: set `JITSI_DOMAIN` in wrangler.toml.
Camera/mic/screen share need https or localhost.

## Deploy (free Cloudflare tier)
    npm run build && npx wrangler deploy
    npx wrangler secret put JAAS_APP_ID   (and JAAS_KID, JAAS_PRIVATE_KEY)
Add a Cloudflare rate-limiting rule for POST /api/rooms (dashboard) to limit room creation per IP.
