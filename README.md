# FloorplayUnfiltered

A static, self-contained sexual comfort quiz and conversion flow for FloorplayUnfiltered.

## Overview

This project includes a front-end quiz experience for visitors and a confirmation page for paid guide purchases.

- `quiz.html` — the public quiz experience
- `Confirmation.html` — the post-purchase thank-you / download page
- `FloorplayUnfiltered Quiz — Deployment & Setup Guide.md` — setup and deployment notes

## Current user flow

1. Visitor lands on `quiz.html` and sees the intro screen.
2. They complete 6 questions with progress tracking.
3. After the final question, they are prompted to enter their first name and email.
4. The form submits to Formspree with:
   - `firstName`
   - `email`
   - `resultType`
   - `resultHeading`
   - `answers`
   - `submittedAt`
5. Formspree sends Ali a notification and can trigger an autoresponder email to the user.
6. The user sees a thank-you screen and then the personalized result page.
7. The result page includes a call-to-action to purchase the complete guide.
8. After checkout, the visitor lands on `Confirmation.html` where they can download the PDF guide.

## Recent changes

- Reworked the quiz into a six-question flow with a clear result logic and CTA sequence.
- Added a progress bar and improved branded styling aligned to the FloorplayUnfiltered identity.
- Added a first-name/email step before result delivery.
- Included result metadata and answers in the Formspree submission payload for easier follow-up and list building.
- Added a dedicated confirmation page for successful guide purchases.
- Kept the project static and front-end-only, with no backend required for the quiz itself.

## Files and purpose

### `quiz.html`
The main quiz page contains:
- branded intro and educational framing
- six quiz questions
- option selection state and result calculation
- Formspree submission logic
- result display and guide CTA
- restart flow

### `Confirmation.html`
The post-purchase confirmation page contains:
- thank-you messaging
- order summary
- download button for the guide PDF
- “what’s inside” section and support text

### `FloorplayUnfiltered Quiz — Deployment & Setup Guide.md`
Detailed setup instructions for:
- Formspree form and email notifications
- autoresponder setup
- exporting submissions
- GitHub Pages deployment
- product-link customization

## Setup and deployment

### 1. Formspree
The quiz expects a live Formspree form connection. Confirm the form is active in the Formspree dashboard and that notification emails are enabled.

Formspree should receive the same fields used by the form in `quiz.html` including the result metadata and submission timestamp.

### 2. GitHub Pages
To publish the quiz:

1. Upload `quiz.html` to a GitHub repository.
2. Open the repository's Settings → Pages.
3. Set the source branch to `main` and the folder to `/ (root)`.
4. Save the settings.
5. Use the generated GitHub Pages URL to share the quiz.

### 3. Product checkout
Update the guide CTA in `quiz.html` to the current product link when needed.

### 4. Confirmation page
The confirmation page is a static purchase confirmation page for the guide download. It should point to the live PDF file or Google Drive link used by the product.

## Notes

This is a static front-end project designed to keep setup simple and public-facing. The quiz domain flow is intentionally lightweight: no server build, no package install, and no database required.

## Support

For updates, content review, or live deployment changes, work directly in the `quiz.html` and `Confirmation.html` files and keep the Formspree form configuration aligned with the front-end field names.
