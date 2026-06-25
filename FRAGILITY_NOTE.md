# Important: The "No-Key" Magic & Fragility

This project uses a unique method to provide high-quality video dubbing for free, but it's important to understand how it works and why it might stop working.

## How it works (The "Magic")

The dubbing engine doesn't use a standard API key. Instead, it communicates directly with Sarvam's internal dashboard backend (`dashboard.sarvam.ai`). 

1.  **No Authentication**: Currently, Sarvam's dashboard API responds to unauthenticated requests. The project piggybacks on this internal service.
2.  **Browser Mimicry**: The updated code uses browser-like headers to blend in with normal web traffic, reducing the chance of being flagged as a bot.
3.  **Parallel Processing**: By splitting videos into small chunks and processing them in parallel, we can bypass some of the rate limits intended for single users.

## Why it's fragile

Because this project uses an internal, undocumented backend rather than a public API, it is subject to several risks:

-   **API Changes**: If Sarvam updates their dashboard, the endpoint might change, breaking the script.
-   **Authentication Gating**: Sarvam could add a login requirement (cookies/tokens) to their dashboard API at any time. If they do, this "no-key" method will stop working instantly.
-   **Rate Limiting**: The 240s timeouts and "retry" loops you see are the server's way of protecting itself. If you hit these too hard, your IP might be temporarily blocked.

## What to do if it fails

If you see a **CRITICAL API ERROR**, it likely means the "free" door has been closed. 

1.  **Check the Error**: If the error says `HTTP 401` or `HTTP 403`, Sarvam has added authentication.
2.  **Wait and Retry**: If it's a `HTTP 429` (Rate Limit), just wait 10-15 minutes and try again.
3.  **Use Resume**: The project is designed to be resumed. If it fails midway, just run the script again on the same folder. It will skip everything that was already dubbed successfully.

*This project is provided for educational purposes. Use responsibly.*
