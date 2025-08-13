# Email Template Pack

This pack provides production-ready, responsive HTML email templates in multiple ESP formats.

## Folders
- `welcome_email/html/` – ESP-agnostic HTML (copy/paste into any provider)
- `welcome_email/mailchimp/` – Mailchimp build with mc:edit regions and merge tags
- `welcome_email/klaviyo/` – Klaviyo build with Liquid tags and unsubscribe macro
- `password_reset/html/`, `password_reset/mailchimp/`, `password_reset/klaviyo/`
- `email_activation/html/`, `email_activation/mailchimp/`, `email_activation/klaviyo/`

## Usage
- HTML: Import as raw HTML in your ESP. Replace links and addresses.
- Mailchimp: Import as a template. Edit regions via the editor. Merge tags used:
  - `*|MC_PREVIEW_TEXT|*`, `*|CURRENT_YEAR|*`, `*|LIST:ADDRESS|*`, `*|UNSUB|*`
  - For password reset: `*|RESET_LINK|*` (create a campaign/template variable for the button URL)
  - For account activation: `*|ACTIVATION_LINK|*` (create a campaign/template variable for the button URL)
- Klaviyo: Import as HTML template. Merge tags used:
  - `{{ now | date: "%Y" }}`, `{{ organization.full_address }}`, `{% unsubscribe %}`
  - For password reset: `{{ reset_link }}` (set as a variable/flow property for the button URL)
  - For account activation: `{{ activation_link }}` (set as a variable/flow property for the button URL)

## Responsive/Dark Mode
- Mobile responsive with fluid tables and inline styles
- Transparent confetti images adapt in dark mode
- Outlook (desktop) background images supported via VML fallbacks
- CTA buttons include bulletproof VML fallback for rounded corners in Outlook

## Adding New Templates
1. Start from `welcome_email/html/welcome_email.html` as a base.
2. Duplicate into `mailchimp/` and add mc:edit + Mailchimp merge tags.
3. Duplicate into `klaviyo/` and convert merge tags to Klaviyo variables.
4. Keep images at 600px width canvases for backgrounds; use PNG with transparency.
5. Test in Gmail, Outlook, iOS/Android, and (optionally) Litmus/Email on Acid.

## Customization Checklist (per template)
- Replace brand name and `logo.png` with your assets
- Update CTA links (`*|RESET_LINK|*` for Mailchimp, `{{ reset_link }}` for Klaviyo)
- Swap social URLs and footer address
- Optionally host images on your CDN (update `assets/images/*` URLs)

## Notes
- Keep all CSS inline. Avoid web fonts and complex CSS.
- Images are hosted via GitHub raw URLs for testing; use your CDN in production.
