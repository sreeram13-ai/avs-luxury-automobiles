# avs-luxury-automobiles

The frontend is a static `index.html` suitable for GitHub Pages. The AI concierge uses a Vercel serverless function at `api/concierge.js`; the browser never receives the OpenAI API key.

## Publish the static site

In the repository's **Settings → Pages**, choose **Deploy from a branch**, select `main` and the `/ (root)` folder, then save. GitHub will publish `index.html` at the Pages URL shown in those settings.

## Configure the concierge

1. Deploy this repository to Vercel so it can run the `api/concierge.js` function (GitHub Pages serves only the static frontend).
2. In the Vercel project settings, add these environment variables for the production environment:
   - `OPENAI_API_KEY`: your OpenAI API key. Add it in Vercel's environment settings; never put a real key in this repository or in the HTML.
   - `AVS_ALLOWED_ORIGIN`: the exact website origin, such as `https://your-username.github.io` (no path or trailing slash). For a custom domain, use its `https://` origin instead.
   - `OPENAI_MODEL` (optional): model name; defaults to `gpt-4.1-mini`.
3. After deploying, set the `avs-concierge-endpoint` meta tag in `index.html` to the deployed function URL, for example `https://your-project.vercel.app/api/concierge`, then publish the updated HTML to GitHub Pages.
4. In Vercel, configure usage limits and rate limiting before promoting the endpoint to production. The origin check is a browser CORS restriction, not authentication; a public endpoint can still receive direct requests.

The function sends the chat to OpenAI's Responses API with `store: false`, restricts requests to the configured origin, and bounds the message sizes and conversation length. The concierge only receives chat messages; it does not receive the enquiry form's contact details. Users are told that messages are processed by OpenAI.

To preview the static page locally, opening `index.html` shows the concierge UI, but AI replies require the deployed function and matching site origin. The sample enquiry form remains a preview and does not submit sales leads.
