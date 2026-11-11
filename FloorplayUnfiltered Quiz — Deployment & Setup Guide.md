# FloorplayUnfiltered — Sexual Comfort Quiz

### Deployment & Setup Guide

*By Ali Schum, MS OTR/L · @FloorplayUnfiltered*

---

## What this project does

This repo contains the public-facing quiz and post-purchase confirmation flow for FloorplayUnfiltered.

The current experience works like this:

1. A visitor opens the quiz page.
2. They complete six questions with a progress bar and answer selections.
3. After the final question, the app asks for first name and email.
4. The form is submitted to Formspree with the quiz result + answers.
5. Formspree sends a notification to Ali and can trigger the user’s autoresponder email.
6. The visitor is shown a result page with a call-to-action for the guide.
7. After purchase, they reach a confirmation page with a PDF download button.

This is intentionally lightweight: the quiz is static HTML, CSS, and JavaScript with no backend required for the basic flow.

---

## Files in the project

```text
FloorPlayUnfiltered/
├── quiz.html              # main quiz experience
├── Confirmation.html      # purchase confirmation/download page
├── FloorplayUnfiltered Quiz — Deployment & Setup Guide.md
└── README.md              # project summary / repo landing page
```

---

## Current user flow

### Quiz flow

- Intro screen explains the six-question assessment
- Question 1 through Question 6 each gather one answer
- Progress bar updates as the user moves through the survey
- Final result is categorized as Mostly A, Mostly B, Mostly C, or Mixed
- The app captures the person’s first name and email before showing the result
- The result page includes a CTA to purchase the complete guide

### Submission flow

The Formspree submission includes:

- `firstName`
- `email`
- `resultType`
- `resultHeading`
- `answers`
- `submittedAt`

This gives Ali a full record of the visitor’s result and the question-by-question responses.

### Purchase flow

Once the visitor clicks the guide CTA, they are routed to the payment page. After successful purchase, they land on `Confirmation.html`, where they can access the guide PDF or download link.

---

## Recent updates

The project has recently been updated to reflect the live conversion flow:

- Added a clearer six-question quiz structure
- Added a progress indicator and refined result presentation
- Added the name/email capture step before result delivery
- Added result data fields to the Formspree payload for lead tracking and segmentation
- Added a dedicated confirmation page for guide delivery
- Kept the app entirely front-end static and easy to deploy

---

## Formspree setup

The form is wired to a live Formspree form and should be configured in the dashboard.

### Confirm these settings

1. Log in to https://formspree.io
2. Open the relevant form linked to this quiz
3. Under Settings → Notifications, confirm Ali’s email is listed
4. Under Integrations, set up the autoresponder email if desired
5. Verify the submission fields match the front-end input names in `quiz.html`

### Important note

The front-end form currently posts the following key values:

- `firstName`
- `email`
- `resultType`
- `resultHeading`
- `answers`
- `submittedAt`

If your Formspree dashboard is missing a field or the autoresponder is not firing, confirm the hidden input names and the connected form settings.

---

## Autoresponder email template

Use an autoresponder in Formspree with a subject such as:

```text
Your sexual comfort quiz result — FloorplayUnfiltered
```

Typical email content should include:

- the visitor’s name
- their result heading
- their result type
- a quick explanation that the result is educational, not diagnostic
- a link to the complete guide or a purchase CTA

---

## GitHub Pages deployment

To publish the quiz for free:

1. Go to GitHub and create a public repository.
2. Upload `quiz.html` to the repo root.
3. Go to Settings → Pages.
4. Set Source to:
   - Branch: `main`
   - Folder: `/ (root)`
5. Save and wait for the Pages URL to generate.
6. Share the live page link.

Example live URL:

```text
https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPO-NAME/
```

---

## Customize the guide CTA

In `quiz.html`, find the CTA link and replace it with the current product URL when needed:

```html
<a href="https://your-store-url.com" class="btn-cta" id="guideCTA">Get the complete guide</a>
```

Update this whenever the product landing page or checkout link changes.

---

## Test before launch

Before sharing publicly:

1. Open `quiz.html` in a browser.
2. Complete the full quiz using a test email.
3. Make sure Formspree receives the submission.
4. Check that the notification email lands.
5. Confirm the autoresponder email is sent if enabled.
6. Click the purchase CTA and verify the post-purchase confirmation page loads correctly.

---

## Notes

- This project is intentionally static and easy to maintain.
- It does not require a server for the quiz itself.
- The main operational dependencies are the live Formspree form and the current product checkout URL.

---

## Questions?

Reach out to your developer or form support if the form submission, autoresponder, or deploy flow needs troubleshooting.

© 2026 Ali Schum / FloorplayUnfiltered
