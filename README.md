# nuno store — Telegram-ready

This version sends a Telegram message whenever Nuno redeems a reward.

## Important security rule
NEVER put `TELEGRAM_BOT_TOKEN` inside `index.html`.
The token belongs only in the server environment.

## Deploy on Vercel
1. Put this project in a GitHub repository.
2. Import the repository into Vercel.
3. In Vercel: Project Settings -> Environment Variables.
4. Add:
   - `TELEGRAM_BOT_TOKEN` = the token from BotFather
   - `TELEGRAM_CHAT_ID` = `6165333383`
5. Redeploy.

The browser calls `/api/order`.
The server calls Telegram's official Bot API `sendMessage`.
The token never reaches the browser.

## Telegram prerequisite
Open your bot chat and press Start before testing. Telegram's Bot API sends the message to the `chat_id` supplied to `sendMessage`.

## Current limitation
The points/orders are still browser-localStorage in this prototype.
For a true production site, the order and point deduction must be moved to a database/server transaction before the Telegram notification is sent.
