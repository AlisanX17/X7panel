# X7 Panel

VPN management panel built with Flask, SQLite, Nginx and Xray.

## Railway deployment
Set ADMIN_USER, ADMIN_PASS, and a long random SECRET_KEY in Railway Variables. Set APP_BASE_URL to the public HTTPS URL of the service for Telegram webhooks. Attach a persistent Railway Volume mounted at /data and set DB_PATH=/data/users.db so SQLite data survives redeployments. Do not mount the volume over /app because that directory contains the application files.

## X7 Bot Factory
The bot builder connects Telegram bots to this panel's own SQLite users table and Xray core. Each bot has its own administrator ID, card number and sales plans. Customers choose a plan, pay by card transfer, and submit a receipt. The configured bot administrator reviews the receipt; only approval creates the VPN user in X7.

Bot tokens are encrypted at rest using a key derived from SECRET_KEY. Keep this secret stable and private. Never paste bot tokens into public issues or source files.

## Security
Change the default panel login immediately. Verify transfers independently before approving receipts.