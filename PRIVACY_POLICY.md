# Privacy Policy for FinalDraft

**Last Updated:** January 10, 2026

## Overview

FinalDraft ("the Extension") is a browser extension that helps users draft email replies using AI. This privacy policy explains how we handle your data.

## Data We Access

The Extension accesses the following data to function:

1. **Email Content** - We read email thread content from Gmail and Plusvibe to generate contextually appropriate reply drafts.

2. **Gmail API Access** - We use Gmail API to:
   - Read email threads (to understand conversation context)
   - Create draft replies (to save generated drafts)
   - List inbox messages (for batch draft generation)
   - Read sent messages (to match drafts with final sent emails for quality improvement)

3. **PlusVibe/Pipl.ai Data** - When using PlusVibe, we intercept network responses to extract:
   - Email thread content
   - Contact information
   - Conversation context

4. **User Settings** - We store your preferences locally, including:
   - OpenAI API key (stored locally in your browser)
   - Assistant ID configuration
   - Custom prompts
   - Auto-show preferences

## How We Use Your Data

- **Email content** is sent to OpenAI's API to generate draft replies
- **Error data** is sent to Sentry for crash reporting and debugging
- **Training samples** may be collected to improve AI draft quality (see Training Data section)
- **API keys are stored locally** in your browser and never transmitted to us

## Training Data Collection

To improve the quality of AI-generated drafts, the Extension may collect:

- **Draft-to-sent comparisons**: When you send an email that was drafted by FinalDraft, we may capture both the original draft and your final sent version to understand how to improve future drafts.
- **What we collect**: 
  - Email content, subject lines, and metadata (timestamps, thread IDs)
  - User identification: Your email address and Google account ID (to associate training data with users for personalized improvements)
- **What we DON'T collect**: Attachments, API keys, or personal account credentials
- **Storage**: Training samples are stored securely in Supabase (cloud database)
- **Purpose**: Solely to improve AI draft generation quality and provide personalized email drafting
- **Retention**: Training samples are automatically deleted after 30 days

### Opting Out of Training Data

Training data collection helps improve the Extension for all users. If you prefer not to participate, contact crb1898@gmail.com to opt out.

## Third-Party Services

The Extension uses the following third-party services:

| Service | Purpose | Data Shared | Privacy Policy |
|---------|---------|-------------|----------------|
| **OpenAI** | Generate email drafts | Email content, conversation context | [openai.com/privacy](https://openai.com/privacy/) |
| **Google Gmail API** | Read/write emails and drafts | Email access via OAuth | [policies.google.com/privacy](https://policies.google.com/privacy) |
| **Sentry** | Error tracking and crash reporting | Error messages, stack traces, browser info | [sentry.io/privacy](https://sentry.io/privacy/) |
| **Supabase** | Training data storage | Anonymized email samples | [supabase.com/privacy](https://supabase.com/privacy) |

## Error Reporting (Sentry)

When errors occur, we automatically send diagnostic information to Sentry, including:

- Error messages and stack traces
- Browser type and version
- Extension version
- Timestamps

This data helps us identify and fix bugs. **No email content is included in error reports.**

## Data Storage

- **Local storage**: Settings and API keys are stored locally in your browser using Chrome's `chrome.storage.local` API
- **Cloud storage**: Training samples (if collected) are stored in Supabase with encryption at rest
- **No unauthorized access**: We do not sell, share, or provide access to your data to third parties except as described above

## Data Security

- API keys are stored locally and never leave your browser
- All API communications use HTTPS encryption
- Training data is encrypted in transit and at rest
- Supabase database access is restricted to authorized personnel only
- Sentry data is automatically purged after 90 days

## Your Rights

You can:
- **Uninstall** the extension at any time to stop all data access
- **Clear stored data** via Chrome's extension settings
- **Revoke Gmail API access** via your [Google Account settings](https://myaccount.google.com/permissions)
- **Opt out of training data collection** by contacting crb1898@gmail.com
- **Request data deletion** by contacting crb1898@gmail.com

## Children's Privacy

This Extension is not intended for use by children under 13 years of age. We do not knowingly collect personal information from children.

## Contact

For privacy questions or data requests, contact: **crb1898@gmail.com**

## Changes to This Policy

We may update this policy occasionally. Significant changes will be noted in the Extension's changelog. Continued use of the Extension after changes constitutes acceptance of the updated policy.

---

*This privacy policy is effective as of January 10, 2026.*
