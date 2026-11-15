# kite-callback

A one-page relay for logging in to Kite Connect from a phone, used by a private trading-research
project (data only; it never places orders).

After you log in to Kite (password and TOTP, typed by hand), Kite redirects to this page with a
one-time `request_token`. The page hands it to **your own** Telegram bot as
`/start k<request_token>_<state>` and does nothing else: no network calls, no storage, no
cookies, no third-party code. It removes the token from the address bar and history at once.

The token works once, expires within minutes, and is useless without the Kite API secret, which
only the bot's server has. The bot accepts it only for the login link it issued itself (the
random `state`), within 30 minutes, from its owner's chat.

The page holds no secret and no account name: the bot's username arrives in the login link.
