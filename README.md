=== Smart Site AI Chatbot ===
Contributors: tanvirapb
Tags: chatbot, ai, live chat, woocommerce, lead generation
Requires at least: 5.8
Tested up to: 7.1
Requires PHP: 7.4
Stable tag: 1.0.0
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

AI chat assistant for WordPress and WooCommerce. Answers from your own content, captures leads and books calls. Optional Gemini, OpenAI or Groq key.

== Description ==

Smart Site AI Chatbot adds a chat assistant to your site that answers visitor questions from your own published content, captures leads and bookings, and looks up WooCommerce order status.

It works without an API key. On activation the plugin builds a searchable index of your published pages, posts, products and other public content, and answers from that index. If you want generated answers instead, you can add your own key for Google Gemini, OpenAI, OpenRouter or Groq. No account, subscription or external service is required to use the plugin.

= What it does =

* **Answers from your own content.** A built-in index of your published pages, posts and products is searched on every question, and matching items are shown as cards with a link.
* **No API key required.** The built-in engine runs entirely on your own server. An API key is optional and only used if you add one.
* **Bring your own AI key.** Google Gemini, OpenAI, OpenRouter and Groq are supported. If a provider fails or is rate limited, the plugin falls back to the built-in engine so the chat keeps working.
* **Lead capture and booking.** Visitors can request a call, send a project inquiry or subscribe, either step by step in the conversation or through an inline form. Submissions are stored in WordPress and emailed to the address you choose.
* **WooCommerce order lookup.** Customers can check an order by entering the order ID and the billing email used at checkout. The email must match the order before any detail is shown.
* **Buttons that match your site.** The quick actions in the chat window are generated from what the plugin finds while indexing. A WooCommerce store gets Products and its busiest product categories by name, plus order tracking. An agency site gets Services, Our work and Pricing. A site that publishes regularly gets Articles. You can override them with your own list at any time.
* **Page-aware prompts.** Starter prompts and the greeting adapt on contact, pricing, portfolio, service and shop pages.
* **Conversation memory.** A conversation continues across page views and reloads for a period you choose, from 6 hours to 7 days.
* **Floating widget, shortcode or block.** Show the launcher site-wide, or embed an inline card with `[smart_site_ai_chatbot]` or the Smart Site AI Chatbot block.
* **Admin tools.** Review recent sessions by masked IP, manage captured leads, and export them to CSV.
* **Privacy options.** An optional consent notice can be shown before a visitor starts chatting, and visitor IP addresses are only ever displayed masked.

= Shortcode =

`[smart_site_ai_chatbot title="Ask our assistant" subtitle="Online"]`

= Developers =

The plugin exposes filters for the indexed post types (`ssac_indexed_post_types`), the index size (`ssac_index_item_limit`), question and answer extraction (`ssac_post_faqs`), whether the widget loads on a request (`ssac_enable_widget`), and IP resolution behind a proxy (`ssac_client_ip`). The `ssac_lead_saved` action fires after each submission.

== External services ==

This plugin works entirely on your own server by default. Nothing is sent anywhere unless you add an API key, or a visitor clicks the WhatsApp button you configured.

If you enter an API key for one of the providers below, the visitor's message, a short extract of the matching content from your site, and the business details you entered in the plugin settings are sent to that provider in order to generate a reply. Data is sent only while a visitor is chatting.

1. **Google Gemini** - used only if you enter a Gemini API key. Requests are sent to `https://generativelanguage.googleapis.com/`. See the [Google privacy policy](https://policies.google.com/privacy) and [Google APIs terms of service](https://developers.google.com/terms).
2. **OpenAI** - used only if you enter an OpenAI API key. Requests are sent to `https://api.openai.com/v1/chat/completions`. See the [OpenAI privacy policy](https://openai.com/policies/privacy-policy) and [OpenAI terms of use](https://openai.com/policies/terms-of-use).
3. **OpenRouter** - used only if you enter an OpenRouter API key. Requests are sent to `https://openrouter.ai/api/v1/chat/completions`. See the [OpenRouter privacy policy](https://openrouter.ai/privacy) and [OpenRouter terms](https://openrouter.ai/terms).
4. **Groq** - used only if you enter a Groq API key. Requests are sent to `https://api.groq.com/openai/v1/chat/completions`. See the [Groq privacy policy](https://groq.com/privacy-policy/) and [Groq terms of service](https://groq.com/terms-of-service/).
5. **WhatsApp** - used only if you enable the handoff option and enter a number. Clicking the button opens `https://wa.me/` in the visitor's browser. No data is sent by the plugin itself. See the [WhatsApp privacy policy](https://www.whatsapp.com/legal/privacy-policy).

== Privacy ==

The plugin stores a chat transcript for each visitor as a temporary record that expires after the retention period you set. Transcripts are linked to a random token stored in the visitor's browser, not to their IP address. IP addresses are used only for rate limiting and are shown masked in the admin screens. Leads, bookings and subscriptions you capture are stored as private records in your database and are removed when the plugin is deleted.

== Installation ==

1. Upload the plugin files to `/wp-content/plugins/smart-site-ai-chatbot`, or install it through the Plugins screen in WordPress.
2. Activate the plugin through the Plugins screen.
3. Go to **AI Chatbot** in the admin menu.
4. Your content is indexed automatically. Set your assistant name, colours and business profile, and add an API key only if you want generated answers.

== Frequently Asked Questions ==

= Does it work without an API key? =

Yes. The built-in engine indexes your published content and answers from it, shows matching pages and products as cards, captures leads and bookings, and looks up WooCommerce orders. No external service is involved.

= Can I use a free API key? =

Yes. Google AI Studio, OpenRouter and Groq all offer free tiers, and a paid OpenAI key works as well. If a provider is unavailable or rate limited, the plugin falls back to the built-in engine automatically.

= Does the conversation survive a page reload? =

Yes. The conversation is stored against a random token in the visitor's browser and kept on the server for the retention period you choose: 6 hours, 12 hours, 24 hours, 48 hours or 7 days.

= How does the WooCommerce order lookup work? =

The visitor is asked for an order ID and the billing email used at checkout. The plugin only shows the order status, date, items and total when that email matches the order.

= Is any visitor data sent to an external service? =

Only if you add an API key. See the External services section above for exactly what is sent and to whom.

= Where do the buttons in the chat window come from? =

They are generated from your own content when the site is indexed, so a shop shows its products and busiest product categories while an agency shows its services and portfolio. To set your own instead, enter one prompt per line under Quick actions and starter prompts. The settings screen shows which buttons are currently generated for your site.

= Can I open the assistant from a link or menu item? =

Yes. Link to `#ssac-open` to open the assistant, or to `#ssac-ask=Your%20question` to open it and ask that question straight away. This works from a menu item, a button or any link on the page.

= How do I stop the widget loading on certain pages? =

Return false from the `ssac_enable_widget` filter for the requests you want to exclude.

== Screenshots ==

1. The assistant answering a question with matching pages from the site shown as cards.
2. Booking a call without leaving the conversation, using the inline form.
3. Checking a WooCommerce order from the chat window.
4. The settings screen: appearance, session retention and feature toggles.
5. Captured leads and bookings, with one-click CSV export.

== Changelog ==

= 1.0.0 =
* Initial release.

== Upgrade Notice ==

= 1.0.0 =
Initial release.
