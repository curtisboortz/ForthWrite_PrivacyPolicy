# Privacy Policy for FinalDraft

**Last updated:** April 21, 2026

> The canonical, always-current version of this policy lives at
> **https://finaldraft.dev/privacy**. This Markdown copy is kept byte-for-byte
> in sync with that page for the convenience of Chrome Web Store reviewers,
> Google OAuth verification reviewers, and anyone reading the source repo.

---

## 1. Overview

FinalDraft ("we," "our," or "us") is an AI-powered email drafting tool. This
policy explains how we collect, use, and protect your information when you use
our Chrome extension and web application at finaldraft.dev.

## 2. Information We Collect

We collect the following categories of information:

- **Account information:** Email address and authentication data when you sign up.
- **Subscription data:** Plan type, billing interval, and payment processor IDs (handled by Stripe).
- **Usage data:** Draft generation counts for tier rate limiting and aggregate, anonymous engagement metrics.
- **Gmail content read by the Chrome extension:** When the extension is installed and signed in to a Google account, it reads (a) the thread you are currently viewing so it can generate a contextually relevant draft, and (b) the inbox-thread list (using the read-only filter `in:inbox is:unread`) at most once every 60 seconds so it knows which new conversations to draft for. We do not read Gmail labels, attachments, archived mail, or any folder other than the inbox. Thread content is never persisted to our servers; it is held in memory only for the duration of the draft request.
- **Email content during draft generation:** When you generate a draft, the relevant thread content is sent to your configured AI provider (BYOK) or, on the Free tier and AI-included plans, through our backend proxy to OpenAI. We do not retain the thread content after the response is returned.
- **Gmail send-as aliases:** When you connect a Google account on the web app, we call `users.settings.sendAs.list` once to enumerate the alias addresses configured on that account so the right "From" identity can be attached to drafts. We store only the alias email address and display name, never the alias signature HTML.
- **Sent-email snippets for voice matching (Standard and Pro):** When you enable voice-matching capture in the extension, snippets of emails you send (the body of your reply, the surrounding thread, and metadata like timestamps and platform) are stored in our database so we can learn your writing voice. On Standard, this powers a private writing-style profile injected into the model. On Pro, snippets are additionally embedded so the model can retrieve your past similar emails at draft time. Capture is off by default until you enable it.
- **Historical email backfill (Pro only, opt-in):** If you choose to import historical emails from the Training Dashboard, we read up to the last six months of your sent mail via Gmail or Microsoft OAuth and store the same snippet-level information described above. We do not read inbox or non-sent folders, and the import is one-shot. We do not poll your mailbox in the background.
- **OAuth tokens for connected inboxes:** When you connect a Gmail or Outlook account on the web, we store the access and refresh tokens issued by the provider, encrypted at rest using AES-256-GCM with per-user data-encryption keys wrapped by a master key held only on our servers. Tokens are used solely to support the features you have asked for (currently: historical email backfill; in the future: high-confidence send-from-web notifications).

## 3. How We Use Your Information

- To provide and maintain the FinalDraft service.
- To manage your subscription and billing.
- To enforce rate limits on the free tier.
- To communicate important service updates.
- To improve the product based on aggregate, anonymous usage patterns.
- To learn your writing voice when you enable voice-matching capture, by summarizing your sent-email snippets into a private writing-style profile (Standard and Pro) and, on Pro, by embedding those snippets so the model can retrieve your most relevant past replies at draft time. Your snippets are never used to train shared or third-party models, and are never combined with another user's data.

## 4. API Keys and AI Providers

When you provide your own API key (BYOK), it is stored locally in your browser
via Chrome's storage API. Your key is sent directly from your browser to the AI
provider (OpenAI, Anthropic, Google, xAI, etc.) and never passes through our
servers. For free-tier users without an API key, draft requests are routed
through our backend proxy, where email content is sent to OpenAI to generate
drafts. This content is not stored after the response is returned.

## 5. Data Storage and Security

Account and subscription data is stored in a secure Supabase (PostgreSQL)
database with row-level security enabled. Payment information is handled
entirely by Stripe and never touches our servers. All data is transmitted over
HTTPS.

Sent-email snippets captured for voice matching are stored in the same Supabase
database, scoped per user, and accessible only to your own account. OAuth
tokens for connected Gmail and Outlook accounts are encrypted at rest using
AES-256-GCM envelope encryption with per-user data-encryption keys; the master
key is held only on our application servers and is never written to the
database.

## 6. Third-Party Services

- **Stripe:** Payment processing. Subject to [Stripe's Privacy Policy](https://stripe.com/privacy).
- **Supabase:** Database and authentication hosting.
- **Sentry:** Error tracking (no email content is sent to Sentry).
- **AI Providers:** OpenAI, Anthropic, Google, xAI, and others. Subject to their respective privacy policies.

## 7. Data Retention

Account and subscription data is retained while your account is active. Draft
usage counters reset weekly.

Sent-email snippets captured for voice matching are retained for as long as you
keep voice-matching capture enabled, so we can keep your writing-style profile
current. You can disable capture at any time from the extension options page,
and you can request deletion of all captured snippets by emailing us. Your
account, subscription, and writing-style profile remain intact unless you also
request full account deletion.

You can request deletion of your account and all associated data (including
snippets, the writing-style profile, OAuth tokens, and any embeddings) by
emailing us.

## 8. Your Rights

You have the right to access, correct, or delete your personal data. You can
export your data or request account deletion at any time by contacting us at
**support@finaldraft.dev**.

You can also disable voice-matching capture at any time from the extension
options page, and disconnect any linked Gmail or Outlook inbox from the
Settings tab in your dashboard. Disconnecting an inbox revokes our stored
OAuth tokens for that account immediately.

## 9. Google API Services User Data Policy

FinalDraft's use and transfer to any other app of information received from
Google APIs will adhere to the
[Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy),
including the **Limited Use** requirements. Specifically:

- We do not use Gmail data for serving advertisements.
- We do not allow humans to read your Gmail data, except (a) with your explicit consent for specific messages, (b) where necessary for security purposes such as investigating abuse, (c) to comply with applicable law, or (d) where the data is aggregated and used for internal operations in accordance with applicable privacy laws.
- We do not transfer Gmail data to others except as necessary to provide or improve user-facing features that are prominent in the application's user interface, to comply with applicable law, or as part of a merger, acquisition, or sale of assets with appropriate notice to users.
- We do not use Gmail data to develop, improve, or train generalized or non-personalized AI or machine-learning models. The voice-matching writing-style profile and Pro retrieval embeddings described above are user-scoped, used only to draft email *for that same user*, and never combined with another user's data or shared with any third party.

The specific Google OAuth scopes FinalDraft requests, and the user-facing
feature each scope powers:

- **`gmail.readonly`** — reading the open Gmail thread to build draft context; polling the inbox-thread list (read-only, `in:inbox is:unread`) so the extension knows which new conversations to draft for; reading sent-mail snippets when you opt into voice capture or one-shot historical backfill.
- **`gmail.compose`** — creating, updating, and deleting *only the drafts FinalDraft itself authored*. We never modify or delete drafts you wrote by hand.
- **`gmail.settings.basic`** (web only) — enumerating your send-as aliases via `users.settings.sendAs.list` so the right "From" identity is attached when drafting. No other settings are read or written.
- **`userinfo.email`** — identifying the authenticated Google account so the extension can match it to your FinalDraft subscription.

## 10. Changes to This Policy

We may update this policy from time to time. We will notify you of material
changes via email or a notice on the website.

## 11. Contact

For privacy-related questions, contact us at **support@finaldraft.dev**.
