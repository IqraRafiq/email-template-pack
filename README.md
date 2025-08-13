# Email Template Pack

Production‑ready, responsive HTML email templates in three formats (raw HTML, Mailchimp, Klaviyo). Built for high compatibility across Gmail, Outlook, iOS/Android.

## Folders
- `welcome_email/html/` – ESP-agnostic HTML (copy/paste into any provider)
- `welcome_email/mailchimp/` – Mailchimp build with mc:edit regions and merge tags
- `welcome_email/klaviyo/` – Klaviyo build with Liquid tags and unsubscribe macro
- `password_reset/html/`, `password_reset/mailchimp/`, `password_reset/klaviyo/`
- `email_activation/html/`, `email_activation/mailchimp/`, `email_activation/klaviyo/`
- `support_request/html/`, `support_request/mailchimp/`, `support_request/klaviyo/`
- `payment_confirmation/html/`, `payment_confirmation/mailchimp/`, `payment_confirmation/klaviyo/`
- `feature_announcement/html/`, `feature_announcement/mailchimp/`, `feature_announcement/klaviyo/`
- `feedback_email/html/`, `feedback_email/mailchimp/`, `feedback_email/klaviyo/`

## Usage
- HTML: Import as raw HTML in your ESP. Replace links, addresses, and brand name.
- Mailchimp: Import as a template. Edit regions via the editor. Merge tags used:
  - `*|MC_PREVIEW_TEXT|*`, `*|CURRENT_YEAR|*`, `*|LIST:ADDRESS|*`, `*|UNSUB|*`
  - For password reset: `*|RESET_LINK|*` (create a campaign/template variable for the button URL)
  - For account activation: `*|ACTIVATION_LINK|*` (create a campaign/template variable for the button URL)
  - For support request: `*|TICKET_ID|*`, `*|SUBMIT_DATE|*`, `*|RESPONSE_TIME|*`, `*|TICKET_URL|*`
  - For payment confirmation: `*|TRANSACTION_ID|*`, `*|PAYMENT_METHOD|*`, `*|DATE|*`, `*|BILLING_URL|*`
- Klaviyo: Import as HTML template. Merge tags used:
  - `{{ now | date: "%Y" }}`, `{{ organization.full_address }}`, `{% unsubscribe %}`
  - For password reset: `{{ reset_link }}` (set as a variable/flow property for the button URL)
  - For account activation: `{{ activation_link }}` (set as a variable/flow property for the button URL)
  - For support request: `{{ ticket_id }}`, `{{ submitted_on }}`, `{{ response_time }}`, `{{ ticket_url }}`
  - For payment confirmation: `{{ plan_name }}`, `{{ amount_paid }}`, `{{ transaction_id }}`, `{{ payment_method }}`, `{{ date }}`, `{{ billing_url }}`

## Responsive/Dark Mode
- Mobile responsive with fluid tables and inline styles
- Transparent PNG confetti assets (`confetti_header.png`, `confetti_bottom.png`) work in light/dark themes
- Outlook desktop background images supported via VML fallbacks
- CTA buttons use bulletproof VML for rounded corners in Outlook

## Adding New Templates
1. Start from `welcome_email/html/welcome_email.html` as a base.
2. Duplicate into `mailchimp/` and add mc:edit + Mailchimp merge tags.
3. Duplicate into `klaviyo/` and convert merge tags to Klaviyo variables.
4. Keep background images at 600px wide canvases; use transparent PNGs.
5. Test in Gmail (web/mobile), Outlook desktop (Windows, Mac), Apple Mail, iOS/Android. Optional: Litmus/Email on Acid.

## Customization Checklist (per template)
- Replace brand name and `assets/images/logo.png`
- Update CTA links and variables (see per‑ESP merge vars above)
- Replace social URLs and footer address/company info
- Swap illustration sizes if desired (common sizes: 140–380px, exported @2x)
- Host images on your CDN for production and update URLs

## Assets and Sizes
- Header/Bottom confetti: `confetti_header.png`, `confetti_bottom.png` (canvas 600px wide)
- Illustrations: 140–380px display width, export @2x (e.g., 280–760px)
- Emojis: 64px (`happy_emoticon.png`, `neutral_emoticon.png`, `sad_emoticon.png`)

## Compatibility
- Tested with table‑based layout; no web fonts; inline CSS
- Works in: Gmail, Apple Mail, Outlook (with VML), iOS Mail, Android Gmail
- Uses standard ALT text; decorative elements use background images where appropriate

## Packaging for Envato
1. Include the following in your ZIP:
   - `welcome_email/`, `password_reset/`, `email_activation/`, `support_request/`, `payment_confirmation/`, `feature_announcement/`, `feedback_email/`
   - `assets/images/` (PNG assets referenced by templates)
   - `README.md` (this file)
2. Provide screenshots previews for each template (optional but recommended).
3. Version your release (e.g., `v1.0.0`) and include a short changelog if you update files later.

## License/Notes for Buyers
- Replace all placeholder links, addresses, and brand assets with your own.
- Ensure unsubscribe and address blocks comply with your ESP and local laws.
- Images provided for demo; host on your own CDN for production deliverability.

## Notes
- Keep all CSS inline. Avoid web fonts and complex CSS.
- Images are hosted via GitHub raw URLs for testing; use your CDN in production.
