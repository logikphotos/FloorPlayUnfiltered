# FloorplayUnfiltered — Sexual Comfort Quiz

### Deployment & Setup Guide

*By Ali Schum, MS OTR/L · @FloorplayUnfiltered*

---

## What This Is

A single-file, self-contained quiz that:

- Walks visitors through 6 questions
- Captures their name + email
- **Sends Ali a notification** with their answers and result type
- **Emails the visitor** their personalized result automatically
- Displays the result on-screen at the end

No backend server needed. No subscription required on the free tier.

---

## Files

```
floorplay-quiz/
├── index.html   ← The entire quiz (all CSS, JS, and HTML in one file)
└── README.md    ← This setup guide
```

---

## Step 1 — Formspree is Already Connected ✅

The quiz is wired to your live Formspree form at:

```
https://formspree.io/f/mqpqkbgy
```

No code changes needed. The Formspree Ajax SDK (`@formspree/ajax`) is loaded from CDN and handles all submissions automatically — no bundler, no npm, no server.

**What to confirm in your Formspree dashboard:**

1. Log in at [https://formspree.io](https://formspree.io)
2. Open your `FloorplayUnfiltered Quiz` form
3. Under **Settings → Notifications**, confirm your email address is set (this is where Ali receives submission alerts)
4. Free tier: 50 submissions/month. Upgrade to Basic ($10/mo) for 1,000/mo.

---

## Step 2 — Set Up the Autoresponder Email (Formspree)

This is the email your quiz takers receive with their results.

1. In your Formspree dashboard, open your form
2. Click **Integrations** → **Email Notifications** → **Add Autoresponder**
3. Set **Reply To field** to `email` (matches the field name in the form)
4. Use this subject line:

   ```
   Your sexual comfort quiz result — FloorplayUnfiltered
   ```
5. Paste the email body below (edit as needed):

---

**Autoresponder Email Template:**

```
Hi {{firstName}},

Your quiz result: {{resultHeading}}

{{resultType}}

---

This result is not a diagnosis — it simply highlights an area that may be worth exploring, whether that's pelvic floor tension, nervous-system protection, arousal and lubrication, communication, or other health factors.

I created Understanding Pain with Sex to help you explore:

• Pelvic floor tension and relaxation
• Nervous-system regulation
• Curiosity instead of fear or self-judgment
• Communication and consent scripts
• Lubrication, positioning, and pacing
• Non-penetrative intimacy
• Gentle strategies for graded exploration
• When to seek professional support

Get the guide here: [INSERT YOUR PURCHASE LINK]

Your body does not have to be forced into comfort. The goal is more choice, safety, curiosity, and pleasurable experiences that work for you.

Warmly,
Ali Schum, MS OTR/L
FloorplayUnfiltered
@FloorplayUnfiltered
```

---

## Step 3 — View Submissions (Ali's Dashboard)

Every time someone completes the quiz and enters their email:

1. Log in to **[https://formspree.io](https://formspree.io)**
2. Click your form → **Submissions**
3. You'll see each entry with:
   - First name
   - Email address
   - Result type (Mostly A / B / C / Mixed)
   - Result heading
   - All 6 individual answers (as a JSON object)
   - Submission timestamp
4. You can also **export to CSV** (Submissions → Export) to build your email list in Mailchimp, ConvertKit, Flodesk, etc.

---

## Step 4 — Export to Your Email Platform (Optional)

To sync leads into Mailchimp, Flodesk, ConvertKit, or another platform:

**Option A — Zapier (easiest)**

1. Go to zapier.com → New Zap
2. Trigger: Formspree → New Submission
3. Action: Add Subscriber to Mailchimp / Flodesk / ConvertKit
4. Map fields: `firstName` → First Name, `email` → Email, `resultType` → Tag

**Option B — Formspree native integrations** Formspree Pro ($8/mo) has native Mailchimp and ConvertKit integrations in the dashboard.

**Option C — Manual CSV export** Formspree free tier → Submissions → Export CSV → import manually.

---

## Step 5 — Deploy to GitHub Pages (Free Hosting)

This puts the quiz at a public URL you can link from Instagram.

1. Go to **github.com** and sign in (or create a free account)
2. Click **New Repository**
   - Name it `floorplay-quiz` (or anything you like)
   - Set it to **Public**
   - Click Create
3. Upload `index.html` to the repository
   - Click **Add file** → **Upload files**
   - Drag in `index.html` → Click **Commit changes**
4. Go to **Settings** → **Pages** (in the left sidebar)
5. Under **Source**, choose:
   - Branch: `main`
   - Folder: `/ (root)`
   - Click **Save**
6. After about 60 seconds, your quiz will be live at:

   ```
   https://YOUR-GITHUB-USERNAME.github.io/floorplay-quiz/
   ```
7. You can share this URL in your Instagram bio, link-in-bio tool (Linktree, etc.), or DMs.

---

## Customizing the Guide Purchase Link

In `index.html`, find this line:

```html
<a href="#" class="btn-cta" id="guideCTA">Get the complete guide</a>
```

Replace `#` with your actual product link (Gumroad, Shopify, Stan Store, etc.):

```html
<a href="https://your-store.gumroad.com/l/your-guide" class="btn-cta" id="guideCTA">Get the complete guide</a>
```

---

## Testing Before Launch

Before sharing publicly:

1. Open `index.html` in your browser (double-click the file)
2. Complete the quiz with a test email address
3. Confirm you receive both:
   - **Your notification** (from Formspree to Ali's email)
   - **The autoresponder** (to your test email)
4. Check the Formspree dashboard → Submissions to confirm the entry appears
5. Only then share the GitHub Pages URL

---

## Free Tier Limits

| Service | Free Limit | Notes |
| --- | --- | --- |
| Formspree | 50 submissions/month | Upgrade to Basic ($10/mo) for 1,000/mo |
| GitHub Pages | Unlimited | No limits on visitors |
| Email autoresponder | Included with Formspree | Per submission |

If the quiz goes viral and you hit 50 submissions fast, Formspree Basic ($10/month) handles up to 1,000.

---

## Questions?

Reach out to your developer (Darius) or Formspree support at [support@formspree.io](mailto:support@formspree.io).

© 2026 Ali Schum / FloorplayUnfiltered