# AVS luxury automobiles

The storefront is a static `index.html` suitable for GitHub Pages. It welcomes visitors to explore the car collection at their own pace and contact AVS by phone. Its AVS Smart Guide is a lightweight, rule-based vehicle recommender that runs in the browser. It matches visitor requests to the collection's vehicle types, model names, and listed specifications; it does not use a language model, require an API key, or send chat messages to a server.

## Publish the static site

In the repository's **Settings → Pages**, choose **Deploy from a branch**, select `main` and the `/ (root)` folder, then save. GitHub will publish `index.html` at the Pages URL shown in those settings.

## Optional OpenAI endpoint

The repository retains `api/concierge.js` as an optional server-side integration for a future generative concierge. It is not called by the current storefront. To enable and connect it, deploy the repository to Vercel, configure `OPENAI_API_KEY` and `AVS_ALLOWED_ORIGIN` in Vercel's environment settings, and deliberately update the frontend integration. Never put a real API key in the HTML or repository.

The contact options use the phone number displayed on the site. Prices are available on request, and the AVS team must confirm current vehicle availability and pricing.
